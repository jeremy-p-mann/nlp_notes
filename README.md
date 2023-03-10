# NLP Notes

Developing this repo requires npm

## Basics

```bash
brew install node
```

To install the package:

```bash
npm install
```

To see your changes live:

```bash
npm run dev
```

Main branch is protected, so please branch off of main and open a PR for new
changes.

## Adding a New Page

First, create the markdown file, e.g.:

```bash
cp ./src/content/docs/en/template.md ./src/content/docs/en/template.md
```

Edit the title and description, then add content. Once you have the page, you
integrate it into the sidebar by modifying `./src/consts.ts`, see:

```javascript
export const SIDEBAR: Sidebar = {
// it's hopefully clear how to do this.
}
```

## Branches

## 🧞 Commands

All commands are run from the root of the project, from a terminal:

| Command                | Action                                           |
| :--------------------- | :----------------------------------------------- |
| `npm install`          | Installs dependencies                            |
| `npm run dev`          | Starts local dev server at `localhost:3000`      |
| `npm run build`        | Build your production site to `./dist/`          |
| `npm run preview`      | Preview your build locally, before deploying     |
| `npm run astro ...`    | Run CLI commands like `astro add`, `astro check` |
| `npm run astro --help` | Get help using the Astro CLI                     |

For basics on astro see the [documentation](https://docs.astro.build)

## Customize This Theme

### Site metadata

`src/config.ts` contains several data objects that describe metadata about your site like title, description, default language, and Open Graph details. You can customize these to match your project.

### CSS styling

The theme's look and feel is controlled by a few key variables that you can customize yourself. You'll find them in the `src/styles/theme.css` CSS file.

If you've never worked with CSS variables before, give [MDN's guide on CSS variables](https://developer.mozilla.org/en-US/docs/Web/CSS/Using_CSS_custom_properties) a quick read.

This theme uses a "cool blue" accent color by default. To customize this for your project, change the `--theme-accent` variable to whatever color you'd like:

```diff
/* src/styles/theme.css */
:root {
  color-scheme: light;
-  --theme-accent: hsla(var(--color-blue), 1);
+  --theme-accent: hsla(var(--color-red), 1);   /* or: hsla(#FF0000, 1); */
```

## Page metadata

Astro uses frontmatter in Markdown pages to choose layouts and pass properties to those layouts. If you are using the default layout, you can customize the page in many different ways to optimize SEO and other things. For example, you can use the `title` and `description` properties to set the document title, meta title, meta description, and Open Graph description.

```markdown
---
title: Example title
description: Really cool docs example that uses Astro
layout: ../../layouts/MainLayout.astro
---

# Page content...
```
For more SEO related properties, look at `src/components/HeadSEO.astro`

### Sidebar navigation

The sidebar navigation is controlled by the `SIDEBAR` variable in your `src/config.ts` file. You can customize the sidebar by modifying this object. A default, starter navigation has already been created for you.

```ts
export const SIDEBAR = {
  en: [
    { text: "Section Header", header: true },
    { text: "Introduction", link: "en/introduction" },
    { text: "Page 2", link: "en/page-2" },
    { text: "Page 3", link: "en/page-3" },

    { text: "Another Section", header: true },
    { text: "Page 4", link: "en/page-4" },
  ],
};
```
