# Portfolio Backend API

A Flask-based backend API for handling contact form submissions from the portfolio website.

## Features

- Contact form submission handling
- Email validation and sanitization
- SMTP email sending via Gmail
- CORS support for frontend integration
- Environment variable configuration
- Error handling and logging

## Setup

### Prerequisites

- Python 3.8+
- pip (Python package installer)

### Installation

1. Clone this repository:
```bash
git clone <your-repo-url>
cd portfolio-backend
```

2. Create a virtual environment:
```bash
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate
```

3. Install dependencies:
```bash
pip install -r requirements.txt
```

4. Create a `.env` file with your email configuration:
```env
SENDER_EMAIL=your-email@gmail.com
EMAIL_PASSWORD=your-app-password
RECEIVER_EMAIL=your-email@gmail.com
```

### Gmail Setup

1. Enable 2-Factor Authentication on your Gmail account
2. Generate an App Password:
   - Go to Google Account Settings
   - Security → App passwords
   - Generate a new app password for "Mail"
   - Use this password in your `.env` file

## Local Development

Run the Flask development server:
```bash
python app.py
```

The API will be available at `http://localhost:5000`

## API Endpoints

### Health Check
- **GET** `/` - Returns API status and available endpoints

### Contact Form
- **POST** `/api/contact` - Submit contact form
  
  **Request Body:**
  ```json
  {
    "name": "John Doe",
    "email": "john@example.com",
    "message": "Hello, this is a test message."
  }
  ```
  
  **Response:**
  ```json
  {
    "message": "Message sent successfully!"
  }
  ```

## Environment Variables

| Variable | Description | Example |
|----------|-------------|---------|
| `SENDER_EMAIL` | Gmail address for sending emails | `your-email@gmail.com` |
| `EMAIL_PASSWORD` | Gmail app password | `abcd efgh ijkl mnop` |
| `RECEIVER_EMAIL` | Email address to receive messages | `your-email@gmail.com` |
| `PORT` | Server port (default: 5000) | `5000` |

## Deployment

### Render Deployment

1. Connect your GitHub repository to Render
2. Create a new Web Service
3. Configure environment variables in Render dashboard
4. Deploy using the following settings:
   - **Build Command:** `pip install -r requirements.txt`
   - **Start Command:** `gunicorn app:app`

### Manual Deployment

1. Set up your production server
2. Install dependencies: `pip install -r requirements.txt`
3. Configure environment variables
4. Run with Gunicorn: `gunicorn --bind 0.0.0.0:$PORT app:app`

## Project Structure

```
portfolio-backend/
├── app.py              # Main Flask application
├── requirements.txt    # Python dependencies
├── .env               # Environment variables (not in git)
├── .gitignore         # Git ignore file
├── README.md          # This file
└── render.yaml        # Render deployment config
```

## Error Handling

The API includes comprehensive error handling for:
- Missing or invalid request data
- Email validation errors
- SMTP connection issues
- Server errors

All errors return appropriate HTTP status codes and descriptive messages.

## Security Features

- Input validation and sanitization
- Email format validation
- Environment variable protection
- CORS configuration
- Error message sanitization

## Contributing

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Test thoroughly
5. Submit a pull request

## License

This project is licensed under the MIT License.