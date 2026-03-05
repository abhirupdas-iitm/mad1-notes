## Week 3 Extra Tutorial
### Executing Python Scripts and Passing Command Line Arguments
##### Description: Demonstrates how Python scripts can be executed using the command line interface (CLI). Explains different ways of executing Python files in a project and how command line arguments can be passed to scripts and accessed using the `sys.argv` list.

---
### Introduction

Python scripts can be executed in multiple ways:
- Using the **Run button** in development environments
- Importing scripts as modules
- Executing scripts directly through the **command line interface (CLI)**
The tutorial focuses on executing Python scripts using the command line and passing parameters to them.
### Replit Project Structure
When creating a Python project in Replit, the interface typically contains three sections:
#### 1. Layout Panel
Located on the left side.
Purpose:
- Shows all files in the project
- Allows creating new files or folders
Example files:
- `main.py`
- `hello.py`
#### 2. Workspace
Located in the center.
Purpose:
- Used for writing code.
Example Python code:
`print("Hello world")`
#### 3. Console
Located on the right side.
Purpose:
- Displays program output.
Example output:
Hello world
### Running Python Files in a Project
In many environments like Replit, clicking the **Run button** executes only the default file:
main.py
Other files in the project are not automatically executed.
Therefore, additional methods are needed to run other scripts.
### Method 1: Using the Import Statement
One way to execute another Python file is by importing it.
Example concept:
import hello
If a file named `hello.py` exists, Python loads and executes the code in that file.
Example file:
hello.py
`print("You are in file hello.py")`
Running `main.py` that imports `hello` will execute this code.
Output:
You are in file hello.py
### Method 2: Using the exec() Function
Another way to execute a Python script is by reading its contents and executing it dynamically.
Example concept:
`exec(open("hello.py").read())`
Steps performed:
1. Open the file `hello.py`
2. Read its content
3. Execute the Python code using `exec()`
This also runs the code inside the file.
### Method 3: Running Python Scripts via Command Line
Python scripts can be executed directly from the terminal or shell.
General command format:
python filename.py
Example:
python hello.py
This command executes the file `hello.py`.
Output example:
You are in file hello.py
### Example Script with Input
Example Python script:
hello.py
```
print("Welcome everyone")  
name = input("Enter your name: ")  
print("Welcome", name)
```
When executed:
python hello.py
Example interaction:
Enter your name: Abhishek  
Welcome Abhishek
This demonstrates how scripts can interact with users through command line input.
### Passing Command Line Arguments
Python scripts can receive parameters directly from the command line.
Example command:
python hello.py 123 Abhishek
Here:
- `123` is the first argument
- `Abhishek` is the second argument
These values are passed to the script during execution.
### Accessing Command Line Arguments
Python provides the **sys module** to access command line arguments.
The module contains a special list:
`sys.argv`
This list stores all command line parameters passed to the script.
To use it:
`import sys`
### Structure of sys.argv
The list contains:

| Index   | Value                        |
| ------- | ---------------------------- |
| argv[0] | Name of the Python script    |
| argv[1] | First command line argument  |
| argv[2] | Second command line argument |
| ...     | Additional arguments         |
Example command:
python hello.py 123 Abhishek
Then:
`sys.argv = ["hello.py", "123", "Abhishek"]`
### Counting Command Line Parameters
To count parameters:
`len(sys.argv)`
Example code:
```
import sys  
print("Total parameters:", len(sys.argv))
```
Example command:
python hello.py 123 Abhishek
Output:
Total parameters: 3
Explanation:
- hello.py
- 123
- Abhishek
Three elements exist in the list.
### Accessing Individual Parameters
Example code:
```
import sys  
print("First parameter:", sys.argv[1])  
print("Second parameter:", sys.argv[2])
```
Example command:
python hello.py 123 Abhishek
Output:
First parameter: 123  
Second parameter: Abhishek
Note:
`sys.argv[0]` is skipped because it stores the script name.
### Passing Multiple Arguments
Python allows passing **any number of parameters**.
Example command:
python hello.py 10 20 30 40 50
If the script only accesses the first two parameters, the remaining parameters are ignored.
Extra parameters do not cause errors unless accessed incorrectly.
### Data Type of Command Line Arguments
All command line arguments are stored as **strings**.
Example code:
```
import sys  
print(type(sys.argv[1]))  
print(type(sys.argv[2]))
```
Output:
<class 'str'>  
<class 'str'>
Even numeric values such as `123` are treated as strings.
### Type Conversion
If a numeric value is required, arguments must be converted.
Example concept:
`int(sys.argv[1])`
Example:
`number = int(sys.argv[1])`
This converts the string `"123"` into the integer `123`.
### Comparison with input() Function
Command line arguments behave similarly to input().
Example behavior:
input() returns **string values**.
Similarly:
sys.argv values are also stored as **strings**.
Therefore, explicit type conversion is required when working with numbers.
### Summary
This tutorial introduced command line execution of Python scripts and parameter passing.
Key concepts covered:
- Running Python scripts from the command line
- Importing Python files as modules
- Executing scripts using `exec()`
- Passing command line arguments
- Accessing arguments using `sys.argv`
- Understanding argument indexing
- Converting argument types
Command line arguments allow Python programs to become more flexible by accepting input parameters during execution.

---
---
## Week 3 – Extra Lecture 1  
### Python Templates and Introduction to Jinja2
#### Description
This lecture introduces template generation using Python. It first explains basic string formatting in Python, then introduces Jinja2, a powerful templating engine used to dynamically generate documents such as HTML files. The lecture also demonstrates how to create a virtual environment, install external libraries, and render templates using Jinja2.

---
### 1. Project Setup
Before starting, the following tools are required:
- Web browser (Chrome/Firefox)
- Text editor (e.g., gedit)
- Terminal
- File browser
- Python 3 installed
#### Creating a Working Folder
Create a folder for the experiment:
```bash
mkdir experiment2
cd experiment2
```
Create a Python file:
```bash
touch app.py
```
Open the file in an editor:
```bash
gedit app.py
```
### 2. Basic Python Script Structure
A typical Python script contains a main function and a condition to execute it only when the script runs directly.
Example:
```python
def main():
    print("hello")

if __name__ == "__main__":
    main()
```
Explanation:
- `__name__` represents the current module name.
- When the file is executed directly, `__name__ == "__main__"`.
- This ensures the script runs only when executed from the command line.
Run the program:
```bash
python3 app.py
```
Output:
```
hello
```
### 3. Python String Templates Using format()
Python allows simple templating using the format() method.
Example template:
```python
template_doc = "hello {name}"
print(template_doc.format(name="Thej"))
```
Output:
```
hello Thej
```
Here:
- `{name}` is a placeholder.
- `format()` replaces it with the provided value.
### 4. Positional Formatting
Instead of named placeholders, values can also be inserted by position.
Example:
```python
template_doc = "hello {}"
print(template_doc.format("Thej"))
```
Output:
```
hello Thej
```
Named placeholders are usually preferred because they make templates easier to understand.
### 5. Formatting Numbers
Python formatting allows control over number appearance.
Example:
```python
template_doc = "p={p}, n={n}"
print(template_doc.format(p=5, n=-7))
```
Output:
```
p=5, n=-7
```
### 6. Displaying Explicit Signs
By default, only negative numbers show a sign.  
To show signs for both positive and negative numbers:
```python
template_doc = "p={p:+}, n={n:+}"
print(template_doc.format(p=5, n=-7))
```
Output:
```
p=+5, n=-7
```
The `+` is a format specifier.
### 7. Converting Number Formats
Python formatting can display numbers in different bases.
Example:
```python
template_doc = "Decimal: {value:d}, Hex: {value:x}"
print(template_doc.format(value=10))
```
Output:
```
Decimal: 10, Hex: a
```
Explanation:
- `:d` → decimal
- `:x` → hexadecimal
### 8. Python f-Strings
Python also supports formatted string literals (f-strings).
Example:
```python
name = "Thej"
print(f"hello {name}")
```
f-strings are often more readable and efficient for inline formatting.
### 9. Need for Templating Engines
Basic string formatting works well for small messages or logs.
However, when generating large documents (such as HTML pages), managing templates inside strings becomes difficult.
For such cases, dedicated templating engines are used.
Example engines:
- Jinja2
- Django Templates
- Mako
This lecture introduces Jinja2.
### 10. What is Jinja2?
Jinja2 is a:
- Fast
- Expressive
- Extensible
templating engine for Python.
Features:
- Separates content from code
- Allows Python-like logic inside templates
- Commonly used in frameworks such as Flask
Templates contain placeholders that are replaced during rendering.
### 11. Creating a Virtual Environment
Since Jinja2 is an external package, it should be installed inside a virtual environment.
Create a virtual environment:
```bash
python3 -m venv experiment2-env
```
Activate the environment:
```bash
source experiment2-env/bin/activate
```
Verify Python version:
```bash
python --version
```
### 12. Installing Jinja2
Install Jinja2 using pip:
```bash
pip install Jinja2
```
This installs Jinja2 along with required dependencies.
### 13. Managing Dependencies with requirements.txt
To record installed packages:
```bash
pip freeze > requirements.txt
```
Example requirements.txt:
```
Jinja2==3.0.1
MarkupSafe==2.0.1
```
This file helps recreate the same environment later using:
```bash
pip install -r requirements.txt
```
### 14. Using Jinja2 Templates
First import the Template class:
```python
from jinja2 import Template
```
Create a template string:
```python
template_string = "hello {{ name }}"
```
Notice:
- Jinja2 placeholders use double curly braces `{{ }}`.
### 15. Creating a Template Object
Initialize the template:
```python
template = Template(template_string)
```
This creates a Template object.
### 16. Rendering the Template
Render the template by providing values.
Example:
```python
print(template.render(name="Thej"))
```
Output:
```
hello Thej
```
Steps performed:
1. Template created
2. Variables passed to `render()`
3. Final document generated
### 17. Complete Example
```python
from jinja2 import Template

def main():
    template_string = "hello {{ name }}"
    template = Template(template_string)

    output = template.render(name="Thej")
    print(output)

if __name__ == "__main__":
    main()
```
Output:
```
hello Thej
```
### Summary
This lecture covered:
- Basic Python string formatting
- Format specifiers for numbers
- Introduction to f-strings
- Limitations of simple formatting
- Introduction to Jinja2 templating
- Creating virtual environments
- Installing packages with pip
- Managing dependencies with requirements.txt
- Rendering templates using Jinja2
Jinja2 provides a flexible system for generating dynamic documents such as HTML pages in web applications.

---
---
## Week 3 – Extra Lecture 2  
### Generating Dynamic HTML using Jinja2 Templates
#### Description
This lecture demonstrates how **Jinja2 templates can be used to dynamically generate HTML documents** from Python data structures. It explains how to pass dictionary data into templates, iterate through lists of records, generate HTML tables dynamically, and save the rendered output as an HTML file.

---
### 1. Problem Statement
Suppose we have a dataset of **Jnanpith Award winners** stored in Python.
Example data:
```python
janapith_data = {
    "year": 1965,
    "awardees": "G. Sankara Kurup",
    "language": "Malayalam"
}
```
Goal:
Generate an **HTML document containing a table** showing this information.
### 2. Creating an HTML Template
A basic HTML template might look like this:
```html
<html>
<head>
<title>Jnanpith Awardees</title>
</head>

<body>

<h1>Awardees</h1>

<table border="1">
<tr>
<th>Year</th>
<th>Awardee</th>
<th>Language</th>
</tr>

<tr>
<td>{{ janapith_data["year"] }}</td>
<td>{{ janapith_data["awardees"] }}</td>
<td>{{ janapith_data["language"] }}</td>
</tr>

</table>

</body>
</html>
```
Explanation:
- `{{ }}` are **Jinja2 placeholders**
- They are replaced with actual values during template rendering.
### 3. Passing Data to the Template
In Python, the data is passed during rendering.
Example:
```python
content = template.render(janapith_data=janapith_data)
```
When rendered, the template substitutes the values.
Example generated HTML:
```html
<tr>
<td>1965</td>
<td>G. Sankara Kurup</td>
<td>Malayalam</td>
</tr>
```
### 4. Handling Multiple Rows of Data
Real datasets usually contain multiple entries.
Example dataset:
```python
janapith_data = [
{
"year": 1965,
"awardees": "G. Sankara Kurup",
"language": "Malayalam"
},
{
"year": 1966,
"awardees": "Tarashankar Bandyopadhyay",
"language": "Bengali"
},
{
"year": 1967,
"awardees": "Kuppali Venkatappa Puttappa",
"language": "Kannada"
}
]
```
Now the data is a **list of dictionaries**.
The template must iterate through this list.
### 5. Using Jinja2 Loops
Jinja2 supports loops similar to Python.
Example:
```html
{% for janapith in janapith_data %}

<tr>
<td>{{ janapith["year"] }}</td>
<td>{{ janapith["awardees"] }}</td>
<td>{{ janapith["language"] }}</td>
</tr>

{% endfor %}
```
Explanation:
- `{% %}` represents **Jinja2 control statements**
- `{% for %}` starts a loop
- `{% endfor %}` ends the loop
Each dictionary entry generates one table row.
### 6. Complete Template Example
```html
<html>

<head>
<title>Jnanpith Awardees</title>
</head>

<body>

<h1>Awardees</h1>

<table border="1">

<tr>
<th>Year</th>
<th>Awardee</th>
<th>Language</th>
</tr>

{% for janapith in janapith_data %}

<tr>
<td>{{ janapith["year"] }}</td>
<td>{{ janapith["awardees"] }}</td>
<td>{{ janapith["language"] }}</td>
</tr>

{% endfor %}

</table>

</body>
</html>
```
### 7. Rendering the Template in Python
Python code:
```python
from jinja2 import Template

template = Template(template_string)

content = template.render(janapith_data=janapith_data)

print(content)
```
The template dynamically generates multiple table rows based on the dataset.
### 8. Writing the HTML Output to a File
Instead of printing the HTML, we can save it to a file.
Example:
```python
file = open("janapith.html", "w")

file.write(content)

file.close()
```
This generates an HTML file containing the rendered table.
### 9. Viewing the Generated HTML
After running the script:
```bash
python app.py
```
A file named **janapith.html** will be created.
Opening the file in a browser displays the generated table.
Example structure:
```
Year    Awardee                         Language
1965    G. Sankara Kurup                Malayalam
1966    Tarashankar Bandyopadhyay       Bengali
1967    K. V. Puttappa                  Kannada
```
### 10. Separating Templates from Code
Best practice is to store templates in **separate files** rather than inside Python code.
Example template file:
```
janapith.html.jinja2
```
This file contains the HTML template.
### 11. Reading Template Files in Python
Python can load the template from the file.
Example:
```python
template_file = open("janapith.html.jinja2")

template_content = template_file.read()

template_file.close()
```
The template content is then passed to Jinja2.
### 12. Creating the Template Object
```python
template = Template(template_content)
```
### 13. Rendering the Template
```python
content = template.render(janapith_data=janapith_data)
```
### 14. Saving the Generated HTML
```python
file = open("janapith.html", "w")

file.write(content)

file.close()
```
### 15. Full Workflow
The full process consists of three steps:
#### Step 1 – Read Template File
Load the template into a variable.
#### Step 2 – Render Template
Pass data into the template and generate HTML.
#### Step 3 – Save Output
Write the rendered content into an HTML file.
### 16. Project Structure
A simple project structure looks like this:
```
project_folder/

app.py
janapith.html.jinja2
requirements.txt
experiment2-env/
```
Explanation:
- **app.py** → Python application
- **janapith.html.jinja2** → HTML template
- **requirements.txt** → dependency list
- **experiment2-env** → virtual environment
### 17. Dynamic Data Updates
Adding new records automatically updates the table.
Example new entry:
```python
{
"year": 1968,
"awardees": "Example Name",
"language": "Example Language"
}
```
After running the script again, the table will include the new row.
Similarly, removing rows from the dataset reduces table entries.
### 18. Features of Jinja2
Jinja2 provides powerful templating capabilities.
Examples include:
- Conditional statements (`if`, `else`)
- Loops (`for`)
- Macros
- Template inheritance
- Template inclusion
- Expressions
- Loop controls
These features make it easy to generate complex documents dynamically.
### 19. Jinja2 Documentation
More information can be found on the official Jinja2 documentation site.
The documentation explains:
- Template inheritance
- Filters
- Control structures
- Advanced templating techniques
### Summary
This lecture covered:
- Using Jinja2 to generate HTML dynamically
- Passing dictionary data to templates
- Rendering lists of data using loops
- Writing rendered templates to HTML files
- Separating templates from application code
- Organizing project structure
- Advantages of dynamic templating
Jinja2 enables Python programs to generate complex documents such as **HTML pages, configuration files, or reports** efficiently.

---
---
## Week 3 – Extra Lecture 3  
### Browser Developer Tools (Console)
##### Description
This lecture introduces **browser developer tools**, which are built-in debugging tools available in modern browsers like Chrome and Firefox. These tools help developers inspect HTML, debug JavaScript, monitor network requests, analyze performance, and test how web pages behave across different devices.

---
### 1. Introduction to Browser Developer Tools
Modern browsers provide developer tools that allow developers to:
- Inspect HTML elements
- Modify CSS styles in real time
- Debug JavaScript
- Monitor network requests
- Analyze performance
- Test responsive layouts
These tools are available in **Chrome** and **Firefox**.
### 2. Opening Developer Tools
There are multiple ways to open developer tools.
#### Method 1: Browser Menu
In Chrome:
1. Click the **three-dot menu**
2. Go to **More Tools**
3. Click **Developer Tools**

In Firefox:
1. Open the **menu**
2. Select **More Tools**
3. Click **Web Developer Tools**
#### Method 2: Right Click → Inspect
Right-click on any webpage element and select:
```
Inspect
```
This opens developer tools and highlights the corresponding HTML element.
### 3. Layout of Developer Tools
Developer tools contain multiple tabs:
- **Elements / Inspect**
- **Console**
- **Sources**
- **Network**
- **Application**
- **Performance**
- **Memory**
Each tab provides different debugging capabilities.
### 4. Elements (Inspect) Tab
The **Elements tab** allows developers to inspect the structure of the webpage.
Features include:
- Viewing HTML structure
- Identifying parent and child elements
- Inspecting CSS styles applied to elements
When selecting an element on the webpage, the corresponding HTML is highlighted in the inspector.
Example structure:
```
<div class="container">
   <p>Hello World</p>
</div>
```
The hierarchy of elements becomes visible.
### 5. Viewing Applied CSS Styles
The right side panel shows the **CSS rules applied** to the selected element.
This includes:
- Styles defined by tag selectors
- Styles defined by classes
- Styles inherited from parent elements
Developers can switch to the **Computed tab** to see the final CSS applied after cascading rules.
### 6. Editing CSS in Real Time
Developer tools allow real-time editing of CSS properties.
Example:
```
color: black;
```
Can be changed to:
```
color: green;
```
The webpage immediately reflects the change.
This is useful for experimenting with styles before modifying the actual code.
### 7. Understanding Cascading Style Sheets (CSS)
CSS is called **cascading** because styles may come from multiple sources:
- Element selectors
- Class selectors
- Parent elements
- External style sheets
The **computed styles** tab shows the final result after all styles are applied.
### 8. Responsive Design Testing
Developer tools include a **device simulation mode**.
This allows developers to see how webpages appear on different devices.
Examples include:
- Mobile devices
- Tablets
- Desktop screens
Example simulated devices:
- Pixel 2
- iPad Pro
- Custom screen sizes
This helps ensure that webpages are **responsive**.
### 9. Console Tab
The **Console tab** works like a command line interface.
It allows developers to:
- Run JavaScript commands
- Print debugging information
- View errors and warnings
Example JavaScript command:
```javascript
alert("Hello")
```
This displays a popup alert.
### 10. Logging Messages
The most common debugging method in JavaScript is printing messages to the console.
Example:
```javascript
console.log("Hello")
```
Output appears in the console.
### 11. Error and Warning Messages
JavaScript provides specialized console messages.
Example:
```javascript
console.error("Error message")
```
Displays a red error message.
Example:
```javascript
console.warn("Warning message")
```
Displays a yellow warning message.
These help developers distinguish between different types of logs.
### 12. Using Console for Debugging
Developers frequently print variable values to the console.
Example:
```javascript
console.log(userName)
```
This helps track program behavior during debugging.
### 13. Measuring Execution Time
The console can measure how long code execution takes.
Example:
```javascript
console.time("test")

// code to measure

console.timeEnd("test")
```
This prints the time taken to execute the code.
### 14. Displaying Data Using console.table()
When dealing with arrays or objects, data can be displayed as tables.
Example object:
```javascript
let people = [
 {name:"Ram", age:25},
 {name:"Raj", age:35}
]
```
Printing normally:
```javascript
console.log(people)
```
Printing as a table:
```javascript
console.table(people)
```
This displays data in a structured tabular format.
### 15. Clearing the Console
The console can be cleared using:
```javascript
console.clear()
```
This removes all previously printed logs.
### 16. Sources Tab
The **Sources tab** displays all loaded files.
Examples include:
- HTML files
- JavaScript files
- CSS files
- Images
- Other resources

Features include:
- Viewing formatted source code
- Setting breakpoints
- Debugging JavaScript step-by-step
Breakpoints pause code execution to inspect variable values.
### 17. Network Tab
The **Network tab** shows all network requests made by the webpage.
Examples include:
- HTML requests
- CSS files
- JavaScript files
- Images
- Fonts
- AJAX requests

Information displayed includes:
- Request URL
- Request type (GET, POST)
- Status code
- File size
- Loading time
### 18. Understanding Network Requests
Example request details:
```
Request Type: GET
Status Code: 200
Remote Address: IP address
Port: 443
```
The **200 status code** indicates success.
### 19. Waterfall Timing Chart
The network tab displays a **waterfall timeline**.
This shows how each request progressed through stages:
- Queueing
- DNS lookup
- Initial connection
- SSL handshake
- Request sent
- Waiting for response
- Content download
This helps identify performance bottlenecks.
### 20. Viewing Request Headers
Headers contain metadata about requests.
Example request headers include:
- Host
- User agent
- Accept type
Example response headers include:
- Content type
- Content encoding
- Cache information
### 21. POST Requests and Form Data
Developer tools can show **form submissions**.
Example form fields:
```
Name: Thejesh
Telephone: 9999900000
Email: i@thejesh.com
```
The network tab displays submitted form data.
Example:
```
custom_name = Thejesh
custom_tel = 9999900000
custom_email = i@thejesh.com
```
This helps debug form submissions.
### 22. Preserving Network Logs
Normally, network logs clear after page refresh.
To preserve logs:
Enable:
```
Preserve log
```
This keeps request history across reloads.
### 23. Simulating Network Speed
Developer tools allow simulation of slower internet connections.
Example network throttling:
- Slow 3G
- Fast 3G
- Offline mode
This helps test website performance on mobile networks.
### 24. Application Tab
The **Application tab** shows browser storage mechanisms.
Examples include:
- Local storage
- Session storage
- IndexedDB
- Cookies
- Cache storage
### 25. Local Storage
Local storage stores persistent data in key-value format.
Example:
```
username : Thejesh
theme : dark
```
This data remains even after closing the browser.
### 26. Session Storage
Session storage is similar to local storage but only lasts for the current browser session.
Once the browser is closed, the data is removed.
### 27. Cookies
Cookies store small pieces of data used by websites.
Example cookie data:
```
domain : iitm.ac.in
key : session_id
value : xyz123
size : 40 bytes
```
Cookies are commonly used for:
- Authentication
- User preferences
- Tracking sessions
### 28. Cache Storage
Browsers store cached resources locally to improve performance.
Example cached files:
- Images
- CSS
- JavaScript
When cached files exist, the browser loads them from disk rather than downloading again.
Example indicator:
```
served from disk cache
```
### 29. Importance of Developer Tools
Developer tools are essential for:
- Debugging web applications
- Understanding webpage structure
- Monitoring network activity
- Optimizing performance
- Testing responsive designs
They provide deep visibility into how web applications function.
### Summary
This lecture covered:
- Opening browser developer tools
- Inspecting HTML and CSS
- Editing styles dynamically
- Using the console for debugging
- Logging messages and errors
- Measuring code execution time
- Viewing source files
- Monitoring network requests
- Debugging form submissions
- Simulating network conditions
- Managing local storage, cookies, and cache
Browser developer tools are powerful utilities that every web developer should learn to use effectively.

---
---
