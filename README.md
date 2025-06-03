# React project

## Vite

Vite is a modern build tool that provides a fast development experience for web applications. It uses native ES modules in the browser during development, which allows for instant module reloading and a snappy development experience

## How to Create a Vite Project

To create a new React project using Vite, you can use the following command:

```bash
npm create vite@latest
```
after that you will be prompted to **enter the project name** and **select a template**. For a React project, you can choose the `react` template and choose `javascript`.

```bash
cd my-react-app
npm install
npm run dev
```

This command initializes a new Vite project with the React template. The `my-react-app` is the name of the project directory that will be created.
After running the command, you will have a basic React project structure set up with Vite as the build tool.

## Project Structure

The project structure of a Vite React application typically looks like this:

```
my-react-app/
├── node_modules/
├── public/
├── src/
│   ├── assets/
│   ├── App.jsx
│   ├── App.css
│   ├── main.jsx
│   ├── index.css
│   └── index.css
├── .gitignore
├── index.html
├── package.json
├── README.md
└── vite.config.js
```

### Explanation of the Project Structure

- **node_modules/**: Contains all the dependencies installed via npm.
- **public/**: Contains static assets that will be served directly, such as images and icons.
- **src/**: Contains the source code of the application.
  - **assets/**: A folder for static assets like images and fonts.
  - **App.jsx**: The main React component of the application.
  - **App.css**: Styles for the `App` component.
  - **main.jsx**: The entry point of the React application, where the React app is rendered into the DOM.
  - **index.css**: Global styles for the application.
- **.gitignore**: Specifies files and directories that should be ignored by Git.
- **index.html**: The main HTML file that serves as the entry point for the application.
- **package.json**: Contains metadata about the project, including dependencies and scripts.
- **README.md**: A markdown file that provides information about the project.
- **vite.config.js**: Configuration file for Vite, where you can customize the build process and development server settings.

## Vite Configuration

The `vite.config.js` file is where you configure Vite for your project. It allows you to customize the build process, set up plugins, and define other settings.

```javascript
import { defineConfig } from 'vite'
import react from '@vitejs/plugin-react'

// https://vite.dev/config/
export default defineConfig({
  plugins: [react()],
})
```

## `package.json`
The `package.json` file is a JSON file that contains metadata about the project, including its dependencies, scripts, and other configurations. It typically includes fields such as `name`, `version`, **`dependencies`**, **`scripts`**, `devdependencies`.

> The `package.json` file is a crucial part of any Node.js project, including React applications. It contains metadata about the project and its dependencies.

```json
{
  "name": "my-react-app",
  "private": true,
  "version": "0.0.0",
  "type": "module",
  "scripts": {
    "dev": "vite",
    "build": "vite build",
    "lint": "eslint .",
    "preview": "vite preview"
  },
  "dependencies": {
    "react": "^19.1.0",
    "react-dom": "^19.1.0"
  },
  "devDependencies": {
    "@eslint/js": "^9.25.0",
    "@types/react": "^19.1.2",
    "@types/react-dom": "^19.1.2",
    "@vitejs/plugin-react": "^4.4.1",
    "eslint": "^9.25.0",
    "eslint-plugin-react-hooks": "^5.2.0",
    "eslint-plugin-react-refresh": "^0.4.19",
    "globals": "^16.0.0",
    "vite": "^6.3.5"
  }
}

```

**react** and **react-dom** are two major liabaries.

## Scripts in package.json

The `scripts` section of the `package.json` file allows you to define command line scripts that can be run using npm. Here are the scripts defined in the example:

- **`dev`**: Runs the development server using Vite.
- **`build`**: Compiles the application for production.

These scripts streamline the development process by providing easy commands to manage your application.

when we run `npm run build` command it generates a **_dist_** folder which contains the production-ready files of the application. This folder can be deployed to a web server.

it converts JSX and ES6+ code into browser-compatible JavaScript, optimizes assets, and prepares the application for deployment.

## dependencies in package.json

The `dependencies` section lists the packages that your application needs to run. In the example, it includes:

- **`react`**: The core React library for building user interfaces.
- **`react-dom`**: The package that provides DOM-specific methods for React, allowing you to render React components into the DOM.

## devDependencies in package.json

The `devDependencies` section lists packages that are only needed during development and testing. In the example, it includes:

- **@eslint/js**: ESLint configuration for JavaScript.
- **@types/react**: TypeScript type definitions for React.
- **@types/react-dom**: TypeScript type definitions for React DOM.
- **@vitejs/plugin-react**: Vite plugin for React, enabling features like fast refresh and JSX support.
- **eslint**: A tool for identifying and fixing problems in JavaScript code.
- **eslint-plugin-react-hooks**: ESLint plugin for enforcing React Hooks rules.
- **eslint-plugin-react-refresh**: ESLint plugin for React Fast Refresh.
- **globals**: Provides global variables for various environments.

## index.html

The `index.html` file is the main HTML file that serves as the entry point for the application. It typically includes a root `<div>` where the React application will be rendered, and it may also include links to stylesheets and scripts.

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>My React App</title>
  <link rel="stylesheet" href="/src/index.css">
</head>
<body>
  <div id="root"></div>
  <script type="module" src="/src/main.jsx"></script>
</body>
</html>
```
The `<div id="root"></div>` is where the React application will be mounted. The `<script type="module" src="/src/main.jsx"></script>` line includes the main JavaScript file that initializes the React application.

### Why module is used in script tag?
> The `type="module"` attribute in the `<script>` tag indicates that the script should be treated as a JavaScript module. This allows you to use modern JavaScript features like `import` and `export` within the script, enabling better modularity and code organization. It also allows for asynchronous loading of the script, improving performance in web applications.

## main.jsx

The `main.jsx` file is the entry point of the React application. It typically imports the main `App` component and renders it into the DOM.

```javascript
import { StrictMode } from 'react'
import { createRoot } from 'react-dom/client'
// import './index.css'
import App from './App.jsx'

createRoot(document.getElementById('root')).render(
  <StrictMode>
    <App />
  </StrictMode>,
)

```

### Explanation of main.jsx
This code does the following:

1. **Imports**:
   - `StrictMode`: A tool for highlighting potential problems in an application.
   - `createRoot`: A method from `react-dom/client` to create a root for rendering React components.
   - `App`: The main application component. it is called like a function to render the main component of the application.
   
2. **Renders the App Component**:
    - It uses `createRoot` to create a root element in the DOM with the ID `root`.
    - The `App` component is rendered inside a `StrictMode` wrapper, which helps identify potential issues in the application.

### 📝 Note on StrictMode
`StrictMode` is a tool for highlighting potential problems in an application. It activates additional checks and warnings for its descendants, helping developers identify issues early in the development process.

---

### 📌 Where It's Used

In a typical React project:

* `React` is for creating components.
* `ReactDOM` is for rendering those components into the HTML.


## App.jsx

The `App.jsx` file is the main component of the React application. It typically contains the main layout and structure of the application.

```javascript
import { useState } from 'react'
// import './App.css'

function App() {
  return (
    <>
      <h1>hello!</h1>
    </>
  )
}

export default App

// or

// export default function App() {
//   return (
//     <>
//       <h1>hello!</h1>
//     </>
//   )
// }

// or

// export default function App() {
//   let htmlCotent = <>
//     <h1>hello!</h1>
//   </>
//   return (htmlCotent);
// }

```

### Explanation of App.jsx

This code does the following:
1. **Imports**:
   - `useState`: A React hook for managing state in functional components.
   - The `App.css` file is commented out, but it can be used to style the component.
2. **Defines the App Component**:
    - The `App` function is defined as a functional component.
    - It is returning a fragment (`<>...</>`) containing a simple `<h1>` element with the text "hello!".
    - Simply we can say that App.jsx is functional component that returns a simple JSX element.
3. **Exports the App Component**:
    - The `App` component is exported as the default export of the module, making it available for import in other files.

> Keep in mind that the name `App` and name of the file `App.jsx` should be capitalized, as it is a convention in React to name components with a capital letter.

## App.css

The `App.css` file contains styles for the `App` component. It typically includes styles for layout, colors, fonts, and other visual aspects of the application.

```css
.App {
  text-align: center;
  color: red;
}

/* It typically includes styles for layout, colors, fonts, and other visual aspects of the application. */
```
This code styles the `App` component, giving it a centered layout, a dark background for the header, and some padding for the main content.

## index.css

The `index.css` file contains global styles for the application. It typically includes styles that apply to the entire application, such as body styles, font settings, and reset styles.

```css
body {
  margin: 0;
  font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, 'Helvetica Neue', Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
* {
  box-sizing: border-box;
}
/* Reset styles for all elements */
```
This code sets the default styles for the body, including margin, font family, and font smoothing. It also applies a box-sizing rule to all elements to ensure consistent sizing behavior.
## Running the Application
To run the Vite React application, you can use the following command:

```bash
npm run dev
```
This command starts the development server, and you can access the application in your web browser at `http://localhost:5173` (or the port specified in the terminal).
## Building the Application
To build the Vite React application for production, you can use the following command:

```bash
npm run build
```
This command compiles the application into optimized static files that can be deployed to a web server. The output will be placed in the `dist` directory, which you can then serve using a static file server or deploy to a hosting service.
## Previewing the Built Application
To preview the built application, you can use the following command:

```bash
npm run preview
```
This command starts a local server to serve the built application from the `dist` directory. You can access the preview in your web browser at `http://localhost:4173` (or the port specified in the terminal).
## Conclusion
Vite is a powerful build tool that provides a fast and efficient development experience for React applications. By using Vite, you can take advantage of features like instant module reloading, optimized builds, and a simple configuration process. The project structure and configuration files make it easy to get started with building modern web applications using React and Vite.
## Additional Resources
- [Vite Documentation](https://vitejs.dev/guide/)
- [React Documentation](https://reactjs.org/docs/getting-started.html)

