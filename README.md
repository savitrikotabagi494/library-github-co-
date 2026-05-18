# library-github-co-
### made with github copilot
<img width="1243" height="632" alt="Screenshot 2026-05-18 105937" src="https://github.com/user-attachments/assets/95213463-37ed-44b3-9b5f-dfc05af5bb7b" />
<img width="1219" height="580" alt="Screenshot 2026-05-18 110006" src="https://github.com/user-attachments/assets/7e3944f1-cc80-4d7b-a93a-54f7c4f786f3" />
<img width="499" height="480" alt="Screenshot 2026-05-18 110029" src="https://github.com/user-attachments/assets/83da1064-e9c5-4243-aca8-c0a2a56b57b9" />


# Library Management API

A Django REST Framework-based API for managing a library's book collection. This application provides a comprehensive REST API for performing CRUD operations on books and a web interface for browsing the library.

---

## 📚 What is an API?

An **API (Application Programming Interface)** is a set of rules and protocols that allows different software applications to communicate with each other. It acts as an intermediary between your frontend application and backend server.

### Key Concepts:

- **Request**: Your client application asks for data or asks the server to perform an action
- **Response**: The server sends back data or confirmation of the action
- **Endpoint**: A specific URL where you can access data or perform actions
- **HTTP Methods**:
  - `GET` - Retrieve data
  - `POST` - Create new data
  - `PUT` - Update all fields of existing data
  - `PATCH` - Update specific fields of existing data
  - `DELETE` - Remove data

### REST API:

REST (Representational State Transfer) is an architectural style for building APIs. It uses:
- Standard HTTP methods
- Resource-based URLs (e.g., `/api/books/`)
- JSON for data exchange
- Stateless communication

---

## 📖 About This Application

The **Library Management API** is a full-stack application that allows users to:

✅ View all books in the library with their details
✅ Create new book entries
✅ Update existing book information
✅ Delete books from the database
✅ Check book availability status
✅ Search and filter books by publication date

### Perfect for:
- Small to medium-sized libraries
- Learning REST API development
- Building a foundation for a larger library management system
- Integration with mobile or web applications

---

## 🛠 Technologies Used

- **Backend**: Django 6.0.5 (Python web framework)
- **API Framework**: Django REST Framework 3.14+ (for building REST APIs)
- **Database**: SQLite (lightweight, file-based database)
- **Frontend**: HTML, CSS, JavaScript
- **Python Version**: 3.8+

---

## 📁 Project Structure

```
library_project/
├── books/                          # Main application
│   ├── models.py                   # Database models (Book)
│   ├── serializers.py              # Convert models to JSON (BookSerializer)
│   ├── views.py                    # API endpoints (BookListCreateAPIView, BookDetailAPIView)
│   ├── urls.py                     # URL routing (if app-level urls exist)
│   ├── migrations/                 # Database migrations
│   ├── static/
│   │   └── books/
│   │       ├── app.js              # Frontend JavaScript
│   │       └── style.css           # Frontend styling
│   ├── templates/
│   │   └── books/
│   │       └── home.html           # Homepage template
│   ├── admin.py                    # Django admin configuration
│   ├── apps.py                     # App configuration
│   └── tests.py                    # Unit tests
│
├── library_project/                # Project configuration
│   ├── settings.py                 # Django settings
│   ├── urls.py                     # Main URL routing
│   ├── asgi.py                     # ASGI configuration (async)
│   └── wsgi.py                     # WSGI configuration (production)
│
├── manage.py                       # Django command-line tool
├── db.sqlite3                      # SQLite database
└── README.md                       # This file
```

---

## 🚀 Getting Started

### Prerequisites

- Python 3.8 or higher
- pip (Python package manager)
- Virtual environment (recommended)

### Installation

1. **Navigate to project directory**
   ```bash
   cd library_project
   ```

2. **Create and activate virtual environment**
   
   **On Windows (PowerShell):**
   ```powershell
   python -m venv venv
   .\venv\Scripts\Activate.ps1
   ```
   
   **On Windows (Command Prompt):**
   ```cmd
   python -m venv venv
   venv\Scripts\activate.bat
   ```
   
   **On macOS/Linux:**
   ```bash
   python -m venv venv
   source venv/bin/activate
   ```

3. **Install dependencies**
   ```bash
   pip install -r requirements.txt
   ```
   
   If `requirements.txt` doesn't exist, install manually:
   ```bash
   pip install django==6.0.5
   pip install djangorestframework==3.14.0
   ```

4. **Apply database migrations**
   ```bash
   python manage.py migrate
   ```

5. **Create a superuser (optional, for Django admin)**
   ```bash
   python manage.py createsuperuser
   ```

---

## ▶️ Running the Project

### Start the Development Server

```bash
python manage.py runserver
```

You should see output like:
```
Starting development server at http://127.0.0.1:8000/
Quit the server with CTRL-BREAK.
```

### Access the Application

- **Homepage**: [http://127.0.0.1:8000/](http://127.0.0.1:8000/)
- **Books API**: [http://127.0.0.1:8000/api/books/](http://127.0.0.1:8000/api/books/)
- **Django Admin**: [http://127.0.0.1:8000/admin/](http://127.0.0.1:8000/admin/)

---

## 📡 API Endpoints

### 1. **List All Books & Create a New Book**

**Endpoint**: `GET/POST /api/books/`

**GET Request** - Retrieve all books:
```bash
curl http://127.0.0.1:8000/api/books/
```

**Response (200 OK)**:
```json
[
  {
    "id": 1,
    "title": "The Great Gatsby",
    "author": "F. Scott Fitzgerald",
    "isbn": "9780743273565",
    "published_date": "1925-04-10",
    "is_available": true
  },
  {
    "id": 2,
    "title": "To Kill a Mockingbird",
    "author": "Harper Lee",
    "isbn": "9780061120084",
    "published_date": "1960-07-11",
    "is_available": true
  }
]
```

**POST Request** - Create a new book:
```bash
curl -X POST http://127.0.0.1:8000/api/books/ \
  -H "Content-Type: application/json" \
  -d '{
    "title": "1984",
    "author": "George Orwell",
    "isbn": "9780451524935",
    "published_date": "1949-06-08",
    "is_available": true
  }'
```

**Response (201 Created)**:
```json
{
  "id": 3,
  "title": "1984",
  "author": "George Orwell",
  "isbn": "9780451524935",
  "published_date": "1949-06-08",
  "is_available": true
}
```

---

### 2. **Get, Update, or Delete a Specific Book**

**Endpoint**: `GET/PUT/PATCH/DELETE /api/books/<id>/`

**GET Request** - Get a specific book:
```bash
curl http://127.0.0.1:8000/api/books/1/
```

**PUT Request** - Update all fields of a book:
```bash
curl -X PUT http://127.0.0.1:8000/api/books/1/ \
  -H "Content-Type: application/json" \
  -d '{
    "title": "The Great Gatsby (Revised)",
    "author": "F. Scott Fitzgerald",
    "isbn": "9780743273565",
    "published_date": "1925-04-10",
    "is_available": false
  }'
```

**PATCH Request** - Update specific fields only:
```bash
curl -X PATCH http://127.0.0.1:8000/api/books/1/ \
  -H "Content-Type: application/json" \
  -d '{
    "is_available": false
  }'
```

**DELETE Request** - Delete a book:
```bash
curl -X DELETE http://127.0.0.1:8000/api/books/1/
```

---

## 📊 Book Model Fields

| Field | Type | Description | Required |
|-------|------|-------------|----------|
| `id` | Integer | Unique identifier (auto-generated) | Auto |
| `title` | String (max 200) | Name of the book | Yes |
| `author` | String (max 100) | Author's name | Yes |
| `isbn` | String (13 chars) | ISBN code (must be unique) | Yes |
| `published_date` | Date | Publication date (YYYY-MM-DD) | Yes |
| `is_available` | Boolean | Whether the book is available to borrow | No (default: true) |

---

## 🧪 Testing the API

### Using Python Requests:

```python
import requests

# Get all books
response = requests.get('http://127.0.0.1:8000/api/books/')
print(response.json())

# Create a new book
new_book = {
    'title': 'Python Programming',
    'author': 'Guido van Rossum',
    'isbn': '9781234567890',
    'published_date': '2020-01-15',
    'is_available': True
}
response = requests.post('http://127.0.0.1:8000/api/books/', json=new_book)
print(response.json())
```

### Using Postman:

1. Open Postman
2. Create a new request
3. Set method to GET/POST/PUT/PATCH/DELETE
4. Enter URL: `http://127.0.0.1:8000/api/books/` or `http://127.0.0.1:8000/api/books/1/`
5. For POST/PUT/PATCH, go to Body tab and select "raw" > "JSON"
6. Add your JSON payload
7. Click Send

---

## 🔧 Common Commands

### Database Management

```bash
# Create database migrations (after changing models.py)
python manage.py makemigrations

# Apply migrations
python manage.py migrate

# Create superuser for admin panel
python manage.py createsuperuser

# Reset database (careful - deletes all data)
python manage.py flush
```

### Shell Commands

```bash
# Access Django shell for testing
python manage.py shell

# Example: Create a book from shell
>>> from books.models import Book
>>> Book.objects.create(
...     title="Python Basics",
...     author="John Doe",
...     isbn="9876543210123",
...     published_date="2024-01-01",
...     is_available=True
... )
```

---

## 📝 Environment Variables (Optional)

For production, create a `.env` file in the root directory:

```
DEBUG=False
SECRET_KEY=your-secret-key-here
ALLOWED_HOSTS=your-domain.com
DATABASE_URL=your-database-url
```

---

## 🐛 Troubleshooting

### Issue: Port 8000 is already in use
```bash
python manage.py runserver 8001
```

### Issue: ModuleNotFoundError for Django or rest_framework
```bash
pip install -r requirements.txt
```

### Issue: Database errors after model changes
```bash
python manage.py makemigrations
python manage.py migrate
```

### Issue: "No such table" error
```bash
python manage.py migrate
```

---

## 📚 Resources

- [Django Documentation](https://docs.djangoproject.com/)
- [Django REST Framework](https://www.django-rest-framework.org/)
- [REST API Best Practices](https://restfulapi.net/)
- [HTTP Methods Explained](https://developer.mozilla.org/en-US/docs/Web/HTTP/Methods)

---

## 🤝 Contributing

Feel free to fork, submit issues, and create pull requests for any improvements.

---

## 📄 License

This project is open-source and available under the MIT License.

---

## ✨ Features Summary

- ✅ RESTful API for CRUD operations
- ✅ Django REST Framework integration
- ✅ SQLite database
- ✅ Serialization of Python objects to JSON
- ✅ Error handling and validation
- ✅ Web interface for browsing books
- ✅ Professional API documentation

---

**Created**: 2026
**Last Updated**: May 18, 2026

Happy coding! 🚀
