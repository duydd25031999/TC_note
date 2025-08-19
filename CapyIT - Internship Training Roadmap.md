# **Introduction**

## **Information**

This internship training program is designed to provide aspiring developers with a comprehensive foundation in web development. It serves as a structured learning path where interns engage in both theoretical learning and practical project work. Over the course of the program, participants will work through fundamental concepts in programming and modern development practices while simultaneously applying this knowledge to build a real web application. The aim is to simulate a full-stack development experience at a junior level, giving interns a well-rounded overview of the technologies and processes involved in creating a web application.

## **Background**

The program was initiated to address a common gap in specialization-focused training. Many interns enter the field aiming to become back-end developers or DevOps engineers, yet they often lack exposure to the full spectrum of web development. By ensuring interns learn the basics of front-end, back-end, and even some DevOps concepts, this internship lays down a general knowledge base. With a solid understanding of how each layer of web development works together, interns will be better prepared for any niche they choose later on. Whether they eventually specialize as a front-end developer, back-end developer, or DevOps specialist, they will carry forward a stronger, more holistic skill set.

## **Vision**

The vision of this internship training is to produce capable, self-sufficient junior developers who can confidently contribute to real projects. Rather than sitting in a classroom absorbing theory, interns in this program learn primarily by doing – they will collaborate on building a complete project from scratch. This project-based approach, coupled with guided self-study, encourages critical thinking and problem-solving. Through the process, interns also learn professional responsibility: they are expected to take ownership of tasks, meet deadlines, and adapt to feedback, mirroring the accountability found in a real work environment. By the end of the training, the goal is for each intern to have not only improved their technical skills but also developed the mindset and habits of a proactive, responsible developer.

## **Scope & Limitations**

This internship program focuses on the completion of a single real-world web development project at a junior developer level. Interns will function as full-stack developers for this project, tackling tasks from implementing user interfaces to setting up basic server-side logic and interacting with a database. The training combines hands-on work on project tasks with a comprehensive checklist of topics for self-study, ensuring coverage of fundamental concepts. However, the scope is deliberately limited to foundational skills and the requirements of the chosen project. It will not delve into every advanced or specialized topic in web development or DevOps. The intent is to provide breadth and practical experience — a solid launching pad — while recognizing that true mastery in any specific area will require further learning and experience beyond this program.

# **Checklist**

## **A. Fundamental**

### **Software Approach (Scrum)**

* Task management: Estimation, Log Work, Due Date, Kanban Board

* Scrum Events: Sprint Planning, Daily Meeting, Sprint Review, Sprint Retrospective

### **Programming Language (Java, JavaScript)**

* Virtual Machine: JVM, JavaScript Engine

  * Understand role in code execution.

* Compiler & Memory Management:

  * Compiler vs interpreter: when each is used.

  * Compilation steps: Lexical → Syntax → Semantic → Optimization → Code Generation.

  * Compile-time vs run-time errors: real examples.

  * Source code to executable process.

  * Role of transpiler (TypeScript → JS), JDK.

  * Garbage collection basics and memory allocation in Java vs JS.

* Data Types:

  * Primary: integer, float, boolean \- size limits, defaults.

  * Reference: objects, arrays, functions \- store memory references.

  * Memory storage differences between primary vs reference.

  * Deep vs shallow copy.

  * Mutability vs immutability \- examples in Java & JS.

### **Coding Style & Principles**

* OOP: 4 principles, real-world use.

* SOLID: each principle with an example.

* Design Patterns:

  * Categories: Creational, Structural, Behavioral.

  * Common: Singleton, Factory, Observer, Dependency Injection.

  * When to apply \+ pitfalls to avoid.

* Coding Conventions:

  * Follow standard style guides (Google Java, Airbnb JS, Gitflow) before customization.

  * Consistent naming, indentation, and documentation.

## **B. Web development**

### **Internet & Web Fundamentals**

* How the web works (client–server model).

* HTTP & HTTPS:

  * HTTP methods: GET, POST, PUT, DELETE.

  * Status code categories: 2xx, 3xx, 4xx, 5xx.

  * HTTPS purpose: encryption, authentication, data integrity.

* Domains, DNS, hosting:

  * How DNS resolution works.

* URL structure: protocol, domain, path, query, hash.

### **Project Setup & Environment**

* Git & GitHub/GitLab for version control (clone, commit, push, branch).

* Dependency management:

  * Maven (pom.xml), npm (package.json).

  * Semantic versioning rules.

* CLI basics for project setup & navigation.

* Folder & file structure conventions (frontend/backend examples).

### **Web Architecture Basics**

* Static vs dynamic websites (examples & when to use).

* Three-tier architecture: Presentation (Front-end) – Logic (Back-end) – Database.

* REST API concept & JSON format.

  * Basic API call demonstration (Postman or curl).

## **C. Front-end**

## *Knowledge training through practical work with projects*

### **Non-Semantic HTML & CSS Basics**

* **Goal**: Build common UI elements from the design without worrying about semantic correctness yet.

* **Checklist**:

  * Understand HTML tags: \<div\>, \<span\>, \<img\>, \<a\>, \<button\>, \<table\>.

  * Apply inline styles & CSS selectors (class, id, element).

  * Use CSS box model (margin, padding, border, width/height).

  * Understand display types: block, inline, inline-block, flex basics.

  * Apply basic typography (font-size, font-weight, line-height).

### **SASS, Responsive, UI Kit setup**

* **Goal**: Create a maintainable, scalable UI kit for the ecommerce project.

* **Checklist**:

  * Install & configure SASS in the project.

  * Use variables for colors, fonts, spacing.

  * Use nesting for styling hierarchy.

  * Apply BEM (Block-Element-Modifier) naming convention.

  * Create reusable mixins for media queries.

  * Understand responsive design principles: fluid grid, breakpoints, mobile-first.

### **Semantic HTML, SEO, Alt Text**

* **Goal**: Improve accessibility and SEO friendliness of the website.

* **Checklist**:

  * Replace / with semantic tags (, , , , ).

  * Use proper heading hierarchy ( → ).

  * Add alt attributes to all images with meaningful descriptions.

  * Add meta tags for title, description, viewport.

  * Understand role of “aria-\*” attributes for accessibility.

  * Use descriptive link text.

### **JavaScript Basics (UI Effects)**

* **Goal**: Enhance user experience with basic interactive features.

* **Checklist**:

  * Understand DOM selection (getElementById, querySelector).

  * Add event listeners (click, mouseover, input).

  * Manipulate DOM elements (innerHTML, classList, styles).

  * Toggle classes for showing/hiding elements.

  * Understand the difference between var, let, const.

### **Front-end Framework (React)**

* **Goal**: Modularize UI using React components.

* **Checklist**:

  * Setup React project with Vite or CRA.

  * Create functional components for UI elements.

  * Pass props to components.

  * Map over arrays to render lists.

  * Use state for interactive UI.

  * Apply CSS Modules or Styled Components (optional).

### **JavaScript Advanced (Mock API & Integration)**

* **Goal**: Simulate backend data and integrate with UI.

* **Checklist**:

  * Understand JSON structure for API responses.

  * Use fetch() or axios to call local mock API.

  * Handle async/await and error handling.

  * Understand basic REST principles (GET, POST).

  * Update UI dynamically based on API data.

## **D. Database**

### **Basic SQL Syntax**

* **Goal**: Understand and use fundamental SQL commands to create and manipulate data.

* **Checklist**:

  * SQL statement types: DDL (CREATE, ALTER, DROP), DML (INSERT, UPDATE, DELETE), DQL (SELECT).

  * Syntax rules (keywords, identifiers, case sensitivity).

  * Creating a table with appropriate data types.

  * Inserting, updating, and deleting rows.

  * Simple SELECT with WHERE, ORDER BY, LIMIT.

### **Relationship Design, Data Constraints, Database Design**

* **Goal**: Design an ecommerce database schema with proper relationships and constraints.

* **Checklist**:

  * Understand primary keys (PK) and foreign keys (FK).

  * One-to-one, one-to-many, many-to-many relationships.

  * Common constraints: NOT NULL, UNIQUE, DEFAULT, CHECK.

  * Normalization basics (1NF, 2NF, 3NF).

  * ERD (Entity Relationship Diagram) creation.

### **Join Queries & Subqueries**

* **Goal**: Retrieve related data from multiple tables.

* **Checklist**:

  * INNER JOIN, LEFT JOIN, RIGHT JOIN, FULL JOIN.

  * Use of table aliases.

  * Subqueries in SELECT, FROM, WHERE clauses.

  * Filtering joined data.

### **Advanced Functions**

* **Goal**: Use built-in SQL functions for aggregation, formatting, and conditional logic.

* **Checklist**:

  * Aggregate functions: COUNT, SUM, AVG, MIN, MAX.

  * GROUP BY & HAVING.

  * String functions: CONCAT, SUBSTRING, LOWER, UPPER.

  * Date/time functions: NOW, DATE\_FORMAT.

  * Conditional expressions: CASE WHEN.

### **Query Optimization & Indexes**

* **Goal**: Improve query performance and understand indexing strategies.

* **Checklist**:

  * How indexes work and when to use them.

  * Single-column vs multi-column indexes.

  * Impact of indexes on read vs write performance.

  * Analyzing queries with EXPLAIN.

  * Avoiding SELECT \*.

### **Transactions, Stored Procedures, Functions**

* **Goal**: Manage multiple step operations and encapsulate business logic in the database.

* **Checklist**:

  * Transaction basics: START TRANSACTION, COMMIT, ROLLBACK.

  * ACID properties.

  * Create stored procedures for repetitive tasks.

  * Create user-defined functions.

  * Error handling in stored routines.

## **E. Back-end**

### **Back-end Modules: Middleware, Service, Controller, Model**

* **Goal**: Understand modular design and implement a clean code structure. Build the main ecommerce functionality.

* **Checklist**:

  * Controller: Handles incoming requests & responses.

  * Service: Business logic layer.

  * Model: Data representation, ORM (Sequelize, Mongoose, JPA).

  * Middleware: Functions that run before/after request handling.

  * Request/response lifecycle in the framework.

  * API Document: Swagger/OpenAPI

### **Authentication & Authorization**

* **Goal**: Secure the API with login and role-based access control.

* **Checklist**:

  * Difference between authentication (AuthN) & authorization (AuthZ).

  * JWT (JSON Web Token) basics: payload, signature, expiration.

  * Password hashing (bcrypt).

  * Role-based access (admin, customer).

  * Protecting routes with middleware.

### **API Error Handling & Validation**

* **Goal**: Make API robust and user-friendly.

* **Checklist**:

  * Centralized error handling middleware.

  * HTTP status code usage.

  * Data validation.

  * Custom error messages.

  * File Upload & Static Files

## **F. DevOps**

### **Development Environments & Configurations**

* **Goal**: Understand different environments and configs before deploying.

* **Checklist**:

  * Difference between dev, staging, and production environments.

  * Environment variables and secret management.

  * .env usage and configuration best practices.

  * Importance of consistency between environments.

### **Docker & Containerization**

* **Goal**: Package the application into portable containers.

* **Checklist**:

  * What is Docker? Difference between image, container, Dockerfile.

  * Writing a Dockerfile for the back-end.

  * Multi-stage builds for smaller images.

  * Docker Compose for multiple service apps (back-end \+ DB).

  * Volume mounting and persistence.

### **CI/CD Fundamentals**

* **Goal**: Automate build and test process for every code change.

* **Checklist**:

  * Understand CI/CD pipeline stages: build, test, deploy.

  * GitHub Actions / GitLab CI basics.

  * Writing a simple pipeline (YAML).

  * Running automated tests in the pipeline.

  * Build Docker image in pipeline.

### **Deployment**

* **Goal**: Push application to a real server/cloud.

* **Checklist**:

  * Difference between manual vs automated deployment.

  * Deploy options: VPS, Heroku, AWS, Render, Vercel.

  * Using Docker for deployment.

  * Database migrations in deployment.

# **Roadmap 0: Fundamentals of Web Development**

## *This is the mandatory initial roadmap, then internships move to different project roadmaps.*

## **Milestone 1: Fundamentals of Programming**

### **Software Approach (Scrum)**

1. **Join to project on task management tool:**

   1. Introduce overview about project, task: Task Status, Kanban Board,  Task Metadata

   2. Manage own task: Assigned, Estimation, Due Date,  Log Work

2. **Follow Scrum Events \- join a complete sprint:** 

   1. Sprint Planning

   2. Daily Meeting

   3. Sprint Review

   4. Sprint Retrospective

### **Programming Language (Java, JavaScript)**

**Study knowledge, write notebook and make own small examples:**

1. Virtual Machine: JVM, JavaScript Engine  
   * Understand role in code execution.  
2. Compiler & Memory Management:  
   * Compiler vs interpreter: when each is used.  
   * Compilation steps: Lexical → Syntax → Semantic → Optimization → Code Generation.  
   * Compile-time vs run-time errors: real examples.  
   * Source code to executable process.  
   * Role of transpiler (TypeScript → JS), JDK.  
   * Garbage collection basics and memory allocation in Java vs JS.  
3. Data Types:  
   * Primary: integer, float, boolean \- size limits, defaults.  
   * Reference: objects, arrays, functions \- store memory references.  
   * Memory storage differences between primary vs reference.  
   * Deep vs shallow copy.  
   * Mutability vs immutability \- examples in Java & JS.

### **Coding Style & Principles**

1. **Study knowledge, write notebook and make own small examples:**  
   1. OOP: 4 principles, real-world use.  
   2. SOLID: each principle with an example.  
   3. Design Patterns:  
   * Categories: Creational, Structural, Behavioral.  
   * Common: Singleton, Factory, Observer, Dependency Injection.  
   * When to apply \+ pitfalls to avoid.

2. **Write own Coding Conventions:**  
   1. Follow standard style guides (Google Java, Airbnb JS, Gitflow) before customization.  
   2. Consistent naming, indentation, and documentation.

## **Milestone 2: Web Development Basics**

### **Internet & Web Fundamentals**

**Study knowledge, write notebook and make own small examples:**

* How the web works (client–server model).

* HTTP & HTTPS:

  * HTTP methods: GET, POST, PUT, DELETE.

  * Status code categories: 2xx, 3xx, 4xx, 5xx.

  * HTTPS purpose: encryption, authentication, data integrity.

* Domains, DNS, hosting:

  * How DNS resolution works.

* URL structure: protocol, domain, path, query, hash.

### **Project Setup & Environment**

1. **Create own 2 base project for Front-end, Back-end:**

* Git & GitHub/GitLab for version control (clone, commit, push, branch).

* Dependency management:

  * Maven (pom.xml), npm (package.json).

  * Semantic versioning rules.

* CLI basics for project setup & navigation.

* Folder & file structure conventions (frontend/backend examples).

### **Web Architecture Basics**

1. **Create homepage (landing page), 404 page without styles:**  
   * Learn about Static pages  
2. **Create some examples about dynamic pages and APIs:**  
   * Static vs dynamic websites (examples & when to use).

   * REST API concept & JSON format.

   * Basic API call demonstration (Postman or curl).

3. **Study knowledge, write notebook and make own small examples:**

   * Three-tier architecture: Presentation (Front-end) \- Logic (Back-end) \- Database.

# **Roadmap 1: Motelo** 

## **Milestone 1: Front-end Development**

### **Non-Semantic HTML & CSS Basics**

1. **Create style guide page \- showing common UI components (without CSS):**

   * Understand HTML tags: \<div\>, \<span\>, \<img\>, \<a\>, \<button\>, \<table\>.

2. **Create common CSS: Color, Typography, Box-shadow, … :**

   * Understand display types: block, inline, inline-block, flex basics.

   * Apply basic typography (font-size, font-weight, line-height).

3. **Apply CSS for common UI components (for desktop only):**

   * Apply inline styles & CSS selectors (class, id, element).

   * Use CSS box model (margin, padding, border, width/height).

### **SASS, Responsive, UI Kit setup**

1. **Install & configure SASS in the project:**

   * Learn about SASS in the project

2. **Transfer common CSS to common SASS:**

   * Use variables for colors, fonts, spacing.

   * Use nesting for styling hierarchy.

   * Apply BEM (Block-Element-Modifier) naming convention.

3. **Apply responsive style for common components:**

   * Create reusable mixins for media queries.

4. **Create static mock-up pages (without Javascript):**

   * Understand UI layout components

   * Understand responsive design principles: fluid grid, breakpoints, mobile-first.

### **Semantic HTML, SEO, Alt Text**

### **Knowledge Checklist:**

* Master the basics of HTML and CSS for building user interfaces. Know commonly used HTML tags such as \<div\>, \<span\>, \<img\>, \<a\>, \<button\>, \<table\>, and when to use them. Learn how to apply CSS to style elements, whether by writing inline styles or (preferably) using stylesheets with selectors targeting elements by tag, class, or id.

* Understand the CSS **box model** (how margins, padding, borders, and content form an element’s rectangle) and how to size and space elements on a page. Get familiar with CSS display properties: how block-level elements (like \<div\>) behave versus inline elements (like \<span\>), and the use of inline-block. Start exploring CSS Flexbox for basic layout needs (e.g., to create a navigation bar or a grid of cards). Also, apply basic typography styling (setting font families, sizes, weights, and line-heights) to make text content clear and attractive.

* Set up and use a CSS preprocessor like **SASS** to improve maintainability of your styles. For the Motelo project, configure SASS compilation in your build (or use a tool like Webpack/Vite if using React later). Use SASS features such as variables (for consistent colors, font sizes, spacing values across the site) and nesting (to organize CSS rules in a way that mirrors HTML structure). Create reusable mixins, for example a mixin for common media query breakpoints, to keep your CSS DRY responsive (Don’t Repeat Yourself). Also, adopt a class naming convention like **BEM (Block-Element-Modifier)** to keep your CSS classes organized and meaningful (e.g., use .listing-card\_\_title instead of generic class names).

* Understand responsive design principles. Design the Motelo front-end to be mobile-first – start with a layout for small screens and then add CSS media queries at specific breakpoints to adapt the layout for tablets and desktops. Use a fluid grid or flexbox to ensure elements resize or reposition gracefully. Concepts like percentage widths, max-width, and using CSS breakpoints (e.g., @media (min-width: 768px) { … }) are key to making the application usable on different devices.

* Improve HTML semantics and accessibility. Refactor your initial HTML by replacing non-semantic containers (\<div\>/\<span\>) with meaningful elements: for example, use \<header\> for the top banner or navigation, \<main\> for the main content area, \<nav\> for navigation menus, \<article\> or \<section\> for distinct content sections like a listing description, and \<footer\> for the page footer. Maintain a proper heading hierarchy (one \<h1\> for the page title, and \<h2\>-\<h6\> for subsections as needed). Add alt attributes to all images (e.g., property photos) with descriptive text so that visually impaired users or search engines understand the image content. Include essential meta tags in the page’s \<head\> (such as a descriptive \<title\>, a meta description for SEO, and a viewport meta tag for responsive behavior). Understand the basics of ARIA attributes (Accessible Rich Internet Applications) that can improve screen reader interactions, and use descriptive link text (e.g., “View details of Apartment A” instead of “click here”) to make the interface more accessible and SEO-friendly.

* Use JavaScript to add interactive behavior to the UI. Practice DOM manipulation: selecting elements by document.getElementById or querySelector and changing their content or styles (e.g., showing or hiding parts of the page). Learn to attach event listeners for common events like click (for buttons and links), submit (for forms), mouseover (for hover effects), etc., to make the page respond to user actions. For example, you might show a dropdown menu on a button click or validate a form on submission. Also, understand the differences in variable declaration (var vs let vs const) and why modern JavaScript prefers block-scoped let/const for better code reliability.

* Get introduced to a front-end framework/library (such as **React**). Set up a React project (using a tool like Create React App or Vite for fast setup). Learn to create modular, reusable UI components – for instance, a ListingCard component that displays housing information, or a NavBar component for the site header. Practice passing data into components via **props** (e.g., a listing component receives a title, image URL, price, etc.) and rendering lists of components using arrays (for example, mapping through an array of listings to produce a list of ListingCard elements). Manage component **state** for interactivity (such as a controlled form input for search, or toggling a component’s visibility). Additionally, explore ways to style in React, like using CSS Modules for scoping CSS to a component or using a library like styled-components.

* Learn how to integrate the front-end with back-end data through APIs. Understand the structure of JSON data as it might come from the Motelo back-end (for example, an array of listing objects where each object has fields like id, title, location, price, etc.). Use the browser’s **Fetch API** or a library like Axios to make HTTP requests from your front-end. For instance, fetch a list of housing listings from a mock or real API endpoint and then update the state of your application to display those listings. Handle asynchronous operations using **async/await** or Promises – manage loading states and catch any errors (like network failures or 404 responses) to display appropriate messages to the user. Reinforce understanding of REST by performing the full create-read-update-delete (CRUD) cycle on the front-end: e.g., sending a POST request when a new listing is submitted via a form, or sending a DELETE request to remove a listing, etc., and updating the UI based on the response.

### **Project Tasks:**

1. **Static Layout Implementation:** Using the Motelo project’s design requirements, build the static structure of key pages with HTML and CSS. Start with the **Home page** that lists available rentals: create a grid or list of placeholder listings (each could be a \<div\> or card with a title, image, price, and short description). Also craft a **Listing Details page** that will show detailed info about a selected property (e.g., larger images, detailed description, amenities, contact info). In addition, create simple pages for **User Registration/Login** (forms for users to create an account or sign in). At this stage, focus on layout and style: use basic \<div\> containers, apply classes, and write CSS to position elements (like a navigation bar at top, a list of listings in multiple columns, etc.). Don’t worry about full semantic correctness yet – the goal is to get the visuals in place. Use placeholders for data (hard-coded listing titles, lorem ipsum text, etc.).

2. **Apply Styling and Responsiveness:** Improve the styling by organizing your CSS using SASS. For example, create \_variables.scss for theme colors (maybe a primary color for headers or buttons) and typography settings. Refactor your CSS into SASS partials (like \_header.scss, \_listingCard.scss, etc.) for each major component or section, then import them into a main stylesheet. Implement responsive design: use media queries in your SASS to adjust the layout for smaller screens (perhaps a single column list on mobile, versus a grid on desktop). Ensure that images and text scale appropriately – test the pages by resizing your browser or using device emulation to see that the layout works on mobile devices. Commit these styling changes, noting that the interface is now mobile-friendly and better organized.

3. **Semantic HTML & Accessibility:** Refine your HTML now that the basic layout is working. Replace any non-semantic tags with semantic ones (e.g., wrap the listing cards container in a \<main\> tag, use \<header\> for the top navigation section, etc.). Add alt text to all images used (for example, alt=“Photo of \[Property Name\] in \[Location\]”), and double-check your heading levels (the home page might have an \<h1\> like “Available Rentals” and each listing title could be an \<h2\>). Insert appropriate meta tags into the \<head\> of your pages (a descriptive title and meta description containing keywords like “student housing, Motelo, rentals near FPT University”, and a \<meta name=“viewport” content=“width=device-width, initial-scale=1”\> for responsiveness). If your page has interactive elements like a modal or custom controls, consider adding ARIA attributes or roles to make them screen-reader friendly. This task will improve the site’s usability and SEO, which you can verify by running an HTML validator or accessibility checker on your pages.

4. **Basic Interactivity with JavaScript:** Add client-side scripts to enhance user experience on the Motelo front-end. For example, implement a **toggle for a mobile menu**: use JavaScript to show or hide the navigation links when a hamburger icon is clicked on a small screen. Another idea is to add **form validation** on the registration form: when the user clicks “Sign Up”, use JS to check that all required fields are filled and display a friendly error message next to any missing/incorrect field (and prevent form submission until fixed). You could also implement a simple **image gallery** on the listing details page – when a user clicks a thumbnail image, use JS to change the source of a main display image. These tasks involve adding event listeners (for clicks or form submissions) and DOM manipulation (changing classes or element attributes) to respond to user actions. Test each interactive feature in the browser to ensure it works as expected.

5. **Set Up a React Project (Optional/Advanced):** If the plan is to use React for the final product, now is a good time to migrate your static pages into a React application. Use a tool like Create React App or Vite to scaffold a new React project named motelo-frontend. Re-create your pages as React components: for example, a HomePage component that imports and maps many ListingCard components, and a ListingDetailPage component that shows one listing in detail. This will involve splitting your existing HTML structure into JSX components and possibly adjusting your CSS (you might choose to use CSS modules or styled-components at this point for scoping styles to components). Ensure that the app can route between pages (using React Router, for instance, to navigate from the home page to a detail page component). This task will solidify understanding of component-based development and one of the most popular front-end frameworks.

6. **Dynamic Data with Mock APIs:** Now integrate your front-end with dynamic data. Create a **mock API** to simulate back-end data for Motelo if your real back-end isn’t ready yet. This could be as simple as a JSON file or using a tool like json-server to serve a fake REST API. Include sample data such as a list of listing objects (each with id, title, location, price, image URL, etc.) and perhaps a user list for login. In your front-end code, replace hard-coded content with data fetched from this API. For example, on the Home page, use fetch(‘/api/listings’) to get the listings JSON and then set the state in React (or update the DOM in vanilla JS) to render the listings dynamically. Also handle loading states (show a “Loading…” text or spinner while the data is being fetched) and error states (alert or message if the API call fails). If the user performs an action like submitting the registration form or adding a new listing (in later milestones), simulate that with a POST request to the mock API and show the updated list or a success message. By the end of this task, your Motelo front-end should be largely functional with dynamic data, ready to hook up to the real back-end. Commit your work, noting that the front-end is now interactive and data-driven.

## **Milestone 4: Database Design & SQL**

### **Knowledge Checklist:**

* Understand fundamental SQL syntax and commands. Be able to classify SQL statements into **DDL** (Data Definition Language – e.g. CREATE TABLE, ALTER TABLE, DROP TABLE), **DML** (Data Manipulation Language – e.g. INSERT, UPDATE, DELETE records), and **DQL** (Data Query Language – essentially SELECT queries). Know the basic rules of SQL syntax (capitalization of keywords, quoting identifiers, the importance of proper query termination with semicolons, etc.). Practice writing simple queries: creating a table, inserting some rows, updating data, deleting data, and selecting data with conditions.

* Learn relational database design principles and apply them to the Motelo project. Identify the key **entities** for a housing platform and their relationships. For example, a **User** entity (with attributes like user\_id, name, email, password\_hash), a **Listing** entity (listing\_id, title, description, price, location, owner\_id as a foreign key referencing a User who is the landlord), maybe an **Application/Booking** entity if students can apply to a listing, and possibly others like **Comment** or **Favorite** if those features exist. Understand one-to-one, one-to-many, and many-to-many relationships (e.g., one user can have many listings \= one-to-many; if favorites exist, one user can favorite many listings and one listing can be favorited by many users \= many-to-many through a join table). Design the schema with appropriate **constraints**: primary keys for each table, foreign keys to enforce relationships, and field constraints such as NOT NULL (e.g., a listing must have a title and price), UNIQUE (e.g., emails should be unique in the Users table), DEFAULT values, and CHECK constraints (e.g., ensure a rent price is non-negative). Apply normalization principles (1st, 2nd, 3rd normal forms) to eliminate redundant data – for instance, if an address is stored, you might break it into separate fields (street, city, etc.) or separate tables if needed to avoid duplication. Sketch an **Entity-Relationship Diagram (ERD)** to visualize the tables and relationships for Motelo.

* Be able to write queries that retrieve data from multiple tables using **JOINs**. Practice with different types of joins: **INNER JOIN** (only matching records in both tables), **LEFT JOIN** (all records from the left table and matching ones from the right), **RIGHT JOIN** (vice versa) and know that FULL OUTER JOIN (all records from both sides) exists if supported. Use table aliases for readability. For example, write a query to get all listings with the landlord’s name by joining Listings and Users on owner\_id. Also practice writing **subqueries**: e.g., a subquery in the WHERE clause to filter results (perhaps “find listings where the owner’s registration date is within the last year” using a subquery on the Users table), or in the SELECT clause (like selecting a listing and also the count of how many users have favorited it, using a subquery). Understand which scenarios call for subqueries versus joins.

* Use advanced SQL functions to aggregate and transform data. Learn aggregate functions like **COUNT**, **SUM**, **AVG**, **MIN**, **MAX** and how to group data using **GROUP BY** and filter groups with **HAVING**. For instance, get the average rental price grouped by city or count the number of listings per landlord. Study some common **string functions** (like CONCAT to concatenate text, LOWER/UPPER to change case, SUBSTRING to extract part of a string) as you might need to format addresses or names. Get familiar with **date/time functions** relevant to your SQL dialect (e.g., NOW() for current timestamp, or functions to format dates, calculate intervals, etc.) – if Motelo stores listing post dates, you might query listings posted in the last 30 days using date functions. Also, learn to use conditional expressions in SQL such as CASE WHEN to derive new values (for example, you could classify prices into ranges or label a listing as “recent” if it’s less than a week old).

* Understand basic performance considerations and how indexes work in a database. Learn what an **index** is (a data structure that improves lookup speed on a column at the cost of extra storage and slower writes). Know when to use an index – e.g., on columns that are frequently searched or used in JOIN conditions, such as the location of a listing or foreign key columns. Discuss the difference between a single-column index and a composite index (index on multiple columns), and how each can be utilized. Practice reading a query execution plan (using EXPLAIN in MySQL/PostgreSQL or equivalent) to see if your queries are using indexes and to identify bottlenecks. Understand why selecting all columns with SELECT \* can be inefficient, especially if not all data is needed – prefer selecting only the columns you need to reduce I/O and improve performance.

* Learn about transactions and database-level routines for maintaining data integrity. Understand what a **transaction** is: a sequence of database operations that should either fully succeed or fully fail (to keep data consistent). Learn the commands to control transactions (START TRANSACTION, COMMIT, ROLLBACK) and the concept of **ACID** properties (Atomicity, Consistency, Isolation, Durability) that guarantee reliability of transactions. If your project requirements include multi-step operations (for example, if implementing a booking where creating a booking record and updating a listing’s availability must occur together), see how wrapping these in a transaction ensures one step won’t commit without the other. Also, explore creating **stored procedures** and **user-defined functions** in SQL for common tasks or complex operations (for instance, a stored procedure to mark a room as rented and create a booking in one go). While the Motelo application logic can also be in code, understanding how to do some logic in the database is valuable. Additionally, consider how to handle errors in SQL routines and when it might be better to implement logic in the application layer vs the database.

### **Project Tasks:**

1. **Design the Schema:** Based on the features of the Motelo platform, design the relational database schema. List out all the tables you think you need and their columns. For example, likely tables include **Users**, **Listings**, and possibly **Favorites** or **Bookings**, etc. Determine the relationships: e.g., **Users** to **Listings** is one-to-many (a user/landlord can post many listings), a **Favorites** table would link users and listings in a many-to-many relationship (with fields for user\_id, listing\_id), etc. Draw an ER diagram on paper or using a tool to visualize this design. Identify primary keys (use an id auto-increment or UUID for each table’s PK) and foreign keys (e.g., Listings.user\_id as FK referencing Users.id). Review the design for normalization – ensure each piece of data is stored in the appropriate table without unnecessary redundancy.

2. **Create Database and Tables:** Using a SQL database system (such as MySQL, PostgreSQL, etc.), write the SQL DDL statements to create the Motelo database and each table according to your design. Include all relevant constraints: PRIMARY KEY definitions, FOREIGN KEY constraints with proper ON DELETE/ON UPDATE rules (e.g., if a user is deleted, maybe their listings are either deleted or set to null owner depending on requirements), NOT NULL on required fields, UNIQUE constraints on fields like email or username in Users, CHECK constraints for any business rules (for example, CHECK that rent\_price \>= 0, or that dates make sense if you have date fields). Execute these statements to actually create the schema in a development database. If you’re using an ORM in your project, you could alternatively define the models and let the ORM generate the schema, but writing raw SQL is a valuable learning exercise.

3. **Insert Sample Data:** Populate the tables with some sample records to test your schema. Write SQL INSERT statements for each table. For Users, add a few sample users (some acting as landlords with listings, others as students). For Listings, insert several listings with realistic data (address, price, description, and assign an owner\_id from the Users table). If you have join tables like Favorites or Bookings, insert some entries to simulate a user favoriting a listing or booking it. Ensure that the foreign keys in these tables correctly reference existing IDs from Users/Listings. This sample data will help you validate queries and the overall design.

4. **Basic Queries:** Practice retrieving data with SELECT queries. For example: *Query all listings* – get all columns from the Listings table to see the data. *Filter queries* – find listings in a specific location (e.g., WHERE city \= ‘Hanoi’) or below a certain price (WHERE price \< 500). *Sort results* – maybe order listings by price or date added (ORDER BY price DESC). *Limit results* – if you have many listings, practice using LIMIT (or the equivalent in your SQL dialect) to paginate results (e.g., get the first 5 listings). Try out a search query that a user might do: e.g., find all listings that match a keyword in the title or description (using a WHERE description LIKE ‘%campus%’). These queries will form the basis of what your application needs to do when implementing search and filter features.

5. **Join Queries:** Using the sample data, perform join queries to combine information from multiple tables. For example, list all listings along with the landlord’s name: this would be an INNER JOIN between Listings and Users on the owner/landlord id. Try a LEFT JOIN scenario: list all users and any listings they have (users with no listings should still appear, possibly with listing fields as NULL). If you created a Favorites table, get a list of favorited listings for a particular user by joining through the Favorites table. Experiment with a query that involves three tables (perhaps Users \-\> Listings \-\> Favorites to see which students favorited which listings and include the listing details). If applicable, use a subquery: for instance, find all users who have not posted any listing (one approach: a subquery to select user IDs from Listings, then in the main query select from Users where user\_id NOT IN that subquery). These exercises ensure you can form complex queries that the application’s back-end might require.

6. **Aggregation and Analysis:** Write queries using aggregation to derive insights. For example, find the **average rent price** of all listings, and then perhaps average per city or per type of accommodation if those exist (using GROUP BY city or GROUP BY type). Count how many listings each landlord has posted (SELECT owner\_id, COUNT(\*) FROM Listings GROUP BY owner\_id) – then maybe join that result with Users to see the actual names of landlords and their listing counts. If you have a Favorites or Bookings table, count how many favorites each listing has, or how many bookings each user has made. Use HAVING to filter groups (like “show only landlords who have posted more than 3 listings”). Also test out a CASE expression: for example, select each listing and add a computed column that labels it “Expensive” if price \> some threshold, “Affordable” otherwise (CASE WHEN price \> 1000 THEN ‘Expensive’ ELSE ‘Affordable’ END AS price\_category).

7. **Index and Optimize:** If you notice that some of your queries (especially those filtering by text fields like city or doing joins on foreign keys) are slow on larger data sets, create indexes to improve them. For instance, create an index on the Listings.city column if you frequently query by city, or on Listings.owner\_id since you often join by that. Use EXPLAIN on a complex SELECT (like a join with a subquery or an aggregate) to see the query plan and verify that indexes are being utilized. While your dataset is small now, this is a good simulation for production where data will be larger. Understand the impact: try querying a large dataset (you can script-insert many rows or use a loop in SQL to add, say, 10,000 listings) and compare a query’s speed with and without an index. This will teach you the practical importance of indexing and the need to selectively add indexes for performance.

8. **Transactions and Procedures (Advanced):** To round out your database skills, implement a sample transaction. For example, if you had a Booking process: in a single transaction, you would insert a new row into a Bookings table and update the corresponding listing’s status to “booked”. Write a transaction script that does two actions and roll it back deliberately to ensure it undoes both if one fails (simulate a failure by perhaps violating a constraint in one of the statements). Additionally, try creating a simple stored procedure, for example a procedure sp\_add\_listing(userId, details…) that inserts a new listing for a user and automatically logs an activity or returns the new ID – something that encapsulates logic in the database. This is optional for the project (as much of this logic can be handled by the back-end code), but it’s an excellent learning step to see how business logic can also reside in the database if needed.

## **Milestone 5: Back-end Development**

### **Knowledge Checklist:**

* Understand the typical structure of a back-end application and the responsibilities of each module/component. In a well-organized project, the **Controller** layer handles incoming HTTP requests and sends back responses (often calling services and then formatting JSON or HTML outputs). The **Service** layer contains the business logic – it processes data, applies rules, and coordinates between controller and data layers. The **Model** or Data Access layer manages interaction with the database, often using an **ORM** (Object-Relational Mapping) library or direct queries; this could include defining models or entities that map to database tables (e.g., a Listing model class corresponding to the Listings table) and methods to query or update the data. Also understand what **Middleware** is: reusable functions that run during the request-response cycle, often used for cross-cutting concerns like logging, authentication, or error handling. Be familiar with the overall request lifecycle in your chosen framework (e.g., how an HTTP request flows through middleware, hits the appropriate controller/route, calls service logic, interacts with the database, and returns a response). Finally, know the purpose of API documentation tools like **Swagger/OpenAPI** – these allow you to describe your REST endpoints, request/response formats, and can even generate interactive docs or client code from your specification, which is very useful in a team setting.

* Learn how to implement **authentication and authorization** in the back-end. Authentication is verifying user identity (e.g., checking username/password and establishing who the user is), whereas authorization is checking permissions (e.g., whether a logged-in user is allowed to perform an action). Understand the workflow of a login system: a user submits credentials, the server verifies them (perhaps by checking a hashed password in the database), and if valid, issues a token or session. Focus on **JWT (JSON Web Token)** if stateless auth is used: know that a JWT is a signed token encoding a payload (often user id and roles) that the client stores and sends with each request (usually in the Authorization header). The server can verify the token signature to authenticate the user without a database lookup on each request. Know that JWTs have expirations and should be stored securely on the client (e.g., in HTTP-only cookies or secure storage) to prevent theft. Also, learn about **password hashing** (using bcrypt or similar algorithms) – never store plain passwords; instead, store only salted hashes so that even if the database is compromised, passwords aren’t in clear text. For authorization, understand how to implement **role-based access control**: e.g., define roles like Admin, Landlord, Student and restrict certain API endpoints or actions based on role. In practice, this might involve checking the user’s role from the JWT or database before allowing the action (for example, only an Admin can delete any listing, but a Landlord can delete their own listing, and a Student cannot delete listings at all). Middleware is commonly used here: e.g., an auth middleware to verify the JWT and set the user info in the request, and an authorization middleware or simple checks in handlers to enforce permissions.

* Learn to make your API robust with proper **error handling and validation**. Understand how to structure your code so that errors (like an invalid request or an exception thrown in the logic) are caught and turned into meaningful HTTP responses rather than crashing the server. Many frameworks support a global error handling middleware or mechanism – use that to catch unhandled exceptions and return a JSON with an error message and appropriate status code (500 for unexpected errors, 404 for not found, 400 for bad requests, etc.). Also implement **validation** for incoming data: for instance, when a client posts a new listing, ensure required fields are present and of the correct type (e.g., price is a number, email is properly formatted). You can use libraries or manual checks to validate request bodies and query parameters. Send back clear error messages for validation failures (e.g., “price must be a positive number”). Consistently use proper HTTP status codes: 200-level for success, 400-level for client errors like validation issues or unauthorized access, 500-level for server errors. This improves the API’s usability. Additionally, understand how to handle **file uploads and static files** if the project requires it. In Motelo’s context, this could mean allowing users to upload images of a property. Know how to accept a file via an HTTP request (multipart/form-data), how to store it (either on the file system, in a database as a blob, or on a cloud storage service), and then how to serve it back to users (either by providing a URL to the file or a dedicated endpoint to download it). Also, be cautious with security when serving static files or uploads (for example, only serve specific directories, validate file types, etc.). Many frameworks have built-in support or middleware for static file serving and upload handling.

### **Project Tasks:**

1. **Back-end Framework Setup:** Initialize the back-end application using a suitable framework for the chosen language (e.g., **Express** for Node.js, **Spring Boot** for Java, or Django for Python, etc., depending on your stack). Organize the project structure into the layers: create directories for **controllers** (or routes), **services**, **models** (or database entities), and **middleware**. For example, in an Express app, you might have a routes/ folder for route handlers (controllers), a services/ folder for business logic, a models/ folder for Mongoose/Sequelize models or raw SQL queries, and a middleware/ folder for any middleware functions (like auth checking). Set up a basic routing system – e.g., a controller for listings (listingController.js or ListingController.java) with a couple of stub endpoints, and likewise one for users. Ensure the server can still start and respond (perhaps test your health-check endpoint from Milestone 2 after reorganizing). Commit this baseline back-end structure.

2. **Connect to the Database:** Integrate the database designed in Milestone 4 with your back-end. This might involve setting up a database connection (for example, configuring a connection string to your MySQL/Postgres database in a config file or environment variable). If using an ORM, define model classes or schemas for each table (e.g., a User model class with fields id, name, email, etc., a Listing model class, etc.) and use the ORM to handle migrations or ensure the schema matches. If not using an ORM, prepare SQL queries or use a query builder to perform operations. As a test, implement a simple data access function – for instance, fetch all listings from the database. You could create a service function like listAllListings() that queries the Listings table and returns the data. Hook this up to a controller endpoint (GET /api/listings) to return the data as JSON. Start the server and verify that hitting this endpoint returns actual data from your database (the sample data you inserted previously). This confirms your back-end can talk to the database.

3. **Implement Core API Endpoints:** Develop the key functionalities of the Motelo platform on the back-end by creating RESTful endpoints: \- **Listings API:** Create endpoints for listing resources, e.g. \- GET /api/listings – returns a list of all housing listings (with filtering or pagination support if possible). \- GET /api/listings/{id} – returns details for a specific listing by ID (including information like description, price, owner info, etc., possibly by joining with Users). \- POST /api/listings – allows a landlord to create a new listing (requires authentication). The endpoint should read listing details from the request body, validate them, save a new record to the database, and return the created listing (or an ID). \- PUT/PATCH /api/listings/{id} – allows updating a listing’s details (e.g., if the landlord edits the price or description). Validate fields and ensure the requesting user is authorized to edit (the owner or an admin). \- DELETE /api/listings/{id} – deletes a listing (only allowed for the owner or an admin). Implement these one by one, starting with GET (read-only operations) then moving to write operations. Use the service layer for logic (e.g., a ListingService that has methods like getAllListings(), createListing(data, user), etc.). This separation will make it easier to add things like caching or complex business rules later if needed. \- **User API:** Create endpoints for user actions, e.g. \- POST /api/register – to create a new user account (student or landlord). This should hash the password before saving the user to the database, and then return a success message or user profile (but never the raw password). \- POST /api/login – to authenticate a user. Verify the provided credentials (email/username and password) against the database. If valid, create a JWT (with user id and role in the payload) and send it back (in the response body or as a cookie). If invalid, return a 401 Unauthorized with an error message. \- GET /api/users/{id} – (optional) to retrieve user profile info. This could be restricted to authenticated users (either the user themselves or admin). \- Perhaps endpoints for user-specific actions like viewing their own listings or favorites if those features exist (e.g., GET /api/users/{id}/favorites). \- **Other Features:** If you have a Favorites or Booking system, implement those endpoints similarly. For example, POST /api/listings/{id}/favorite for a student to favorite a listing (which would create a record in the Favorites table), or POST /api/listings/{id}/book for a booking request. Also consider an endpoint for comments if needed (e.g., POST /api/listings/{id}/comments). As you implement each endpoint, test it using Postman or curl and ensure the correct data is being returned/modified in the database. Commit the code for each major feature addition.

4. **Implement Authentication & Authorization:** Protect the routes you implemented in step 3\. First, ensure your server can interpret incoming JWTs. Set up an **authentication middleware** that will run on protected routes: it should read the Authorization header (or cookie) for a token, verify the token’s signature (using the secret key you defined), and if valid, attach the decoded user information (user id, role, etc.) to the request object. If the token is missing or invalid, respond with 401 Unauthorized. Apply this middleware to routes that require login (e.g., creating or editing a listing, favoriting a listing, etc., but not to public GET listing or register/login routes). Next, implement **authorization checks**. For example, in the delete listing controller, after the auth middleware, check that request.user.id matches the listing’s owner ID or that the request.user.role is Admin – if not, return 403 Forbidden. You could also implement this as a separate middleware function that takes required roles or checks ownership for specific routes. Test these security measures: try to access protected endpoints without a token (should be blocked), with a token of a different user (should block actions like deleting someone else’s listing), and with an admin token (should allow admin-only operations). Now your API has proper security in place.

5. **Input Validation:** Go through your controllers and add validation logic to ensure the data coming from clients is correct and safe. For instance, in the register endpoint, check that email, password, and name are provided and meet basic criteria (email contains @, password length is sufficient, etc.). In the create listing endpoint, ensure required fields like title, address, price are present; price is a positive number; maybe limit string lengths for title/description to prevent excessively large inputs. You can use validation libraries (like Joi for Node.js or Hibernate Validator for Spring) or manual if-conditions. When validation fails, respond with a 400 Bad Request status and a JSON that describes the errors (e.g., {“error”: “Price must be a positive number”}). Also, handle cases like trying to update a resource that doesn’t exist – e.g., if a listing ID is not found in a PUT, return 404 Not Found. By doing this, you make the API consumer’s job easier as they get clear feedback.

6. **Error Handling:** Introduce a global error handler to catch any unhandled exceptions or rejections in your endpoints. For example, in Express you might create an error-handling middleware that takes (err, req, res, next) and in Spring Boot you might use @ControllerAdvice with exception handler methods. Make sure that if something goes wrong deep in the service (like a database error or an unexpected condition), the server doesn’t just crash or hang. Instead, catch the error and respond with a 500 Internal Server Error and a generic message (and log the details on the server console for debugging). For anticipated errors (like a lookup that found no results), you might throw a custom error that your handler knows to translate to a 404 status. Test this by, for example, trying to fetch a non-existent listing ID and see that you get a 404 with a friendly message, or by simulating an error in code to see that a 500 is returned gracefully.

7. **File Uploads (if applicable):** If part of the Motelo features includes images for listings (which is likely in a housing app), implement an endpoint for file uploads. For example, allow a landlord to upload a photo when creating a listing or via a separate endpoint like POST /api/listings/{id}/uploadImage. Use a middleware or library to handle multipart form data (such as multer in Node or Spring’s MultipartFile). When a file is received, decide where to store it – perhaps in a directory like /uploads on the server, or an AWS S3 bucket in a real scenario. Save the file path or URL in the database (maybe in a ListingImages table or a field in Listings for the image URL). Also, set up your server to serve these static files (e.g., Express static middleware pointing to the uploads folder, or in Spring, configure resource handlers). After implementing, test by uploading an image via Postman and then retrieving it via the URL your back-end provides. Ensure that only authorized users can upload (a user should only upload images for their own listing, etc.).

8. **API Documentation:** Now that your API is taking shape, document it. Use Swagger/OpenAPI to create a documentation for all endpoints. This can be done by writing an OpenAPI spec (YAML or JSON) manually or using decorators/annotations in code (depending on framework, e.g., using Swagger UI and JSDoc comments, or Springfox in Spring Boot). Document each endpoint’s method, URL, what it does, the expected request body or params, and the response format (including error responses). Host this documentation at an endpoint (often /api-docs or similar). This will be useful for front-end integration and for any future developers. As a test, open the Swagger UI in a browser and try out an endpoint (most Swagger UIs let you send test requests). This ensures your documentation is accurate and your API is usable from the documentation interface.

## **Milestone 6: DevOps & Deployment**

### **Knowledge Checklist:**

* Understand the differences between development, staging, and production **environments**. Development is your local setup where you run the app with debug mode and frequently change code. Staging (or testing) is an environment that mirrors production where you deploy for final testing (often used by QA teams or for UAT – User Acceptance Testing). Production is the live environment for end-users. Know why we separate these (to catch bugs in testing, to ensure quality before users see changes, etc.) and the importance of keeping them consistent (i.e., “it works on my machine” vs production issues). Learn how to manage configuration for different environments: for example, using **environment variables** for things like database connection strings, API keys, or secrets, rather than hardcoding them. Understand how to use a .env file for local development and how those variables might be set in a production server or CI/CD pipeline. Ensure you grasp the importance of **secret management** – never committing sensitive credentials to source code; use secure storage or environment configs instead.

* Learn the basics of **Docker and containerization**. Docker allows you to package your application and its environment into an image that can be run anywhere. Understand key terms: an **image** is a snapshot of an application (including OS layers, runtime, code, dependencies), and a **container** is a running instance of an image. Learn how to write a **Dockerfile** to containerize the Motelo application. For example, if your back-end is a Node.js app, the Dockerfile might start from a Node base image, copy your package.json and source code, install dependencies, and set the command to npm start. If it’s Java, maybe start from an OpenJDK image and copy the JAR file. Practice building the Docker image using docker build and running a container with docker run to ensure it works. Explore **multi-stage builds** in Dockerfile to reduce image size (e.g., build the artifact in one stage, then copy only the artifact into a slim runtime image). Understand how to use **Docker Compose** to define multiple services: for instance, one service for the back-end app and another for the database. Docker Compose allows you to easily start up the whole stack (database \+ server \+ maybe a front-end static server) with one command, which is great for testing the integrated app. Also, familiarize yourself with Docker concepts like volumes (to persist database data or to facilitate local development by mounting code into a container) and networking (how containers communicate, e.g., your app container connecting to the database container by a service name).

* Understand the principles of **CI/CD (Continuous Integration and Continuous Deployment)**. Continuous Integration means every code change (push or merge) triggers an automated process to build and test the application, ensuring that integration issues are caught early. Continuous Deployment extends this by automatically deploying code to an environment (staging or production) after passing tests. Learn about popular CI/CD tools and services – for instance, GitHub Actions, GitLab CI, Jenkins, Travis CI, etc. Focus on one, like GitHub Actions if your code is on GitHub. Understand how pipelines are defined (usually by a YAML file in your repo). Typical stages include build (compile code, install dependencies, run linters), test (run automated tests), and deploy (ship the code to an environment or build a docker image and push it). Learn to write a simple pipeline configuration: for example, a YAML that says “on every push to main, run these jobs”. Within the pipeline, practice running your test suite or at least building the project to catch compile errors. If your project has Docker setup, you can configure the pipeline to build your Docker image and even push it to a registry (like Docker Hub or GitHub Packages). This ensures that anyone can pull a ready-to-run image of your app.

* Explore deployment strategies and platforms. Learn the difference between a **manual deployment** (ftp/scp files to a server, or manually running git pull on a server) versus an **automated deployment** (where your CI pipeline or other tooling deploys new code as soon as it’s ready). Understand various hosting options: \- **VPS (Virtual Private Server)**: you get a server (like on DigitalOcean, AWS EC2, etc.) and you are responsible for configuring the environment (installing runtime, database, etc.) and running your app. \- **Platform as a Service**: services like **Heroku, Render, or AWS Elastic Beanstalk** where you give your code or container and they handle the infrastructure details for you. \- **Serverless / specialized hosts**: e.g., deploying front-end on **Vercel or Netlify** which are great for React apps, or using cloud functions for back-end parts. Understand how Docker plays a role in deployment: many modern deployments involve building a Docker image and either running it in a container orchestration (like Kubernetes) or a PaaS that supports Docker deploys. Know that using containers helps ensure the app runs the same everywhere (no “works on my machine” issues). Also, consider how to manage your database in deployment – often you’ll need to run **database migrations** (updates to the schema) when you deploy a new version of the app. Tools or scripts should be in place to apply these changes to the production database in a controlled way (sometimes integrated into the app startup or CI pipeline). The goal is to smoothly transition the Motelo application from a development state to a live, accessible state on the internet, with minimal manual steps.

### **Project Tasks:**

1. **Environment Configuration:** Prepare your application to run in different environments without code changes. Externalize configuration values like database connection strings, API keys, or debug flags. For example, create a .env file for local development with entries like DB\_URL=postgres://user:pass@localhost:5432/motelo\_dev and perhaps a separate .env.production with production DB credentials or other settings. In your code, use a library or framework features to load these environment variables. Verify this works by running your app with different env files or environment variable settings – for instance, simulate a production run by setting NODE\_ENV=production (for Node) or equivalent and ensure things like logging verbosity or debug options respect that. This task ensures that when you deploy, you can easily supply new config without altering the codebase (important for security and flexibility).

2. **Dockerize the Application:** Write a **Dockerfile** for the Motelo back-end (and front-end if applicable). For example, if back-end is Node.js: \- Use an official Node base image (matching your Node version). \- Set the working directory, copy package.json and run npm install to install dependencies, then copy the rest of the source code. \- Build the app (if it needs building, e.g., for a Java app you’d compile to a JAR; for Node maybe just ensure dependencies). \- Specify the command to run the app (e.g., npm start or java \-jar app.jar). If using multi-stage, you might have one stage to build (especially for a compiled language or to run tests) and a second stage for running (with only the necessary runtime and compiled code). Next, create a **docker-compose.yml** file that defines your services: one for the motelo-backend (using the Dockerfile you wrote) and one for the database (use an official MySQL/Postgres image, and set environment variables in compose for DB name, user, password). Possibly add a service for the front-end (if you containerize a React build or use Nginx to serve static files). Test this by running docker-compose up. It should bring up the database and then the back-end, and the back-end should be able to connect to the database using the host name given in compose (e.g., the service name like db if you named it that). You might need to wait for DB to initialize; consider using depends\_on in Compose and maybe a small wait script. Once both are running, test the API (from your host machine, hitting [http://localhost:PORT/api/listings](http://localhost:PORT/api/listings) for example) to ensure the integrated app works inside containers. This step is complete when you have a working Docker image for the app and can run the whole stack with one command locally. Commit your Dockerfile and docker-compose files to the repo.

3. **CI Pipeline Setup:** Add a Continuous Integration workflow to your repository. For instance, if using GitHub, create a .github/workflows/ci.yml file. In it, define triggers (e.g., on push or pull request to main branch). Add jobs such as: \- **Setup job**: choose a runner environment (like ubuntu-latest), checkout the code, set up any necessary languages/runtimes (for example, actions/setup-node or actions/setup-java). \- **Install & Test job**: install dependencies and run your test suite. If you have unit tests for back-end or front-end, this is where they run. At minimum, run a build or lint to catch syntax errors. For a Node project, you might run npm ci and then npm run build and npm test. For a Java project, run mvn package and perhaps execute JUnit tests. \- **Docker Build job**: If tests pass, have a job to build the Docker image. Use Docker commands or a Docker build action to build the image from your Dockerfile. Optionally, log in to a Docker registry (like Docker Hub) and push the image with a tag (maybe tag it motelo:latest and also with the commit or version number). Ensure the pipeline is configured to run on each commit. Push a dummy change to trigger the pipeline and monitor its execution in the CI system. Adjust any issues (like missing dependencies or failing tests) until the pipeline runs successfully. This automated build/test gives confidence that your codebase is always in a runnable state after changes.

4. **Continuous Deployment (CD) & Releasing:** Extend the CI pipeline or create a separate CD pipeline to handle deployment of the Motelo app. Decide where to deploy: \- If using a service like **Heroku**: You can configure the pipeline to deploy to Heroku either by pushing the Docker image or using the Heroku CLI to push code. Heroku might also detect your repository and auto-deploy if connected. \- If using a **VPS**: you might set up SSH and use scp or an automation tool to pull the new Docker image to the server and run containers. Or use a simple script that the pipeline triggers on the server. \- If using **Docker Hub/Kubernetes**: maybe pushing to Docker Hub and having a Kubernetes cluster pull the new image (more advanced). For learning, a straightforward path is deploying the Docker container to a cloud service. For example, you could use **Render.com or DigitalOcean** which can directly deploy from a Dockerfile or docker-compose. Alternatively, deploy the front-end separately on a static host (Netlify/Vercel for React app) and the back-end on Heroku or a VPS. Document the deployment steps: likely, you’ll need to set environment variables on the server (like database URL, any API keys). Also, ensure your database is accessible in production – if using a hosted DB, get its URL; if running your own DB container on a VPS, you may need to set up volumes for persistence and expose it properly. Execute the deployment: for example, if using Heroku, login and create an app, then use git push heroku main or configure GitHub Actions with a Heroku API key to auto-deploy on push. If using Docker on a VPS, build or pull the latest image and run docker-compose up \-d on the server. Once deployed, your Motelo application should be live at a URL (from Heroku or the IP/domain of your server). Visit the front-end and exercise the main features, which should be communicating with the live back-end and database.

5. **Database Migration on Deployment:** When deploying a new version, if there are changes to the database schema (from development to production), manage them carefully. Implement a migration strategy: for example, use a tool like Flyway or Liquibase for Java, or a Node migration library (like Knex migrations or Sequelize CLI) to apply schema changes. Include migration scripts in your source control. When your CI/CD deploys a new version, ensure it runs the migration steps against the production database before starting the new app. This could be a step in the pipeline or an automated check in the app startup (some ORMs can auto-migrate, though caution is advised). Test this process: if you add a new column in development and release, verify that the deployment adds that column in production without losing data. This knowledge of safe schema migration is crucial for real-world projects.

6. **Final Testing & Monitoring:** After deployment, do a thorough test of the entire Motelo platform as a user would in production. Test user registration, listing creation, searching, etc., to ensure every integrated part (front-end, back-end, database, file serving) works outside of your local environment. Set up basic monitoring or logging to capture issues in production – for instance, enable logging of errors to a file or use a service like Sentry for error tracking. While this goes beyond the development phase, it’s part of DevOps to ensure you can maintain the application after deployment. If any bug or issue appears, create a new task, fix it in code, and go through the CI/CD process to deploy the fix, illustrating the full cycle of continuous improvement.