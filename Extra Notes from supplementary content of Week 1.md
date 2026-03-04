### Lecture: Using Replit for Application Development
#### Working with Python Projects and HTML Files in Replit
##### Description: Introduction to the Replit development environment and how it can be used for application development projects. The lecture demonstrates how to create a Python project, understand the Replit interface, add HTML files, and link multiple web pages within a project.

---
### Introduction to Replit
Replit is an online development environment that allows users to write, run, and manage code directly in the browser.

It is useful for application development because it provides:
- A coding workspace
- A file management system
- A built-in console for output
- An integrated environment to run programs
### Creating a New Project
Steps to create a project in Replit:

1. Open the user dashboard.
2. Click the **New Repl** button.
3. Select the programming language (Python in this case).
4. Give the project a name.
5. Click **Create Repl**.
After creation, Replit loads the development interface and connects to a Python interpreter.
### Replit Interface Overview
The Replit interface can be divided into three main sections.
#### 1. File Explorer (Layout Panel)

Located on the **left side**.
Purpose:
- Displays all project files
- Allows file creation and folder organization

Example:
Initially the project contains one file:
`main.py`
#### 2. Coding Workspace
Located in the **center**.
Purpose:
- Write and edit code
- Develop application logic

Example code:
`print("Hello World")`
#### 3. Console
Located on the **right side**.

Purpose:
- Displays program output
- Shows messages from the interpreter

Running the code using the **Run** button executes the Python file and prints the output in the console.

Example output:
`Hello World`
### Adding HTML Files in a Python Project
A common question is whether HTML files can be used inside a Python project.
Answer:
Yes.
Replit allows adding additional files to the project.
Steps to add an HTML file:
1. Click **Add File** in the file explorer.
2. Provide the complete filename including extension.
Example:
`index.html`
Once added, HTML code can be written inside the file.
### Basic HTML Structure Example
Example structure used in the lecture:
```
DOCTYPE declaration  
html root element  
head section  
title tag  
body section  
```
Example page content:
A heading such as:
`This is my first web page`
The body section contains the visible content displayed in the browser.
### Running the Project
When the **Run** button is pressed in a Python project:
- Only **main.py** is executed
- HTML files are not automatically opened
Therefore, a **driver code** must be added in the Python file to trigger the HTML page.

Purpose of the driver code:
- Launch a small web server
- Render the HTML file in the Replit browser panel

Once the driver code is added and the program is run again:
- A browser window appears inside Replit
- The HTML page is displayed
### Adding Navigation Between Pages
Multiple HTML files can be used within the same project.
Example:
```
index.html  
acad.html
```
Navigation between pages can be implemented using an **anchor tag**.
Example concept:
Anchor tag with href pointing to another HTML file.
Example link text:
Go to acad
When the link is clicked, the browser loads the acad.html page.
### Creating Additional Pages
Steps demonstrated:
1. Create a new HTML file
acad.html
2. Add basic HTML structure
3. Add content such as a heading
Example heading:
This is the acad page
### Testing Navigation
After restarting the program:
- The index page loads
- A link to the acad page appears
- Clicking the link successfully opens the acad.html page

This confirms that:
- Multiple HTML files can exist in a Python project
- Navigation between them works correctly.
### Key Takeaways
Replit provides a simple environment for application development.
Important capabilities include:
- Creating Python projects
- Managing multiple project files
- Adding HTML pages
- Running applications through a Python driver file
- Viewing output in an embedded browser
- Linking multiple web pages using anchor tags
Replit can therefore serve as a convenient platform for building and testing small web applications.

---
---
## Lecture: Creating and Serving an HTML Document
### Building a Basic HTML Page and Hosting It Using a Python HTTP Server
##### Description: Demonstrates how to create a simple HTML document using a text editor, structure it using standard HTML tags, open it in a browser, and serve it across a network using Python’s built-in HTTP server.

---
### Development Environment Setup
To work with HTML documents, a few basic tools are required.

Typical setup used in the demonstration:
- A web browser (Chrome, Firefox, Brave, Chromium, etc.)
- A text editor (e.g., gedit or any code editor)
- A terminal for running commands
- A file browser to manage project files
These tools allow creating, editing, viewing, and serving web documents.
### Creating an HTML File
An HTML file is essentially a structured document that follows markup rules similar to XML.

Steps to create a new HTML document:
1. Create a folder structure to organize files.
2. Create a new file named:
`index.html`
Example command used in the terminal:
`touch index.html`
This creates an empty HTML file on the local machine.
Initially the file size is zero bytes.
### Basic HTML Document Structure
Every HTML document starts by declaring its document type.

Example concept:
DOCTYPE html
Purpose:
- Informs the browser that the file contains HTML content.
The main HTML structure contains the following elements:
```
html tag  
head section  
body section  
```

The entire document is enclosed inside:
```
html  
/ html
```
### Head Section
The head section contains metadata about the document.
Typical information placed in the head section includes:
Character encoding  
Document title  
Document description  
#### Character Encoding
Character encoding specifies how characters are stored.
Example encoding:
UTF-8

Reason:
UTF-8 supports a wide range of characters including many international languages.
This is specified using a meta tag.
#### Title Tag
The title defines the name of the page.
The title appears in the browser tab when the page is opened.

Example concept:
```
title  
My First HTML Page  
/ title
```
#### Description Metadata
Description metadata provides information about the page content.
Example description:
"This is an HTML page"
This is useful for search engines and document metadata.
### Body Section
The body section contains the visible content of the web page.
All information displayed in the browser window appears here.
Example elements added in the body:
Headers  
Text  
Sections of content
### Organizing Page Content Using Sections
Content inside the body can be organized using container elements such as div.
Example structure demonstrated:
Three sections were created:
- Introduction section
- Main section
- Footer section

Each section was implemented using a div element with a unique ID.
Example conceptual structure:
div id = intro  
div id = main  
div id = footer

Purpose of IDs:
- Identify different content areas
- Enable styling or scripting later
### Adding Content
Example content added to sections:

Introduction section:
- Header (h1)
- Introductory text

Main section:
- Main text content

Footer section:
- Footer header
- Footer text
Header elements such as h1 define large section headings.
### Viewing the HTML Document
Once the HTML file is saved, it can be opened directly in a browser.

Steps:
1. Locate the file
2. Open it with a web browser
The browser renders the HTML and displays the formatted content.

Example results:
- Page title appears in browser tab
- Introduction header appears
- Main section text appears
- Footer section appears
### Inspecting the Page
Modern browsers provide developer tools.
These tools allow developers to inspect the structure of the page.
Steps:
Right-click the page → Inspect
This opens the developer console.

Developer tools show:
- HTML structure
- Elements hierarchy
- Page layout
Hovering over elements highlights the corresponding part of the page.
### Serving HTML Across a Network
Opening the HTML file locally only allows viewing it on one machine.
To share the page across a network, a web server is required.
A web server serves files using HTTP over TCP/IP.

Examples of common web servers:
- Apache
- Nginx
For simplicity, Python’s built-in HTTP server can be used.
### Starting a Python HTTP Server
Python includes a simple HTTP server module.
Command used:
`python3 -m http.server`
This command starts a web server in the current directory.
Default settings:
```
IP address: 0.0.0.0  
Port: 8000
```
### Understanding the Server Address
0.0.0.0 is a special IP address.
It represents the local machine.
The page can be accessed using:
`localhost:8000`
or
`127.0.0.1:8000`
Both refer to the same machine.
### Accessing the Page from Other Devices
To access the page from other devices on the same network, the machine’s IP address must be used.
Command used to check IP address:
`ifconfig`
Example IP address:
`192.168.x.x`
Friends on the same network can access the page using:
`192.168.x.x:8000`
This allows sharing the web page across a LAN.
### Viewing Network Activity
Browser developer tools allow monitoring network communication.
Steps:
Open Developer Tools  
Go to Network tab  
Reload the page

The network panel shows:
- Requested document
- Server address
- File size
- Response time

Example information shown:
- Request headers
- Response headers
- Server information
- File content
This helps understand how browsers retrieve web content.
### Key Takeaways
HTML documents are structured markup files that define web page content.
Basic workflow:
1. Create an HTML file
2. Define structure using HTML tags
3. Add metadata in the head section
4. Add visible content in the body
5. Open the document in a browser
6. Serve the document using a web server
Python’s built-in HTTP server provides a simple way to host and share web pages across a network.

---
---
