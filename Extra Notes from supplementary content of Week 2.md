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
### Week 2 Extra Lecture 2
#### Separating Style and Content in HTML Using CSS
##### Description: Explains how to improve HTML styling by separating presentation from content using CSS. Demonstrates moving inline styles into internal styles within the head section and finally into an external CSS file, making styling reusable, maintainable, and efficient.

---
### Motivation for Separating Style and Content
In the previous lecture, styling was applied using **inline CSS**.

Example idea:
Each HTML tag had a style attribute.

Problems with inline styling:
- Repetition of styles across multiple elements
- Difficult to maintain
- Error-prone when updating styles
- Mixing content with presentation
- Hard to reuse styles across multiple pages
A better design approach is to **separate content from styling**.

This improves:
- Maintainability
- Reusability
- Code clarity
- Scalability for large websites
### Method 1: Internal CSS (Style Tag in Head)
The first improvement is to move styles from individual tags into a **style section inside the head tag**.

Example concept:
```
style  
CSS rules  
/style
```
This allows defining styles once and applying them across the document.
### Styling Using Tag Selectors
One way to apply CSS rules is using **tag selectors**.

Example idea:
```
table {  
  style rules  
}
```
This means the defined styles will apply to **all table elements** in the document.
Example rules previously used:
- border
- text alignment
- border collapse
Moving these rules to the style section eliminates the need to repeat them inside each table element.
### Applying Styles to Table Cells

Earlier, each table cell had styling applied individually.
Instead of repeating styles for each cell, styles can be applied using selectors.
Example selector concept:
```
td {  
  style rules  
}
```
This automatically applies the style to **all table data cells**.
Similarly, table header cells can be styled using:
```
th {  
  style rules  
}
```
### Combining Selectors
If multiple elements require the same style, selectors can be combined.

Example concept:
```
td, th {  
  shared style rules  
}
```
This reduces duplication and improves efficiency.
Example use case:
Applying borders to both data cells and header cells.
### Styling Table Headers
The table header row can be styled using a more specific selector.

Example concept:
```
table thead {  
  background color  
}
```
This allows styling the header row without affecting the rest of the rows.
Example color choices:
- green
- lightgreen
- hexadecimal colors like `#FF0000`
### CSS Color Representation
Colors in CSS can be represented using:
1. Named colors  
   Example: green, blue
2. Hexadecimal RGB values  
   Format:
`#RRGGBB`
Example:

`#FF0000` → red  
`#00FF00` → green  
`#0000FF` → blue
Editors often highlight color codes, helping detect spelling mistakes.
### Styling Alternate Rows
Tables with many rows become difficult to read.
Solution:
Use alternating row colors.
CSS provides a selector to target specific rows.

Example concept:
```
tr:nth-child(even) {  
  background color  
}
```
Meaning:
- Every even row receives the specified style.
Alternatively:
`tr:nth-child(odd)`
This creates a **striped table effect** improving readability.
### CSS Cascading Behavior
CSS is called **Cascading Style Sheets** because styles cascade through element hierarchies.
Example hierarchy:
body  
div  
table  
tr  
td

Key rule:
- Lower-level selectors override higher-level styles.
- More specific selectors override general ones.
Example:
A table may define center alignment.
A specific row may override it with left alignment.
### Limitations of Internal CSS
Using styles inside the head section improves maintainability but still has limitations.
Problem:
If multiple HTML pages exist, the same styles must be copied into every page.
This causes:
- Duplication
- Difficulty maintaining consistency
- Repeated updates across files
### Method 2: External CSS (Recommended)
The best practice is to move all styles into a **separate CSS file**.
Example file:
style.css
Steps performed:
1. Create a new file named:
style.css
2. Move all CSS rules from the HTML document into this file.
3. Remove style tags from the HTML file.
### Structure of CSS File
The CSS file contains only styling rules.
Example elements styled:
- `table`
- `td`
- `th`
- `thead`
- `tr:nth-child(even)`
The CSS file becomes a centralized location for styling.
### Linking CSS to HTML
The CSS file must be linked to the HTML document.
This is done inside the head section using a **link tag**.
Example concept:
```
link  
rel = stylesheet  
href = style.css
```
Purpose:
- Informs the browser that styling rules are located in style.css.
- Applies those styles to the HTML document.
If the CSS file is in the same folder, only the filename is required.
Otherwise a full URL may be provided.
### How Browsers Load HTML and CSS
When a page loads, the browser performs these steps:
1. Download the HTML document
2. Parse the HTML structure
3. Identify linked resources (CSS, scripts, images)
4. Download the CSS files
5. Apply styles to the HTML elements
6. Render the final page
Developer tools show this process in the **Network panel**.
Example sequence observed:
7. jnanpith.html downloaded first
8. style.css downloaded next
9. CSS applied during page rendering
This sequence can be visualized using a **waterfall timeline** in developer tools.
### Advantages of External CSS
External CSS provides several benefits:
Reusability:
- Same stylesheet can be used across multiple pages.
Consistency:
- All pages share identical styling rules.
Maintainability:
- Style changes require editing only one file.
Efficiency:
- Browsers can cache CSS files, improving loading speed.
Project scalability:
- Large applications can manage styling systematically.
### Key Takeaways
Three approaches to CSS styling were discussed:
1. Inline CSS  
   Style written directly inside HTML tags  
   Easy but inefficient
2. Internal CSS  
   Style defined inside the head section  
   Reduces duplication
3. External CSS  
   Style stored in a separate file and linked to HTML  
   Most scalable and maintainable approach
External stylesheets are the **standard practice in modern web development** because they allow efficient reuse and centralized control of visual design.

---
---
