# V3LT - Vue 3 Project Template

I got tired of setting up Vue 3 projects from scratch every time — so I made this starter. If you're also "that person," this might save you a few minutes (or hours).

## 🚀 Getting Started

Navigate to the folder where you want to create your project, then run:

```bash
npx degit dev-murphy/v3lt <my-project>
```

Replace `<my-project>` with your desired project name.

Remove the `.git` folder ...

```bash
rm -fr .git
```

And re-initialize the git repo. _(Optional)_

```bash
git init
git add .
git commit -m "feat: initial commit"
git branch -M main
git push -u origin main
```

Once it's cloned, feel free to customize and build from there. Make it your own — and go beyond!

## ⚙️ What's Included

This template includes tools and packages I almost always use in Vue 3 projects:

> 💡 **Note:**  
> This project uses the **Vite Vue template**, **PNPM** as the package manager, and **TypeScript** by default. You can easily switch to your preferred package manager if needed.

### Core Tools & Features

- 🌿 [Tailwind CSS](https://tailwindcss.com/docs/installation/using-vite) – Utility-first CSS framework
- 🧠 [Pinia](https://pinia.vuejs.org/getting-started.html) – State management
- 🧭 [Vue Router](https://router.vuejs.org/) + [unplugin-vue-router](https://github.com/posva/unplugin-vue-router) – File-based routing
- 🪄 [unplugin-auto-import](https://github.com/unplugin/unplugin-auto-import) – Auto-import common APIs (like Vue composition utilities)
- 🧩 [unplugin-vue-components](https://github.com/unplugin/unplugin-vue-components) – Auto-import Vue components
- 🧰 [VueUse](https://vueuse.org/) (optional) – Collection of essential Vue Composition API utilities

## 🙌 Acknowledgements

Big thanks to [@antfu](https://github.com/antfu) — this template draws heavy inspiration from his amazing [Vitesse](https://github.com/antfu-collective/vitesse) starter. Keep up the great work ❤️
