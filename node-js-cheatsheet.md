# Node.js Cheat Sheet

> **Goal:** Learn the most common Node.js and npm commands clearly enough to use them as a beginner.

This cheat sheet is for Node.js projects on Linux, macOS, and Windows.

## How To Read This Sheet

| Pattern | Meaning |
|---|---|
| `[file]` | replace with a real file name, such as `app.js` |
| `[package]` | replace with a package name, such as `express` |
| `[script]` | replace with an npm script name |

## Table Of Contents

| Section | What You Learn |
|---|---|
| [Setup](#setup) | check Node.js and npm versions |
| [Running Code](#running-code) | run JavaScript files and commands |
| [npm](#npm) | manage packages and project files |
| [Scripts](#scripts) | use package.json scripts |
| [Useful Patterns](#useful-patterns) | common Node.js syntax |

## Setup

| Command | Clear Description |
|---|---|
| `node --version` | Show the installed Node.js version. |
| `npm --version` | Show the installed npm version. |
| `npx --version` | Show the installed npx version. |

Example:

```bash
node --version
npm --version
```

## Running Code

| Command | Clear Description |
|---|---|
| `node [file]` | Run a JavaScript file. Example: `node app.js`. |
| `node -e "code"` | Run a short JavaScript command from the terminal. |
| `node` | Open the Node.js REPL. |

Example:

```bash
node app.js
node -e "console.log('Hello, world')"
```

## npm

| Command | Clear Description |
|---|---|
| `npm init` | Create a new package.json interactively. |
| `npm init -y` | Create package.json with default values. |
| `npm install [package]` | Install a package and add it to dependencies. |
| `npm install -D [package]` | Install a package as a dev dependency. |
| `npm uninstall [package]` | Remove a package. |
| `npm list` | Show installed packages. |
| `npm outdated` | Show packages that have newer versions available. |

Example:

```bash
npm init -y
npm install express
```

## Scripts

| Command | Clear Description |
|---|---|
| `npm run [script]` | Run a custom script from package.json. |
| `npm start` | Run the start script if it exists. |
| `npm test` | Run the test script if it exists. |
| `npx [package]` | Run a package without installing it globally. |

Example:

```json
{
	"scripts": {
		"start": "node app.js",
		"dev": "node app.js"
	}
}
```

## Useful Patterns

| Pattern | Clear Description |
|---|---|
| `require("module")` | Import modules in CommonJS style. |
| `import ... from "module"` | Import modules in ES module style. |
| `console.log(value)` | Print a value for quick debugging. |
| `process.env.NAME` | Read an environment variable. |

Example:

```js
const fs = require("fs");

console.log(process.env.NODE_ENV || "development");
```

## Where DevOps Engineers Use This

Use Node.js when you are working on JavaScript services or toolchains that support deployment work.

- Run build tools, CLIs, and package scripts in CI/CD.
- Support backend services, APIs, and server-side rendering apps.
- Use npm scripts to standardize development and release commands.
