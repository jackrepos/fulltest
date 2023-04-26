# fulltest

Fulltest is a web-based project that aims to provide sample codes for testing code.

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

### Type-Check, Compile and Minify for Production

```sh
npm run build

# To deploy on github. If there is a custom domain added to github then you need to download the CNAME file that github automatically create and push in the branch into /dist
npm run deploy
```

### Guide to deploy on github pages

To deploy your Vite app to GitHub Pages, follow these steps:

1. Make sure you have the `gh-pages` branch in your repository.

2. Add a `deploy` script to your `package.json`:

In your `package.json`, add the following script:

```json
"scripts": {
  "deploy": "gh-pages -d dist",
  ...
}
```

This script will use the `gh-pages` CLI to deploy the `dist` directory to your `gh-pages` branch.

3. Build your Vite app for production:

Run the following command in your terminal:

```
npm run build
```

This command will build your Vite app for production and create a `dist` folder with the optimized output.

4. Install the `gh-pages` CLI:

If you haven't already installed the `gh-pages` CLI, install it as a development dependency:

```
npm install gh-pages --save-dev
```

5. Configure the `publicPath` for your Vite app:

In your `vite.config.js` file, set the `publicPath` to the correct path for your GitHub Pages repository. Replace `your-repo-name` with the name of your GitHub repository:

```javascript
// vite.config.js
export default {
  build: {
    publicPath: '/your-repo-name/',
  },
}
```

If you don't have a `vite.config.js` file, create one at the root of your project and add the above content.

6. Deploy your Vite app to GitHub Pages:

Run the following command in your terminal:

```
npm run deploy
```

This command will deploy your Vite app to the `gh-pages` branch of your GitHub repository.

7. Configure your GitHub repository to use the `gh-pages` branch:

Go to your GitHub repository's settings page, scroll down to the "GitHub Pages" section, and select the `gh-pages` branch as the source. Save the changes.

8. Access your Vite app on GitHub Pages:

Your Vite app will be available at `https://<your-github-username>.github.io/your-repo-name/`, where you should replace `<your-github-username>` with your GitHub username and `your-repo-name` with the name of your GitHub repository.

Note: It might take a few minutes for your GitHub Pages site to become available after deployment.

### Other docs

```
## Recommended IDE Setup

[VSCode](https://code.visualstudio.com/) + [Volar](https://marketplace.visualstudio.com/items?itemName=Vue.volar) (and disable Vetur) + [TypeScript Vue Plugin (Volar)](https://marketplace.visualstudio.com/items?itemName=Vue.vscode-typescript-vue-plugin).

## Type Support for `.vue` Imports in TS

TypeScript cannot handle type information for `.vue` imports by default, so we replace the `tsc` CLI with `vue-tsc` for type checking. In editors, we need [TypeScript Vue Plugin (Volar)](https://marketplace.visualstudio.com/items?itemName=Vue.vscode-typescript-vue-plugin) to make the TypeScript language service aware of `.vue` types.

If the standalone TypeScript plugin doesn't feel fast enough to you, Volar has also implemented a [Take Over Mode](https://github.com/johnsoncodehk/volar/discussions/471#discussioncomment-1361669) that is more performant. You can enable it by the following steps:

1. Disable the built-in TypeScript Extension
    1) Run `Extensions: Show Built-in Extensions` from VSCode's command palette
    2) Find `TypeScript and JavaScript Language Features`, right click and select `Disable (Workspace)`
2. Reload the VSCode window by running `Developer: Reload Window` from the command palette.
```
