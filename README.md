# EcoVerse 🌍

This is a Flask-based web application designed to allow users to detect and analyze environmental pollution, primarily through image uploads. It features user authentication, post creation, plastic pollution analysis, and image-based severity scoring.

## 🔧 Features

- **User Authentication**: Register, login, and logout functionalities using Flask-Login.
- **Post System**: Authenticated users can create posts with images and descriptions.
- **Pollution Analysis**: Uploaded images are analyzed using a custom garbage detection algorithm, calculating pollution severity.
- **Plastic Detection**: Separate interface to upload and process images for plastic pollution detection.
- **Comment System**: Users can leave comments on posts (implemented in models).

## 🧱 Tech Stack

- **Backend**: Python, Flask
- **Frontend**: HTML templates rendered via Flask
- **Database**: SQLite + SQLAlchemy ORM
- **Authentication**: Flask-Login
- **File Handling**: Flask-WTF + WTForms + OpenCV
- **Image Analysis**: Custom model via `utils.garbage_analyser` and `plastic_detector`

## 📁 Directory Structure

app/
│
├── init.py # App factory setup and configuration
├── forms.py # WTForms for Login, Register, Post
├── models.py # SQLAlchemy models (User, Post, Comment)
├── routes.py # Route handlers for all major functionalities
├── static/ # Static assets (CSS, JS, images)
├── templates/ # Jinja2 templates (dashboard, login, register, etc.)
├── utils/
│ └── garbage_analyser.py # Pollution analysis utility
├── config.py # Configuration file (not shown here)
└── plastic_detector.py # Image transformer for plastic detection

## 🔑 Key Routes

| Route                            | Method   | Description                        |
| -------------------------------- | -------- | ---------------------------------- |
| `/` or `/dashboard`              | GET      | View all posts and users           |
| `/post`                          | GET/POST | Create a new post (requires login) |
| `/login`                         | GET/POST | User login                         |
| `/logout`                        | GET      | Logout current user                |
| `/register`                      | GET/POST | User registration                  |
| `/plastic`                       | GET/POST | Plastic pollution detection        |
| `/image/<int:image_id>`          | GET      | Serve original uploaded image      |
| `/analysed_image/<int:image_id>` | GET      | Serve analysed image               |

## 🛠️ Setup Instructions

1. **Clone the Repository**

   ```bash
   git clone https://github.com/yourusername/pollution-detector.git
   cd pollution-detector
   ```

2. **Create Virtual Environment**

   ```bash
   python -m venv venv
   source venv/bin/activate  # On Windows: venv\Scripts\activate
   ```

3. **Install Dependencies**

```bash
 pip install -r requirements.txt
```

4. **Setup Config**

   Make sure config.py contains database URI, secret key, and folders for uploads.

5. **Run the App**

   ```bash
   flask run
   ```

## 🧪 Notes

- Make sure to define UPLOAD_FOLDER, PROCESSED_FOLDER, and ALLOWED_EXTENSIONS in your config.py.

- Ensure utils/garbage_analyser.py and plastic_detector.py are properly implemented with valid image processing logic.
