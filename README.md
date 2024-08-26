# GitHub Search App

Welcome to the GitHub Search App! This is a Vue.js application that lets you search for GitHub users or repositories with a responsive interface.

## What It Does

- **Search**: Find GitHub users or repositories.
- **Toggle**: Switch between searching users or repositories with a toggle.
- **Results**: See your search results.

## Approach

To create this app, I took the following approach:

1. **Component-Based Architecture**: Utilized Vue.js components for modularity:
   - **SearchBar**: Handles user input and search requests.
   - **RepoItem** and **UserItem**: Display search results for repositories and users, respectively.
   - **PageLoader**: Provides a visual loading indicator during data fetching.

2. **API Integration**: Integrated with the GitHub API to fetch user and repository data:
   - Used `axios` for making HTTP requests.
   - Implemented error handling to manage API issues.

This template should help get you started developing with Vue 3 in Vite.

## Recommended IDE Setup

[VSCode](https://code.visualstudio.com/) + [Volar](https://marketplace.visualstudio.com/items?itemName=Vue.volar) (and disable Vetur).

## Customize configuration

See [Vite Configuration Reference](https://vitejs.dev/config/).

## Project Setup

```sh
npm install
```

### Compile and Hot-Reload for Development

```sh
npm run dev
```

### Compile and Minify for Production

```sh
npm run build
```

### Lint with [ESLint](https://eslint.org/)

```sh
npm run lint
```