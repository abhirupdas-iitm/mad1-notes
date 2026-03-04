### Week 2 Extra Lecture 1
#### Styling HTML Documents Using CSS (Inline Styling)
##### Description: Introduction to CSS and basic methods of styling HTML elements. Demonstrates how CSS properties can be applied directly to HTML tags using inline styling, how colors and borders can be applied to elements such as headers and tables, and how style inheritance works from higher-level elements to lower-level elements.

---
### Introduction to CSS
CSS stands for **Cascading Style Sheets**.

Purpose of CSS:
- Defines how HTML elements should appear on the screen
- Controls layout, colors, fonts, spacing, and other visual aspects
- Allows separation of **content** and **presentation**
Without CSS, HTML pages appear plain and unstyled.
### Development Environment
To experiment with CSS styling, the following tools are required:
- A modern browser (Chrome, Firefox, Brave, etc.)
- A text editor (e.g., gedit)
- A terminal
- Python 3 (for running a simple HTTP server)
- An example HTML file (jnanpith.html)
The HTML files are stored inside a project directory.

Example structure:
```
MAD1  
experiment1  
index.html  
jnanpith.html
```
### Running the Local Server
To view the HTML pages through a browser, a simple Python server can be started.
Command used:
`python3 -m http.server`
This starts a local web server on port **8000**.
The page can then be accessed in the browser using:
`localhost:8000`
If no specific file is given, the browser automatically opens:
index.html
Reason:
`index.html` is a **default filename** that web servers try to load when a directory is accessed.
To open another page, its exact path must be specified.
Example:
`localhost:8000/jnanpith.html`
### Structure of the Example HTML Page

The example page contains:
- A title and description
- A main section containing information about the **Jnanpith Award**
- A table listing awardees and languages
- A footer section with credits referencing Wikipedia

Initially the HTML page has **no styling**, making it visually plain.
### Adding CSS Styling
There are multiple ways to apply CSS.
The simplest method is **inline styling**.
Inline styling means:
- Adding CSS directly to an HTML element using the **style attribute**.

Example concept:
`style="property: value;"`
Multiple CSS properties are written as **key-value pairs** separated by semicolons.
Example concept:
property: value;
### Styling Headers
A style can be applied to make headers visually distinct.
Example property used:
background-color
Example idea:
Giving the header a light green background.
Colors can be specified in multiple ways:
1. Color names (e.g., green, blue)
2. Hexadecimal RGB values
Example hexadecimal structure:
`#RRGGBB`
Example:
`#00FF00`
Where:
- Red = 00
- Green = FF
- Blue = 00
This produces a green color.
### Styling Tables
Tables often require styling to improve readability.

Example improvements demonstrated:
- Adding background color to alternate rows
- Adding borders around tables and cells
- Aligning text inside cells
These enhancements improve visual clarity when reading table data.
### Alternating Row Colors
Reading large tables can be difficult when rows look identical.
Solution:
Apply background color to alternate rows.

Example idea:
Odd rows → light gray  
Even rows → default color
This improves readability when scanning rows quickly.
### Adding Borders to Tables
Borders help visually separate table cells.
Example CSS property used:
border
Border specification includes three parts:
- Thickness
- Border style
- Border color

Example concept:
`border: 1px solid black`
Meaning:
- Border width: 1 pixel
- Border style: solid
- Border color: black
### Border Behavior in Tables
When borders are added to both:
- The table
- Individual cells
It may create **double borders**.
To fix this issue, CSS provides a property:
`border-collapse`
Concept:
`border-collapse: collapse`
This merges adjacent borders into a **single border line**.
Result:
Cleaner and more readable tables.
### Text Alignment
Text alignment can be controlled using the CSS property:
`text-align`
Possible values:
- left
- right
- center
Example:
`text-align: center`
This centers text inside table cells.
### Applying Styles at Different Levels
CSS can be applied at different hierarchical levels.
Example hierarchy:
body  
div  
table  
row  
cell
Higher-level styles affect all nested elements.
Lower-level elements can **override** higher-level styles.
Example:
- Table may set text alignment to center
- A specific row may override alignment to left
This behavior demonstrates the **cascading nature of CSS**.
### Cascading Principle
CSS is called **Cascading Style Sheets** because:
Styles cascade from **parent elements to child elements**.
Key rule:
Lower-level styles override higher-level styles when conflicts occur.
Example hierarchy:
`body → div → table → row → cell`
If multiple styles exist, the most specific one takes precedence.
### Limitations of Inline Styling
Inline styling is easy to implement but has several drawbacks.
Problems:
- Repetition of style code
- Difficult to maintain
- Hard to update styles across multiple pages
- Increased risk of errors

Example issue:
If many elements require the same style, the same style must be repeated multiple times.
If a change is needed, every occurrence must be manually updated.
### Better Styling Approaches
Inline styling is mainly used for small experiments.
For larger applications, better methods include:
- Internal CSS stylesheets
- External CSS stylesheets
These approaches reduce duplication and improve maintainability.
These methods are introduced in later lectures.
### Key Takeaways
CSS controls the visual presentation of HTML documents.
Important concepts demonstrated:
- Inline CSS styling
- Color specification using names and hexadecimal values
- Styling tables with borders
- Improving readability using alternate row colors
- Using border-collapse for cleaner table borders
- Controlling text alignment
- Understanding cascading style behavior
Inline styling is simple but inefficient for large projects.
More scalable styling methods are introduced in later lessons.

---
---
