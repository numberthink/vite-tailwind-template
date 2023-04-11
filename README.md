# Vite Tailwind Template

This is my go-to, simple, vanilla site template with TailwindCSS for styling. 

To use it you can simply clone this repo:

```bash
npx degit https://github.com/numberthink/vite-tailwind-template.git
```

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

Install tailwind dependencies and plugins (tailwind forms, taolwind typography, autoprefixer, and postcss):

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
  content: ['./**/*.html'],
  theme: {
    extend: {},
  },
  plugins: [
    	require('@tailwindcss/typography'),
		require('@tailwindcss/forms'),
  ],
}

```

Update PostCSS config?

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

Update Vite config?

```js
import { sveltekit } from '@sveltejs/kit/vite';
import tailwindcss from 'tailwindcss';
/** @type {import('vite').UserConfig} */
const config = {
	plugins: [sveltekit(), tailwindcss()],
	test: {
		include: ['src/**/*.{test,spec}.{js,ts}']
	}
};

export default config;
```

Run tailwind "watch" command:

```bash
npx tailwindcss -i ./src/input.css -o ./dist/output.css --watch
```

Add stylesheet import to HTML:

```html
<link href="/src/input.css" rel="stylesheet">
```
