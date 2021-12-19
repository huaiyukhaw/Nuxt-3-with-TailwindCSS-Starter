
# Nuxt 3 Minimal Starter with TailwindCSS



## Create a Nuxt 3 project



Initialize a nuxt3 project



```npx nuxi init nuxt3-app```



Change into the new project directory



```cd nuxt3-app```



Install the dependencies



```npm install```



Start the dev server



```npm run dev```




## Add TailwindCSS to the project



Install TailwindCSS via the terminal



```npm install -D tailwindcss@latest postcss@latest autoprefixer@latest```



Create a Tailwind config file



```npx tailwindcss init```



This command will create a tailwind.config.js file at the root of your project, open the file and update it like so:



```
// tailwind.config.js

module.exports = {

mode: "jit",

purge: [

"./components/**/*.{vue,js}",

"./layouts/**/*.vue",

"./pages/**/*.vue",

"./plugins/**/*.{js,ts}",

"./nuxt.config.{js,ts}",

],

darkMode: false, // or 'media' or 'class'

theme: {

extend: {},

},

variants: {

extend: {},

},

plugins: [],

};

```



Next, we need to include Tailwind in our CSS file. Mine is located at this path: assets/css/tailwind.css. Let’s update this file with this snippet:



```
@tailwind base;

@tailwind components;

@tailwind utilities;
```


Finally, we need to tell Nuxt how to find that file and also set up our post CSS options to include both the Tailwind and autoprefixer plugins. Open nuxt.config.ts and update it with:


```
import { defineNuxtConfig } from "nuxt3";

export default defineNuxtConfig({

css: ["~/assets/css/tailwind.css"],

build: {

postcss: {

postcssOptions: {

plugins: {

tailwindcss: {},

autoprefixer: {},

},

},

},

},

});

```



Open the `App.vue` file, create a `<script>` tag to import your CSS file like so:



```
<script lang="ts" setup>

import './assets/css/tailwind.css'

</script>

```