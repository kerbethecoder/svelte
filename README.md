![image](public/snap.png)

![Static Badge](https://img.shields.io/badge/svelte-v4%2e2%2e18-fb8400) ![Static Badge](https://img.shields.io/badge/tailwindcss-v3%2e4%2e7-38bdf8)

"[Svelte](https://svelte.dev/) is a tool for building web applications. Like other user interface frameworks, it allows you to build your app _declaratively_ out of components that combine markup, styles, and behaviours."

This guide provides a first-hand experience on building a Svelte project using [Vite](https://vitejs.dev/guide/#scaffolding-your-first-vite-project) + [Tailwind CSS](https://tailwindcss.com/docs/guides/sveltekit) and deploying it on [GitHub Pages](https://pages.github.com/).

## 🛠️ Installation

**1. Create your project.**

```bash
# terminal
npm create vite@latest project_name -- --template svelte
cd project_name
```

**2. Install Tailwind CSS.**

```bash
# terminal
npm install -D tailwindcss postcss autoprefixer
npx tailwindcss init -p
```

**3. Configure your template paths.**

```js
// tailwind.config.js
/** @type {import('tailwindcss').Config} */
export default {
  content: ['./src/**/*.{html,js,svelte,ts}'],
  theme: {
    extend: {},
  },
  plugins: [],
};
```

**4. Add the Tailwind directives to your CSS.**

```css
/* app.css */
@tailwind base;
@tailwind components;
@tailwind utilities;
```

**5. Start your build process.**

```bash
# terminal
npm run dev
```

**6. Start coding.**

```html
<h1 class="text-3xl font-bold underline">Hello world!</h1>
```

## 🗂️ File Structure

Feel free to customize your file structure or follow this from [MDN](https://developer.mozilla.org/en-US/docs/Learn/Tools_and_testing/Client-side_JavaScript_frameworks/Svelte_getting_started#application_structure).

```
my-project/
├── README.md
├── package.json
├── package-lock.json
├── rollup.config.js
├── .gitignore
├── node_modules
├── public
│   ├── favicon.png
│   ├── index.html
│   ├── global.css
│   └── build
│       ├── bundle.css
│       ├── bundle.js
│       └── bundle.js.map
├── scripts
│   └── setupTypeScript.js
└── src
    ├── App.svelte
    └── main.js
```

## 🛫 How to deploy to GitHub Pages

Deploying to github pages is totally up to you, be it through **[GitHub Actions](https://docs.github.com/en/actions/deployment/about-deployments/deploying-with-github-actions)**, or via **[gh-pages](https://www.npmjs.com/package/gh-pages)** package, or manually.

> [!NOTE]
>
> - Take note of the specific configurations for your project before deploying it, otherwise, it won't work properly on production. Refer to the documentations for [Svelte](https://svelte.dev/docs/introduction).
> - Also take note that [GitHub Pages](https://pages.github.com/) have limitations, it's free, yes, but it has a limit.

### ❗ via package ❗

**1. Install `gh-pages` package.**

```bash
npm install gh-pages --save-dev
```

**2. Add base path to your repo in `vite.config.js`.**

```js
// vite.config.js
import { defineConfig } from 'vite';
import { svelte } from '@sveltejs/vite-plugin-svelte';

// https://vitejs.dev/config/
export default defineConfig({
  plugins: [svelte()],
  base: '/svelte', // repo name
});
```

**3. Add `deploy` to your scripts.**

```json
{
  "scripts": {
    "deploy": "npm run build && gh-pages -d build"
  }
}
```

**4. Create and configure a new branch for `gh-pages`.**
> [!IMPORTANT]
>
> Make sure that you have committed your changes before doing this. All untracked and staged files may be deleted.

I like to do this manually. If there is some automated way, feel free to let me know by any means.

```bash
git checkout --orphan gh-pages
git reset --hard
git commit --allow-empty -m 'commit_message'
git push origin gh-pages
```

**5. Publish the production build.**

```bash
npm run deploy
```

### ❗ via manually configuring github pages settings ❗

**1. Create your project.**
Start coding your project, either use a framework like React, Vue, or not.

**2. Publish production build to GitHub.**
Push your _production build_ to your github repo. After that, check if your `index.html` file is uploaded, since it is one of the core files needed for your website to work.

**3. Configure your GitHub Pages on repo Settings.**
Navigate to `Settings > Pages > Build and deployment`. Make sure the **Source** says 'Deploy from a branch', and then configure the **Branch** settings and change it to your branch with the files.

---

🌎 [kerbethecoder](https://kerbethecoder.com/)  
📫 krby.cnts@gmail.com  
📌 July 28, 2024
