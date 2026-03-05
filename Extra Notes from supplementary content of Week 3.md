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
