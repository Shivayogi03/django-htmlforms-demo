# Django HTML Forms Demo

A simple Django project showcasing how to create and process HTML forms using the `POST` method.  
This project includes CSRF protection, user input handling, and a minimal styled frontend.

---

## 🚀 Features
- Basic HTML form with username and password fields  
- Handles POST requests securely  
- Demonstrates use of `{% csrf_token %}` in templates  
- Displays dynamic response after form submission  
- Simple gradient background for better UI

---

## 🗂 Project Structure
django-htmlforms-demo/
│
├── app/
│ ├── views.py
│ ├── templates/
│ │ └── htmlforms.html
│ ├── init.py
│ ├── urls.py (optional if app-level)
│
├── project_name/
│ ├── settings.py
│ ├── urls.py
│ ├── init.py
│
├── manage.py
└── README.md

python
Copy code

---

## 🧩 Code Overview

### `views.py`
```python
from django.shortcuts import render
from django.http import HttpResponse

def htmlforms(request):
    if request.method == 'POST':
        un = request.POST['una']
        pw = request.POST['pwa']
        return HttpResponse(f"Username is {un} & your password is confidential!")
    return render(request, 'htmlforms.html')
htmlforms.html
html
Copy code
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>HTML Forms</title>
    <style>
        body {
            background: linear-gradient(to right, pink, blue);
            font-family: Arial, sans-serif;
        }
        form {
            margin-top: 50px;
        }
    </style>
</head>
<body>
    <center>
        <h1>HTML FORM</h1>
        <form method="POST">
            {% csrf_token %}
            <label for="un">Username</label>
            <input type="text" name="una" id="un" required>
            <br><br>
            <label for="pw">Password</label>
            <input type="password" name="pwa" id="pw" required>
            <br><br>
            <input type="submit" value="Submit">
        </form>
    </center>
</body>
</html>
urls.py
python
Copy code
from django.contrib import admin
from django.urls import path
from app.views import htmlforms

urlpatterns = [
    path('admin/', admin.site.urls),
    path('htmlforms/', htmlforms, name='htmlforms'),
]
⚙️ How to Run the Project
Clone the repository

bash
Copy code
git clone https://github.com/<your-username>/django-htmlforms-demo.git
cd django-htmlforms-demo
Create and activate a virtual environment

bash
Copy code
python -m venv venv
source venv/bin/activate      # for Linux/Mac
venv\Scripts\activate         # for Windows
Install dependencies

bash
Copy code
pip install django
Run the server

bash
Copy code
python manage.py runserver
Open in browser

arduino
Copy code
http://127.0.0.1:8000/htmlforms/
