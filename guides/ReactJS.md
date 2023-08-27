# React.js Coding Guidelines and Style Guide

## Table of Contents

1. [Introduction](#1.-introduction)
2. [Project Structure](#2.-project-structure)
3. [Components](#3.-components)
4. [Pages](#4.-pages)
5. [State Management](#5.-state-management)
6. [Props](#6.-props)
7. [Hooks](#7.-hooks)
8. [Styling](#8.-styling)
9. [Conditional Rendering](#9.-conditional-rendering)
10. [Event Handling](#10.-event-handling)
11. [Performance](#11.-performance)
12. [Testing](#12.-testing)
13. [Package Management](#13.-package-management)
14. [Adding License and Copyright Notice](#14.-adding-license-and-copyright-notice)
15. [Conclusion](#15.-conclusion)

## 1. Introduction

Welcome to the React.js Coding Guidelines and Style Guide for Devspace IIT(ISM) Dhanbad. This comprehensive guide is designed to provide best practices and recommendations for developing web applications using the React.js library. Whether you're a beginner or an experienced developer, adhering to these guidelines will help you create clean, reusable, and performant UI components.

## 2. Project Structure

To maintain a scalable and organized React.js project, we suggest the following structure:

```bash
project-root/
  ├── src/
  │    ├── assets/
  │    ├── components/
  │    ├── containers/
  │    ├── pages/
  │    ├── services/
  │    ├── state/
  │    │    ├── context/
  │    │    └── reducers/  (if using Redux)
  │    ├── utils/
  │    ├── App.js
  │    └── index.js
  ├── public/
  ├── package.json
  ├── .gitignore
  └── README.md
```

- **Components**: This directory contains small, reusable UI components. Each component should focus on a single responsibility and be self-contained.

- **Containers**: Containers are components that handle the logic and state management for a group of related components. They connect to services, fetch data, and pass it down to child components.

Containers are responsible for:

- Managing state and business logic.
- Interacting with services to fetch data.
- Passing data and behavior down to child components.

```javascript
// containers/UserContainer.js
import React, { useState, useEffect } from "react";
import { getUserData } from "../services/userService";
import UserInfo from "../components/UserInfo";

function UserContainer() {
  const [userData, setUserData] = useState([]);

  useEffect(() => {
    async function fetchData() {
      const data = await getUserData();
      setUserData(data);
    }
    fetchData();
  }, []);

  return <UserInfo userData={userData} />;
}
```

- **Services**: Services handle data fetching, interaction with APIs, and business logic. They are separate from components and containers to ensure separation of concerns.

```javascript
// services/userService.js
export async function getUserData() {
  const response = await fetch("/api/users");
  const data = await response.json();
  return data;
}
```

## 3. Components

- Break down UI into small, reusable components.
- Use meaningful and descriptive names for components.
- **Follow the Single Responsibility Principle**: each component should do one thing.

```javascript
// components/Header.js
import React from "react";

function Header() {
  return <header>...</header>;
}
```

## 4. Pages

- Organize your application into pages corresponding to distinct views or routes.
- Each page may consist of multiple components and containers.
- Pages help separate concerns and maintain codebase organization.

```javascript
// pages/HomePage.js
import React from "react";
import Header from "../components/Header";
import ProductListContainer from "../containers/ProductListContainer";

function HomePage() {
  return (
    <div>
      <Header />
      <ProductListContainer />
    </div>
  );
}
```

## 5. State Management

- Use state management libraries like Redux or Context API for complex applications, based on the requirements.
- For simpler cases, use React's built-in state with the `useState` hook.

## 6. Props

- Pass data and behavior to child components using props.
- Destructure props in function components for cleaner code.

```javascript
function UserInfo({ name, email }) {
  return (
    <div>
      {name} - {email}
    </div>
  );
}
```

## 7. Hooks

- Use React hooks like `useState`, `useEffect`, `useContext`, etc., for managing state and side effects.
- Follow hook naming conventions and guidelines for custom hooks.

## 8. Styling

- Use CSS Modules for component-level styling. This approach encapsulates styles within components.

```bash
Button/
  ├── Button.js
  └── Button.module.css
```

```javascript
import React from "react";
import styles from "./Button.module.css";

function Button() {
  return <button className={styles.button}>Click me</button>;
}
```

## 9. Conditional Rendering

- Use conditional rendering to show or hide components based on conditions.
- Use ternary operators or `&&` for simple cases and `if` statements for complex conditions.

```javascript
function WelcomeMessage({ user }) {
  return user ? <div>Welcome, {user.name}!</div> : null;
}
```

## 10. Event Handling

- Use arrow functions or function binding to handle events.
- Pass event handlers as props to child components.

```javascript
function Button({ onClick }) {
  return <button onClick={onClick}>Click me</button>;
}
```

## 11. Performance

- Optimize rendering using `React.memo` for functional components.
- Use the `key` prop to help React efficiently update the component tree.

## 12. Testing

- Write unit tests for components, ensuring they render and behave as expected.
- Use testing libraries like `react-testing-library` or `enzyme`.

## 13. Package Management

- Use `npm` or `yarn` for package management.
- Keep the `package.json` file organized and up-to-date.

```json
// package.json
{
  "name": "react-app",
  "version": "1.0.0",
  "dependencies": {
    "react": "^17.0.2",
    "react-dom": "^17.0.2"
  }
}
```

## 14. Adding License and Copyright Notice

For every source code file in your React.js project, include a license and copyright notice at the top of the file. This ensures proper attribution and protection of your organization's intellectual property.

```javascript
/*
 * Devspace IIT(ISM) Dhanbad
 *
 * This software and related documentation are owned by Devspace IIT(ISM) Dhanbad.
 * Unauthorized copying, reproduction, or modification via any medium is strictly prohibited.
 * Proprietary and confidential. All rights reserved.
 */

// Rest of your code starts here
import React from "react";
import ReactDOM from "react-dom";
import App from "./App";
```

## 15. Conclusion

Congratulations! By following these comprehensive React.js coding guidelines and best practices, you're well-equipped to develop clean, modular, and efficient UI components. Remember that these guidelines are meant to support your growth as a React.js developer. Continuously seek opportunities to enhance your skills and contribute to the success of your projects.

Happy coding!
