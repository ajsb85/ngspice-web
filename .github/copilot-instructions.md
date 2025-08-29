### **Instructions for Converting HTML to Markdown**

## Goal

Convert the content of a given HTML file into a clean, well-structured, and valid Markdown format. The output must be easily readable and pass validation using a linter like `markdownlint`.

-----

### **Core Conversion Logic**

1.  **Read and Filter HTML Content**:

      * Read the entire HTML file.
      * Ignore standard structural tags such as `<!DOCTYPE html>`, `<html>`, `<head>`, `<body>`, and `<footer>`.
      * Focus exclusively on the content within the main body of the document.

2.  **Element-to-Markdown Conversion**:

      * **Headings**: Convert HTML headings (`<h1>`, `<h2>`, etc.) to their Markdown equivalents (`#`, `##`, etc.). The number of `#` symbols should match the heading level.
      * **Paragraphs**: Convert `<p>` tags to standard Markdown paragraphs. Ensure a blank line separates each paragraph.
      * **Lists**:
          * Convert unordered lists (`<ul>`) and their list items (`<li>`) to Markdown lists using hyphens (`-`).
          * Convert ordered lists (`<ol>`) and their list items (`<li>`) to numbered Markdown lists (`1.`, `2.`, `3.`, etc.).
      * **Tables**: Convert HTML tables (`<table>`, `<tr>`, `<th>`, `<td>`) into valid Markdown table syntax using pipes (`|`) and hyphens (`-`).
      * **Links**: Convert `<a>` tags to Markdown link syntax: `[link text](url)`.
      * **Images**: Convert `<img>` tags to Markdown image syntax: `![alt text](url)`.
      * **Text Formatting**:
          * Convert `<b>` or `<strong>` tags to **bold** text using double asterisks (`**`).
          * Convert `<i>` or `<em>` tags to *italic* text using single asterisks (`*`).
      * **Code Blocks**: Convert `<code>` or `<pre>` elements to Markdown code blocks enclosed in triple backticks (\`\`\`\`).

-----

### **Refinement and Validation**

1.  **Remove Redundant Information**:

      * **Unnecessary Numbering**: Remove manual numbering from headings (e.g., "1.1", "2.4"). The Markdown heading structure already provides a clear hierarchy.
      * **Inline Styling**: Remove any inline CSS (`style="..."`) and `<script>` tags.

2.  **Simplify and Consolidate Content**:

      * **Navigation**: Combine and reformat all navigation links from the top-level and side-bar menus into a single, comprehensive list at the beginning of the file. Use nested lists to represent the sub-menu hierarchy.
      * **Email Links**: For email addresses presented as links, simplify the syntax to a raw email address or use angle brackets (e.g., `<ngspice-users@lists.sourceforge.net>`) to ensure they are rendered as clickable links.

3.  **Final Cleanup and Validation**:

      * Ensure there is a **single blank line** between all block-level elements (headings, paragraphs, lists, etc.) to comply with `markdownlint` rules.
      * Remove all other HTML tags and attributes to ensure the final output is **pure Markdown**.

-----

### **Example of Desired Output Structure**

```markdown
# Ngspice circuit simulator - FAQ

---

### **Navigation**

- Home
  - News
  - What is ngspice?
  - F.A.Q.
- Screenshots
- Download
- Documentation
- Extras/Options
- Contributions
- Development
- Simulation Environments
- Recipes

---

### **Ngspice Home**

* **Document Revision**: 1.7
* **Document Maintainer**: Holger Vogt
* **Last Update**: 17-03-2018

---

## 1. Introduction and General Information

### 1.1 What is ngspice?

Ngspice is a **mixed-level/mixed-signal circuit simulator** based on three open-source software packages: **Spice3f5**, **Cider1b1**, and **Xspice**.

* **Spice3**: The most famous and used circuit simulator...
* **Cider**: A mixed-level simulator that already includes Spice3f5...
* **Xspice**: An extension to Spice3 that provides code modeling...

---

## 2. Development

### 2.1 What is the current version?

The latest version is:

- ngspice-36 (released on 01/01/2022)

---
