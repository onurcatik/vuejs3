# Hello World

This tutorial will guide you through creating your first Vue 3 application using the Vue CLI. We will cover setting up your development environment, installing necessary tools, and creating a basic Vue project. This tutorial is intended for developers who want to get started with Vue.js 3 efficiently.

## Setting Up Your Development Environment

### Prerequisites

To get started with Vue.js 3, ensure you have the following installed:

1. **Node.js**: Download and install the latest stable release from [nodejs.org](https://nodejs.org). If you already have Node.js installed, make sure to update it to the latest version.
2. **Text Editor**: Use any text editor of your choice. We recommend Visual Studio Code (VS Code), which can be downloaded from [code.visualstudio.com](https://code.visualstudio.com).

### Installing VS Code Extensions

After installing VS Code, install the Vetur extension, which provides syntax highlighting, code snippets, linting, formatting support, and more for Vue.js:

1. Open VS Code.
2. Go to the Extensions tab.
3. Search for "Vetur" and install it.

## Creating a Vue Application

There are several ways to add Vue.js to a project. We will focus on using the Vue CLI, which is efficient for setting up single-page applications (SPAs) quickly.

### Installing Vue CLI

The Vue CLI (Command Line Interface) allows you to create and manage Vue projects efficiently. Follow these steps to install the Vue CLI:

1. Open a command prompt or terminal as an administrator. On Windows, you can do this by right-clicking the Command Prompt icon and selecting "Run as administrator."
2. Install the Vue CLI globally using either Yarn or npm:

   ```sh
   # Using Yarn
   yarn global add @vue/cli
   
   # Using npm
   npm install -g @vue/cli
   ```

3. Verify the installation by checking the Vue CLI version:

   ```sh
   vue --version
   ```

## Creating Your First Vue Project

With the Vue CLI installed, you can now create a new Vue project. Follow these steps:

1. Open a terminal or command prompt.
2. Navigate to the directory where you want to create your project.
3. Run the following command to create a new project called `hello-world`:

   ```sh
   vue create hello-world
   ```

4. The Vue CLI will prompt you to pick a preset. Choose the default preset with Vue 3, Babel, and ESLint by selecting the second option: "Default (Vue 3) ([Vue 3] babel, eslint)."
5. You will be prompted to choose a package manager. Select `yarn` or `npm` according to your preference.

The CLI will now scaffold a new project in the `hello-world` directory.

## Running the Vue Application

After the project is created, you can run it locally to see your first Vue application in action:

1. Navigate to the project directory:

   ```sh
   cd hello-world
   ```

2. Start the development server:

   ```sh
   # Using Yarn
   yarn serve
   
   # Using npm
   npm run serve
   ```

3. The development server will start, and you will see output indicating the server is running on `localhost`. Open your browser and go to `http://localhost:8080` to see your Vue application.

You should see a default Vue.js application with a "Hello World" message and links to Vue documentation and other resources.

## Summary

In this tutorial, you have learned how to set up your development environment, install Vue CLI, create a new Vue.js 3 project, and run your application locally. The Vue CLI simplifies the process of starting a new Vue project and helps you focus on building your application rather than configuring build tools.

In the next tutorial, we will explore the project's folder structure and understand how the Vue application is organized.

```sh
# Commands Summary
yarn global add @vue/cli
vue create hello-world
cd hello-world
yarn serve
```

Stay tuned for the next tutorial where we delve deeper into the structure of a Vue.js project and start building more complex applications.