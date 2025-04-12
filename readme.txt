TechBlogs Project - README

1.  Description

    TechBlogs is a web application (likely a blog or article platform) built with Vue.js. It aims to provide a space for sharing articles, tutorials, and information, possibly related to technology, as indicated by the name.

2.  Repository

    The project's source code is hosted on GitHub:
    https://github.com/Evin-7/TechBlogs.git

3.  Technologies Used

    * Frontend Framework: Vue.js
    * Bundler: Vite
    * Styling: Tailwind CSS
    * Routing: Vue Router
    * Code Formatting: Prettier
    * Code Linting: ESLint

4.  Prerequisites

    Before you can run this project, you need to have the following software installed on your system:

    * Node.js: (Version 18 or later is recommended). You can download it from https://nodejs.org/
    * npm: (Usually comes with Node.js)
    * Git: (If you want to clone the repository). You can download it from https://git-scm.com/

5.  Installation and Setup Instructions

    Follow these steps to get the project running on your local machine:

    Step 1: Clone the repository

    Open your terminal or command prompt and navigate to the directory where you want to store the project. Then, run the following command:

    ```bash
    git clone [https://github.com/Evin-7/TechBlogs.git](https://github.com/Evin-7/TechBlogs.git)
    ```

    This will create a copy of the project on your local machine.

    Step 2: Navigate to the project directory

    Use the `cd` command to go into the project's directory:

    ```bash
    cd TechBlogs
    ```

    Step 3: Install dependencies

    Run the following command to install all the necessary packages and libraries:

    ```bash
    npm install
    ```

    This command uses the `package.json` file (provided below) to download the required dependencies.

    Step 4: Run the development server

    To start the application in development mode, use this command:

    ```bash
    npm run dev
    ```

    This will build the project and start a local development server. You can then view the application in your web browser, usually at `http://localhost:5173`.

    Step 5: Building for Production (Optional)
    To create an optimized build for deployment, use:
    ```bash
    npm run build
    ```

    Step 6: Previewing the Production Build (Optional)
    To preview the production build locally, use:
    ```bash
    npm run preview
    ```

6.  Package.json

    ```json
    {
      "name": "techblogs",
      "private": true,
      "version": "0.0.0",
      "type": "module",
      "scripts": {
        "dev": "vite",
        "build": "vite build",
        "lint": "eslint . --ext .js,.vue --fix",
        "format": "prettier --write .",
        "preview": "vite preview"
      },
      "dependencies": {
        "eslint-config-prettier": "^10.1.1",
        "prettier": "^3.5.3",
        "vue": "^3.5.13",
        "vue-router": "^4.5.0"
      },
      "devDependencies": {
        "@eslint/js": "^9.22.0",
        "@vitejs/plugin-vue": "^5.2.1",
        "autoprefixer": "^10.4.21",
        "eslint": "^9.22.0",
        "eslint-plugin-vue": "^10.0.0",
        "globals": "^16.0.0",
        "postcss": "^8.5.3",
        "tailwindcss": "^3.4.17",
        "vite": "^6.2.0"
      }
    }
    ```

7.  Key Dependencies

    * `vue`: The core Vue.js framework.
    * `vue-router`: For handling navigation between different pages in the application.

8.  Key DevDependencies

    * `@vitejs/plugin-vue`: Vite plugin for Vue.js single-file components.
    * `vite`: A fast build tool that significantly improves the development experience.
    * `eslint`: A tool for identifying and fixing coding style issues.
    * `prettier`: A code formatter for consistent code style.
    * `tailwindcss`: A utility-first CSS framework.

9.  Contact

    If you have any questions or issues, please contact me.
