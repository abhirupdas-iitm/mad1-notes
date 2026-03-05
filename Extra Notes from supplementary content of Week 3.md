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
