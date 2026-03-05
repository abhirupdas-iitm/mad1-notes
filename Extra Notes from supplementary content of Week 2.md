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
### Week 2 Extra Lecture 3
#### CSS Selectors for Styling HTML Documents
##### Description: Explains how CSS selectors are used to target specific elements within an HTML document for styling. Covers tag selectors, class selectors, ID selectors, relationship selectors (descendant and child), pseudo-class selectors, pseudo-element selectors, and attribute selectors.
### Purpose of CSS Selectors
CSS selectors allow developers to **identify specific elements within an HTML document** and apply styles to them.
Instead of styling every element individually, selectors provide a way to **target groups of elements efficiently**.
Selectors are the core mechanism that connects CSS styling rules to HTML elements.
### Example Setup for Experiments
A simple HTML file (`test.html`) is created to experiment with selectors.
Basic structure of the file:
- HTML root
- Head section with style definitions
- Body containing a **form**
- The form contains:
  - Paragraph labels
  - Input fields
  - Div sections
Initially, the page appears plain when opened in a browser.
CSS selectors are then applied to modify the appearance of different parts of the page.
### 1. Tag Selectors
Tag selectors apply styling to **all instances of a particular HTML tag**.
Example idea:
```
p {  
font-size: 20px;  
}
```
Effect:
- Every paragraph element (`<p>`) in the document receives the specified style.
- In the example page, all paragraph labels become larger.
This method is useful when the same styling should apply to **all occurrences of a tag**.
### 2. Class Selectors
Class selectors allow styling only elements that belong to a **specific class**.
Class selectors start with a **dot (`.`)**.
Example concept:
```
.name_para {  
font-size: 20px;  
}
```
To apply this style, the HTML element must include the class attribute.
Example idea:
`<p class="name_para">`

Advantages of class selectors:
- The same class can be applied to **multiple elements**
- Not restricted to a specific tag
- Reusable across different parts of the document
For example, the same class could be applied to paragraphs, divs, or other elements.
### 3. ID Selectors
ID selectors apply styling to **one specific element** identified by its unique ID.
ID selectors begin with **`#`**.
Example concept:
```
#personal {  
color: blue;  
}
```
If a div has the attribute:
`id="personal"`
then all elements inside that div inherit the styling defined for that ID.
Key characteristics:
- IDs should be **unique within a document**
- Used for styling or referencing specific sections
Example behavior:
If the `#personal` div contains text, paragraphs, or other elements, the style affects all content inside it.
### 4. Relationship Selectors
Relationship selectors style elements based on their **position in the HTML hierarchy**.
Two main relationships exist:
#### Descendant Relationship
A descendant is **any element inside another element**, regardless of depth.
Example:
```
form input {  
background-color: yellow;  
}
```
Meaning:
- Select every `<input>` element inside a `<form>`
This includes inputs nested within multiple levels of elements.
Example hierarchy:
body  
└── form  
    └── div  
        └── input
The input is still a descendant of the form.
#### Child Relationship
A child selector targets **only direct children** of an element.
Symbol used:
`>`
Example concept:
```
form > input {  
background-color: yellow;  
}
```
Meaning:
- Select only input elements that are **direct children of the form**
- Inputs inside nested `divs` will **not be selected**
Difference summary:

| Selector     | Meaning              |
| ------------ | -------------------- |
| form input   | All descendants      |
| form > input | Only direct children |
### 5. Pseudo-Class Selectors
Pseudo-class selectors apply styles based on **element states or structural conditions**.
They use a **single colon (`:`)**.
Example types:
- hover
- visited
- nth-child
#### Hover Example
Pseudo-class for mouse interaction:
:hover
Example concept:
```
form input:hover {  
background-color: red;  
}
```
Effect:
- Input field turns red **when the mouse hovers over it**
Without hovering, the input remains unchanged.
This selector responds to **user interaction events**.
#### Structural Pseudo-Class: nth-child
Structural pseudo-classes target elements based on **their position within a parent**.
Example concept:
```
tr:nth-child(even) {  
background-color: lightgray;  
}
```
Meaning:
- Select table rows (`tr`)
- Apply styling to **even-numbered rows**
This technique creates alternating row colors in tables.
Example result:
Row 1 → normal  
Row 2 → gray  
Row 3 → normal  
Row 4 → gray
This improves table readability.
### 6. Pseudo-Element Selectors
Pseudo-element selectors style **specific parts of an element's content**.
They use **double colons (`::`)**.
Example concept:
```
p::first-letter {  
color: red;  
font-size: 20px;  
}
```
Meaning:
- Target the **first letter of each paragraph**
- Apply the specified styles

This technique is commonly used in:
- magazines
- articles
- blog layouts
where the first letter of a paragraph is emphasized.
#### Other Examples of Pseudo-Elements
Common pseudo-elements include:
- `::first-line`
- `::before`
- `::after`
- `::selection`
These allow styling specific portions of content.
### 7. Attribute Selectors
Attribute selectors style elements based on the **presence or value of attributes**.
Example HTML attribute:
`<input type="text">`
Here:
- `type` → attribute
- `text` → attribute value
#### Attribute Value Selector
Example concept:
```
input[x="y"] {  
background-color: red;  
}
```
Meaning:
- Select all `<input>` elements
- Only if attribute `x` has value `y`
Example:
`<input x="y">`
will be styled.
If the attribute value changes (e.g., `x="z"`), the style will not apply.
#### Example Behavior
Suppose two inputs contain:
x="y"
These will be styled.
If another input contains:
x="z"
the style will not affect it.
Attribute selectors allow highly precise styling.
### Cascading Nature of CSS
CSS rules cascade according to specificity and hierarchy.
General rules:
- More specific selectors override general ones
- Later rules override earlier ones when specificity is equal
Example priority order (simplified):
Tag selector  
→ Class selector  
→ ID selector
This layered behavior is why CSS is called **Cascading Style Sheets**.
### Summary of Selector Types

| Selector Type           | Example          | Purpose                                 |
| ----------------------- | ---------------- | --------------------------------------- |
| Tag selector            | `p`              | Style all elements of a tag             |
| Class selector          | `.name_para`     | Style elements with a specific class    |
| ID selector             | `#personal`      | Style a unique element                  |
| Descendant selector     | `form input`     | Style nested elements                   |
| Child selector          | `form > input`   | Style direct children only              |
| Pseudo-class selector   | `:hover`         | Style based on element state            |
| Pseudo-element selector | `::first-letter` | Style part of element content           |
| Attribute selector      | `input[x="y"]`   | Style elements with specific attributes |
### Key Takeaways
CSS selectors provide powerful mechanisms for targeting elements within HTML documents.
Important categories include:
- Tag-based selectors
- Class and ID selectors
- Relationship selectors
- Pseudo-class selectors
- Pseudo-element selectors
- Attribute selectors
Understanding selectors is essential for building **structured, maintainable, and flexible CSS styling systems**.

---
---
