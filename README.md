# Vite Tailwind Template

This is a basic, vanilla site template with [TailwindCSS](https://tailwindcss.com/) for styling. 

To use it you can simply clone this repo:

```bash
npx degit https://github.com/numberthink/vite-tailwind-template.git
```

Install dependencies:

```bash
npm install
```

And run it:

```bash
npm run dev
```

## Rebuild from scratch

Or follow the steps I took to create it from scratch:

1. Create a vanilla Vite project

```bash
npm create vite@latest
```

And choose "vanilla" and then follow the instructions.

2. Install Tailwind

```bash
npm i tailwindcss
```

Init tailwind:

```bash
npx tailwindcss init
```

Install tailwind dependencies and plugins (tailwind forms (optional), tailwind typography (optional), autoprefixer, and postcss):

```bash
npm i @tailwindcss/forms
npm i @tailwindcss/typography
npm i autoprefixer
npm i postcss
```

Update Tailwind config (`tailwind.config.js` in the root folder):

```js
/** @type {import('tailwindcss').Config} */
export default {
  mode: 'jit',
  content: ['./index.html'],
  theme: {
    extend: {},
  },
  plugins: [
    require('@tailwindcss/typography'),
	require('@tailwindcss/forms'),
  ],
}
```

Update PostCSS config (`postcss.config.js`)

```js
const tailwind = require('tailwindcss');
const autoprefixer = require('autoprefixer');

module.exports = {
	plugins: [
		// Some plugins, like postcss-nested, need to run before Tailwind
		tailwind(),
		// But others, like autoprefixer, need to run after
		autoprefixer()
	]
};

```

Run tailwind "watch" command:

```bash
npx tailwindcss -i ./src/input.css -o ./dist/output.css --watch
```

Add stylesheet import to HTML:

```html
<link href="/src/input.css" rel="stylesheet">
```
