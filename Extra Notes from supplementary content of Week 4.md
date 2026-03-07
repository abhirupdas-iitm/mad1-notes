## Week 4 Extra Tutorial
### Building a Simple Flask Web Application
##### Description: This lecture demonstrates how to build a basic web application using the Flask framework. It covers setting up a virtual environment, installing dependencies, creating a Flask application, defining routes, using templates with Jinja2, handling GET and POST requests, processing form input, and generating dynamic responses.

### 1. Introduction
In this tutorial, the goal is to build a **simple web application using Flask** and run it using Flask’s **built-in development server**.
Tools required:
- Web browser (Chrome or Firefox)
- Text editor (`gedit` or any editor)
- Terminal
- File browser

### 2. Creating the Project Directory
First, create a new folder for the project.
Example:
```
mkdir experiment3
cd experiment3
```
This folder will contain:
- the application code
- templates
- dependencies

### 3. Creating a Virtual Environment
A virtual environment isolates project dependencies.
Command:
```
python3 -m venv .experiment-env
```
This creates a virtual environment folder.
Activate it using:
```
source .experiment-env/bin/activate
```
After activation, Python will run from the **local virtual environment**.

### 4. Creating Requirements File
Create a file named:
```
requirements.txt
```
Add Flask to it:
```
flask
```
Optionally, specify version:
```
flask==1.0.0
```
If no version is specified, the **latest version will be installed**.

### 5. Installing Dependencies
Install packages from the requirements file:
```
pip install -r requirements.txt
```
This installs:
- Flask
- all dependencies required by Flask
To verify installed packages:
```
pip freeze
```
Typical dependencies include:
- flask
- jinja2
- markupsafe
- others

### 6. Creating the Application File
Create a Python file:
```
application.py
```
This file will contain the Flask application code.

### 7. Writing the Simplest Flask Application
The simplest Flask application:
- imports Flask
- creates an application instance
- defines a route
- returns HTML content

Example structure:
```
from flask import Flask

app = Flask(__name__)

@app.route("/")
def hello_world():
    return "<h1>Hello World</h1>"

if __name__ == "__main__":
    app.run(debug=True)
```
Explanation:
- `@app.route("/")` defines the **URL endpoint**
- the function returns **HTML content**
- `debug=True` enables debugging

### 8. Running the Flask Application
Start the server using:
```
python application.py
```
Output:
```
Running on http://127.0.0.1:5000
```
Important notes:
- Flask development server runs on **port 5000 by default**
- This server is **not suitable for production**
- It is meant only for **development and testing**

### 9. Accessing the Application
Open a browser and visit:
```
http://127.0.0.1:5000
```
You will see:
```
Hello World
```
This confirms the server is working.

### 10. Understanding Flask Routes
Routes define **URL paths**.
Example:
```
@app.route("/hello")
```
Now the page is available at:
```
http://127.0.0.1:5000/hello
```
If you visit:
```
http://127.0.0.1:5000/
```
You will get:
```
404 Not Found
```
because the root route is no longer defined.

### 11. Auto Reload in Debug Mode
When `debug=True`:
- Flask automatically restarts when files change
However, if the restart fails, the server can be manually restarted using:
```
CTRL + C
python application.py
```

### 12. Moving HTML to Templates
Instead of embedding HTML inside Python code, it is better to use **templates**.
Flask uses **Jinja2 templates**.
Create a folder:
```
templates
```
Inside it create:
```
hello_world.html
```
Example content:
```
<html>
<body>
<h1>Hello World</h1>
</body>
</html>
```

### 13. Rendering Templates in Flask
Flask provides the function:
```
render_template()
```
Update the route:
```
return render_template("hello_world.html")
```
Now Flask reads the HTML file from the **templates folder** and renders it.

### 14. Benefits of Using Templates
Advantages:
- separates HTML from Python code
- easier maintenance
- reusable components
- cleaner architecture

### 15. Creating a Form for User Input
Next goal:
Allow the user to **enter their name**.
Create a new template:
```
get_details.html
```
This template contains an HTML form.
Example structure:
```
<form method="POST">
<input type="text" name="username">
<input type="submit">
</form>
```
The form sends data to the server.

### 16. Serving the Form
Modify the route to return:
```
render_template("get_details.html")
```
Now the user sees:
- a text field
- a submit button

### 17. Understanding HTTP Methods
Web requests use HTTP methods.
Two common ones:
```
GET  
POST
```
GET:
- used to retrieve data
- default request type
POST:
- used to submit data
- commonly used with forms

### 18. Enabling POST Requests
By default, Flask routes allow only **GET requests**.
To allow POST:
```
@app.route("/hello", methods=["GET","POST"])
```
Now the route accepts both request types.

### 19. Processing Form Submissions
Inside the route function:
```
if request.method == "GET":
    return render_template("get_details.html")
```
If the request is POST:
- retrieve form data
- process it

### 20. Reading Form Data
Form data is accessed using:
```
request.form
```
Example:
```
username = request.form["username"]
```
This retrieves the value submitted by the user.

### 21. Creating the Response Template
Create another template:
```
display_details.html
```
Example content:
```
<html>
<body>
Hello {{ username }}
</body>
</html>
```
This uses **Jinja template variables**.

### 22. Passing Variables to Templates
Flask allows passing variables to templates.
Example:
```
return render_template("display_details.html", username=username)
```
The variable becomes available inside the template.

### 23. Full Flow of the Application
The application now performs a full request-response cycle.
Steps:
1. User accesses `/hello`
2. Server sends HTML form
3. User enters name
4. Form sends POST request
5. Server reads form data
6. Server renders response template
7. User sees personalized message

Example output:
```
Hello Thej
```

### 24. Importance of Debug Mode
Debug mode helps identify errors.
Example issue:
```
NameError: request not defined
```
Solution:
Import request from Flask.
```
from flask import request
```
Debug mode displays helpful error messages.
In production:
```
debug=False
```
This prevents exposing internal system information.

### 25. Form Submission Destination
Forms can submit data to the same route.
Example:
```
<form method="POST">
```
The request returns to the same endpoint.
Alternatively, specify an action:
```
<form method="POST" action="/world">
```
Now submission goes to `/world`.
If no route exists, the server returns:
```
404 Not Found
```

### 26. Summary
This tutorial demonstrated how to build a basic Flask web application.
Key steps:
- create project directory
- create virtual environment
- install Flask
- write a basic Flask app
- run the development server
- define routes
- move HTML into templates
- create HTML forms
- process GET and POST requests
- use Jinja templates for dynamic responses
The final application allows:
- user input through a form
- server-side processing
- dynamic response generation
This demonstrates the fundamental workflow of **web applications built using Flask**.

---
