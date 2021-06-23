---
theme: default
title: 'Create Icon Package With Vue and Rollup'
download: true
monaco: false
routerMode: 'hash'
colorSchema: 'dark'
highlighter: Prism
info: |
  ## Create Icon Package With Vue and Rollup
  By Lucky Dewa Satria.
---

<style>
  .text-gradient {
    background-color: #2B90B6;
    background-image: linear-gradient(45deg, #4EC5D4 10%, #146b8c 20%);
    background-size: 100%;
    -webkit-background-clip: text;
    -moz-background-clip: text;
    -webkit-text-fill-color: transparent; 
    -moz-text-fill-color: transparent;
  }
  .text-gradient-red {
    background-color: #2B90B6;
    background-image: linear-gradient(45deg, #f59e0b 10%, #ef4444 20%);
    background-size: 100%;
    -webkit-background-clip: text;
    -moz-background-clip: text;
    -webkit-text-fill-color: transparent; 
    -moz-text-fill-color: transparent;
  }
  .cover {
    color: white;
    background-image: linear-gradient(rgba(0, 0, 0, 0.333), rgba(0, 0, 0, 0.533)), url('/bg.jpeg');
    background-repeat: no-repeat;
    background-position: center center;
    background-size: cover;
  }
</style>

<div class="cover text-center">
  <div class="backdrop-filter backdrop-blur-sm p-8">
    <span class="text-4xl mb-4 block font-semibold">Create Vue Icon Package With Rollup</span>
    <div class="flex justify-center items-center">
      <img
        src="/contact/vue-logo.png"
        class="h-40 mx-2"
        title="Vue"
        alt="Vue"
      />
      <img
        src="/npm-logo.png"
        class="h-25 mx-2"
        title="npm"
        alt="npm"
      />
    </div>
    <span class="block mt-3">From the developer, by the developer, for the developer.</span>
    <div class="pt-12">
      <span @click="$slidev.nav.next" class="px-2 p-1 rounded cursor-pointer" hover="bg-white bg-opacity-10">
        Press Space for next page <carbon:arrow-right class="inline"/>
      </span>
    </div>
  </div>
</div>
<div class="p-1  bg-gradient-to-r from-yellow-500 via-red-500 to-purple-500 absolute bottom-0 right-0 left-0"></div>

---

<span class="text-gradient-red text-2xl font-bold">Prerequisites</span>

This talks is about a step by step guid for creating a Vue2 icon package (module) with Rollup. Finally is explained the basis for running, installing and then publishing locally or publicly.

- 🧑‍💻 Basic knowledge of Javascript and Vue2 is required
- 💾 Basic knowledge of Vue SFC is required
- 🤹 Knowledge of Rollup is good, but not needed
- 🛠 You must be familiar and comfortable with the command line

<br>
<br>

You can read more about publishing simple package to npm here: <br>
[Simply Publish Your Package to npm](https://masukin.link/talks/simply-publish-your-package-to-npm)

<br>
<br>

Read more about [Vue SFC?](https://v3.vuejs.org/guide/single-file-component.html#introduction)

<div class="p-1  bg-gradient-to-r from-yellow-500 via-red-500 to-purple-500 absolute bottom-0 right-0 left-0"></div>

---

<span class="text-gradient-red text-2xl font-bold">About Rollup</span>

I found in rollup a great tool for creating npm modules. Is particularly easy to understand, no need so much configuration but it's open for add more extras depending of your needs.

<div class="flex items-center">
  <img
    src="/rollup.jpeg"
    class="h-60"
    border="rounded-lg"
    title="Rollup"
    alt="Rollup"
  />
  <span class="p-6 leading-loose">
    Rollup is a module bundler for JavaScript which compiles small pieces of code into something larger and more complex, such as a library or application.
    It can output CommonJs, EJS, and UMD.
    <br> We'll talk about it later.
  </span>
</div>

Read more about [rollup](https://rollupjs.org/guide/en/)

<div class="p-1  bg-gradient-to-r from-yellow-500 via-red-500 to-purple-500 absolute bottom-0 right-0 left-0"></div>

---

<span class="text-gradient-red text-2xl font-bold">About Vue SFC Rollup</span>

It's the fastest way to produce npm-ready vue components! It shipped with a minimal rollup config and development environment. This package is a very useful utility when starting a component library.

<img
  src="/vue-sfc.png"
  class="h-60"
  border="rounded-lg"
  title="Vue SFC"
  alt="Vue SFC"
/>

Read more about [vue-sfc-rollup](https://github.com/team-innovation/vue-sfc-rollup)

<div class="p-1  bg-gradient-to-r from-yellow-500 via-red-500 to-purple-500 absolute bottom-0 right-0 left-0"></div>

---

<div class="absolute top-1/2 left-1/2 transform-gpu -translate-x-1/2 -translate-y-1/2 w-11/12">
  <div class="flex items-center">
    <div>
      <h1>Let's begin with imagination.</h1>
      <h3 class="text-white">
        Let's assume we are working on <span class="text-yellow-500">3 different projects</span> using <span class="text-purple-500">one beautiful design system</span> that our designer already created for us. We are going to create a SPA for 3 different projects. The bundle size is a constraint. We cannot have too large a bundle size since it directly affects the performance of our app. Then we need to  <span class="text-yellow-500">make sure every app is consistent especially the icon</span>. So, let’s look at how we can create a single codebase that shared across 3 different project
      </h3>
    </div>
    <img
      src="/npm-wombat.jpeg"
      class="h-60 ml-8"
      border="rounded-lg"
      title="wombat mascot"
      alt="wombat mascot"
    />
  </div>
</div>
<div class="p-1  bg-gradient-to-r from-yellow-500 via-red-500 to-purple-500 absolute bottom-0 right-0 left-0"></div>

---

<span class="text-gradient-red text-2xl font-bold">Project Overview</span>

We want to create a simple component wrapper for our svg icon, then publish it locally with package file. They will make it easy to maintain a consistent look and feel across an application.

`npm i icon-pack-0.0.1.tgz`

<div class="flex">
  <div>

```ts
<script lang="ts">
import Vue from 'vue';
import { OurIcon } from '@/entry.esm';
export default Vue.extend({
  name: 'ServeDev',
  components: {
    OurIcon,
  },
});
</script>

<template>
  <div id="app">
    <our-icon icon="monster" style="color:#ef4444; font-size:10em" />
  </div>
</template>
```

  </div>
  <div class="ml-5 w-78">
    <img
      src="/result.png"
      class="w-full"
      border="rounded-lg"
      title="Result"
      alt="Result"
    />
    <div class="bg-yellow-500 p-2 py-1 mt-2 rounded-lg">
      <span class="text-xs">We will use free icons made by <a href="http://www.dariusdan.com" title="Darius Dan">Darius Dan</a> from <a href="https://www.flaticon.com/" title="Flaticon">www.flaticon.com</a></span>
    </div>
  </div>
</div>
<div class="p-1  bg-gradient-to-r from-yellow-500 via-red-500 to-purple-500 absolute bottom-0 right-0 left-0"></div>

---

<span class="text-gradient-red text-2xl font-bold">1.0</span> <span class="text-2xl font-bold">You'll want to install the vue-sfc-rollup globally </span>

<div class="flex justify-between">
  <div class="w-1/2">

`npm install -g vue-sfc-rollup`

Once that is installed globally...

`cd develop`

run the following command to initialize the project.

`sfc-init`, see options on the right

`cd path/to/my-component-or-lib`

`npm install`

Once that is done, you can open the folder up in your editor of choice.

  </div>
  <div class="w-1/2">
    Choose the following options within the prompts: <br/><br/>
    <ul>
      <li><b>Which version of Vue are you writing for?</b> Vue 2</li>
      <li><b>Is this a single component or a library?</b> Library</li>
      <li><b>What is the npm name of your library?</b> this will need to be unique on npm. I used my-icon-pack)</li>
      <li><b>Will this library be written in JavaScript or TypeScript?</b> JavaScript (feel free to use TypeScript if you know what you're doing)</li>
      <li><b>Enter a location to save the library files:</b> This is the folder name you want your library to have. It will default to the npm name you gave it above so you can just hit enter.</li>
    </ul>
  </div>
</div>

<div class="p-1  bg-gradient-to-r from-yellow-500 via-red-500 to-purple-500 absolute bottom-0 right-0 left-0"></div>

---

<span class="text-2xl font-bold">Folder Structure</span>

<div class="flex justify-between">
  <div class="w-1/2">
    <div class="grid grid-cols-2 gap-2">
      <div class="rounded-lg bg-gray-700 p-3">
        <img
          src="/folder-1.png"
          class="w-60"
          border="rounded-sm"
          title="folder"
          alt="folder"
        />
        <span class="text-xs my-1 block">A minimal rollup config from vue-sfc. It will output esm, cjs and iife format for our library</span>
      </div>
      <div class="rounded-lg bg-gray-700 p-3">
        <img
          src="/folder-2.png"
          class="w-60"
          border="rounded-sm"
          title="folder"
          alt="folder"
        />
        <span class="text-xs my-1 block">a sample usage file which can be used to load and test your component/library during development</span>
      </div>
      <div class="rounded-lg bg-gray-700 p-3">
        <img
          src="/folder-3.png"
          class="w-60"
          border="rounded-sm"
          title="folder"
          alt="folder"
        />
        <span class="text-xs my-1 block"> This is the place where our component library is present.</span>
      </div>
      <div class="rounded-lg bg-gray-700 p-3">
        <img
          src="/folder-4.png"
          class="w-60"
          border="rounded-sm"
          title="folder"
          alt="folder"
        />
        <span class="text-xs my-1 block">Babel config and generated package.json from vue-sfc</span>
      </div>
    </div>
  </div>
  <div class="w-1/2 ml-4">
    <span class="text-base">
    There is a sample Vue component built for us. You can find it inside of the <span class="bg-gray-700 px-1 rounded-sm">/src/lib-components</span> folder. To see what this component looks like, you can run <span class="bg-gray-700 px-1 rounded-sm">npm run serve</span> and navigate to <a href="http://localhost:8080/">http://localhost:8080/</a>
    </span>
    <br/><br/>
    Don't forget to <span class="bg-gray-700 px-1 rounded-sm">npm install</span> first!
    <br/><br/>
    <br/>
    Output:
    <br/><br/>
    <img
      src="/example-component.png"
      class="w-full"
      border="rounded-lg"
      title="folder"
      alt="folder"
    />
  </div>
</div>

<div class="p-1  bg-gradient-to-r from-yellow-500 via-red-500 to-purple-500 absolute bottom-0 right-0 left-0"></div>

---

<span class="text-2xl font-bold">ESM vs CJS vs IIFE</span>

<div class="grid grid-cols-3 gap-2">
  <div>
    <span class="block text-xl font-bold">ESM</span>
    <span class="text-sm">
    Keep the bundle as an ES module file. Suitable for other bundlers and inclusion as a  tag in modern browsers (alias: esm, module).
    </span>
    <ul class="text-sm">
      <li>It can only be placed at the top of a file</li>
      <li>The export directive, on the other hand, can be used to explicitly make items public</li>
    </ul>
  </div>
  <div>
    <span class="block text-xl font-bold">CJS</span>
    <span class="text-sm block">
    Suitable for Node and other bundlers (alias: commonjs).
    </span>
    <ul class="text-sm">
      <li>It is widely used on the server side</li>
      <li>Were designed with server development in mind</li>
      <li>Cannot be used on the browser side unless it is packaged with a transpiler</li>
      <li>Can be recognized by the use of the require() function and module.exports</li>
    </ul>
  </div>
  <div>
    <span class="block text-xl font-bold">IIFE</span>
    <span class="text-sm">
    A self-executing function suitable for inclusion in a script tag. If you want to create a bundle for your application, you probably want to use this.
    </span>
    <ul class="text-sm">
      <li>We can use this format to create a bundle for an application</li>
      <li>It helps us to put things into namespaces to avoid variable collisions and keep code private.</li>
    </ul>
  </div>
</div>

<div class="p-1  bg-gradient-to-r from-yellow-500 via-red-500 to-purple-500 absolute bottom-0 right-0 left-0"></div>

---

<span class="text-gradient-red text-2xl font-bold">2.0</span> <span class="text-2xl font-bold">Let’s start with creating icon wrapper component</span>

<div class="flex">
<div class="w-1/2">

```ts
<template>
  <component :is="iconComponent" role="img" />
</template>
```

```ts
props: {
  icon: {
    type: String,
    required: true,
  },
  hasFill: {
    type: Boolean,
    default: true,
  },
  growByHeight: {
    type: Boolean,
    default: true,
  },
},
```

</div>
  <div class="w-1/2 ml-4">
    <ul class="text-base">
      <li>Icon string prop to pass the .svg filename to import</li>
      <li>hasFill boolean prop which tells the component if fill property will be used to change the color of the svg element, default is false i.e. no fill</li>
      <li>growByHeight boolean prop to determine to use height or width to scale relative to the font-size, default is true i.e. use height</li>
    </ul>
    <span class="text-base">Add fill: currentColor so it will match text color</span>

```css
<style scoped>
.svg-class {
  display: inline-flex;
  fill: currentColor;
}
</style>
```

  </div>
</div>
<div class="p-1  bg-gradient-to-r from-yellow-500 via-red-500 to-purple-500 absolute bottom-0 right-0 left-0"></div>

---

<span class="text-gradient-red text-2xl font-bold">2.1</span> <span class="text-2xl font-bold">Add computed property to get the icon</span>

<div class="flex">
  <div>

```js{all|5,7|4}
computed: {
  iconComponent() {
    let component;
    if (process.env.NODE_ENV === 'production') {
      component = () => import(`../src/assets/icons/${this.icon}`);
    } else {
      component = () => import(`@/assets/icons/${this.icon}`);
    }
    return component;
  },
},
```

  </div>
</div>
<arrow v-click="1" x1="610" y1="350" x2="500" y2="250" color="#564" width="3" arrowSize="1" />
<span v-click="1" class="absolute right-40 top-88 text-green-300 text-xl">
  Using lazy import to import icon component
</span>

<arrow v-click="2" x1="610" y1="150" x2="500" y2="170" color="#564" width="3" arrowSize="1" />
<span v-click="2" class="absolute right-30 top-24 text-green-300 text-xl w-60">
  If in production mode we use '../' I still don't know why, but it works!
</span>
<div class="p-1  bg-gradient-to-r from-yellow-500 via-red-500 to-purple-500 absolute bottom-0 right-0 left-0"></div>

---

<span class="text-gradient-red text-xl font-bold">2.2</span> <span class="text-2xl font-bold">Add Function to properly convert svg on update lifecycle</span>

<div class="flex">
  <div class="text-base -mt-4">

```js
updated() {
    if (this.$el.firstElementChild && this.$el.nodeName === 'svg') {
      const svgElement = this.$el;
      // use `viewBox` attribute to get the svg's inherent width and height
      const viewBox = svgElement.getAttribute('viewBox').split(' ').map((n) => Number(n));
      const widthToHeight = (viewBox[2] / viewBox[3]).toFixed(2);
      if (this.hasFill) {
        // recursively remove all fill attribute of element and its nested children
        recursivelyRemoveFill(svgElement);
      }
      // set width and height relative to font size
      // if growByHeight is true, height set to 1em else width set to 1em
      // and remaining is calculated based on widthToHeight ratio
      if (this.growByHeight) {
        svgElement.setAttribute('height', '1em');
        svgElement.setAttribute('width', `${widthToHeight}em`);
      } else {
        svgElement.setAttribute('width', '1em');
        svgElement.setAttribute('height', `${1 / widthToHeight}em`);
      }
      svgElement.classList.add('svg-class');
    }
},
```

  </div>
</div>
<div class="p-1  bg-gradient-to-r from-yellow-500 via-red-500 to-purple-500 absolute bottom-0 right-0 left-0"></div>

---

<span class="text-gradient-red text-2xl font-bold">2.3</span> <span class="text-2xl font-bold">Add recursivelyRemoveFill function</span>

<div class="flex">
<div class="w-1/2">

```ts
function recursivelyRemoveFill(el) {
  if (!el) return;
  el.removeAttribute('fill');
  [].forEach.call(el.children, (child) => {
    recursivelyRemoveFill(child);
  });
}
```

<span>We are trying to clear fill attribute from our svg</span>

</div>
<div class="w-90 ml-8">
  <span class="block mb-2 mt-30">Convert our svg to vue components, then place our svg icons to folder bellow</span>
  <img
    src="/icons-folder.png"
    class="w-90"
    border="rounded-lg"
    title="folder"
    alt="folder"
  />
  <span class="block mt-2 text-xs">I will give you script to automate that task in bonus <noto-partying-face class="inline"/> </span>
</div>
</div>
<arrow x1="649" y1="100" x2="650" y2="190" color="#ef4444" width="3" arrowSize="1" />
<div class="p-1  bg-gradient-to-r from-yellow-500 via-red-500 to-purple-500 absolute bottom-0 right-0 left-0"></div>

---

<span class="text-gradient-red text-2xl font-bold">3.0</span> <span class="text-2xl font-bold">Test our component</span>

<div class="flex">
<div class="w-1/2">
<span class="text-sm">Add our component in index.js so we can import</span>

```ts
// index.js
export { default as OurIcon } from './our-icon.vue';
```

</div>
</div>

<div class="flex my-2">
<div class="w-1/2">
<span class="text-sm">We can use it globally</span>

```ts
// dev/server.js
import MyIconPack from '@/entry.esm';
Vue.use(MyIconPack);
```

</div>
<span class="mx-5 self-center">OR</span>
<div class="w-1/2">
<span class="text-sm">We can use it local in our component</span>

```ts
// dev/server.js
import { OurIcon } from '@/entry.esm';
export default Vue.extend({
  name: 'ServeDev',
  components: {
    OurIcon,
  },
});
```

</div>
</div>
<span>Usage in our component</span>
<div class="flex mt-2">
<div>

```html
<template>
  <div id="app">
    <our-icon icon="monster" style="color:#ef4444; font-size:10em" />
  </div>
</template>
```

</div>
<div class="ml-3">

- Run `npm run serve`
- Open in [http://localhost:8080/](http://localhost:8080/)
- See the result

</div>
</div>

<div class="p-1  bg-gradient-to-r from-yellow-500 via-red-500 to-purple-500 absolute bottom-0 right-0 left-0"></div>

---

<div class="absolute top-1/2 left-1/2 transform-gpu -translate-x-1/2 -translate-y-1/2">
  <span class="text-center block text-5xl leading-loose">
    Let's <emojione-v1:passenger-ship class="inline"/> it...
  </span>
</div>
<div class="p-1  bg-gradient-to-r from-yellow-500 via-red-500 to-purple-500 absolute bottom-0 right-0 left-0"></div>

---

<span class="text-gradient-red text-2xl font-bold">4.0</span> <span class="text-2xl font-bold">Publish it Locally</span>

<div class="flex">
  <div class="w-1/2">
    <span class="leading-loose">If we want to just use our package independently without publish it on npm so we can use <span class="bg-gray-700 px-1 rounded-sm">npm pack</span>. It will convert our package to ~.tgz so we can share it later to our team</span>
    <img
      src="/npm-pack.png"
      class="w-90 mt-2"
      border="rounded-lg"
      title="npm pack"
      alt="npm pack"
    />
    
Read more about [npm-pack](https://docs.npmjs.com/cli/v6/commands/npm-pack)

  </div>
  <div class="ml-4 w-1/2">
    <ol>
      <li>First run command <span class="bg-gray-700 px-1 rounded-sm">npm run build</span></li>
      <li>Then run command <span class="bg-gray-700 px-1 rounded-sm">npm pack</span></li>
    </ol>
    <span>Result</span>
    <img
      src="/result-npm-pack.png"
      class="w-60 mt-2"
      border="rounded-lg"
      title="npm pack"
      alt="npm pack"
    />
    <span class="block mt-4 mb-3">Usage</span>
    <span class="bg-gray-700 px-1 rounded-sm">npm i my-icon-pack-1.0.0.tgz</span>
  </div>
</div>

<div class="p-1  bg-gradient-to-r from-yellow-500 via-red-500 to-purple-500 absolute bottom-0 right-0 left-0"></div>

---

<span class="text-gradient-red text-2xl font-bold">4.1</span> <span class="text-2xl font-bold">Publish publicly</span>

`npm publish`

<img
  src="/publish.png"
  class="h-80"
  title="NPM publish"
  alt="NPM publish"
/>

<div class="p-1  bg-gradient-to-r from-yellow-500 via-red-500 to-purple-500 absolute bottom-0 right-0 left-0"></div>

---

<span class="text-gradient-red text-2xl font-bold">5.0</span> <span class="text-2xl font-bold">Check on npm registry</span>

You can check on [npm](https://www.npmjs.com/)

<img
  src="/registry.png"
  class="h-80"
  title="NPM registry"
  alt="NPM registry"
/>

[https://www.npmjs.com/package/my-icon-pack](https://www.npmjs.com/package/my-icon-pack)

<div class="p-1  bg-gradient-to-r from-yellow-500 via-red-500 to-purple-500 absolute bottom-0 right-0 left-0"></div>

---

<div class="absolute top-1/2 left-1/2 transform-gpu -translate-x-1/2 -translate-y-1/2">
  <span class="text-center block text-5xl leading-loose">
    There is more <flat-color-icons:idea  class="inline" />
  </span>
</div>
<div class="p-1  bg-gradient-to-r from-yellow-500 via-red-500 to-purple-500 absolute bottom-0 right-0 left-0"></div>

---

<span class="text-xl font-bold">Tips, you can automate convert svg to vue component automatically</span>

<div class="flex -mt-3">
<div class="w-200">

```js
const fs = require('fs');
const path = require('path');

fs.readdir('./svg/', function (err, files) {
  if (err) {
    return console.log('Unable to scan directory: ' + err);
  }
  files.forEach(async function (file) {
    const name1 = path.basename(file);
    const ext1 = path.extname(file);
    const nameWithoutExt1 = path.basename(name1, ext1);
    if (path.extname(file) === '.svg') {
      const svg = fs.readFileSync(`./svg/${file}`, 'utf8');
      fs.writeFile(
        `./icons/${nameWithoutExt1}.vue`,
        `<template>${svg}</template>`,
        function (err) {
          if (err) return console.log(err);
          console.log(`${file} > ${nameWithoutExt1}.vue`);
        }
      );
    }
  });
});
```

</div>
<div class="w-80 ml-2 self-center">
  <span class="block mb-2 font-bold">Result</span>
  <img
    src="/compile.png"
    class="w-50"
    title="compile assets"
    alt="compile assets"
  />
  <img
    src="/magic.gif"
    class="w-50 mt-2"
    title="Magic meme"
    alt="Magic meme"
  />
</div>
</div>

<div class="p-1  bg-gradient-to-r from-yellow-500 via-red-500 to-purple-500 absolute bottom-0 right-0 left-0"></div>

---

# Thanks, Any feedback would be appreciated

<div class="flex w-sm my-10 items-center">
  <img src="/contact/lucky.jpg" class="h-20 rounded-full shadow-2xl">
  <div class="ml-5">
    <span class="block mb-2">Lucky DS</span>
    <span class="block mb-2">Fullstack Javascript Engineer</span>
    <a href="tel:085156501865" class="text-xs">085156501865</a>
  </div>
</div>

### Tech Stack for this presentation

<div border="rounded" class="bg-white mt-2">
  <div class="flex justify-around p-5">
    <img src="/contact/vue-logo.png" alt="vue" class="h-20 mx-2" title="vue"/>
    <img src="/contact/slide_dev.png" alt="slidev" class="h-20 mx-2 " title="slidev"/>
    <img src="/contact/cloudfare.png" alt="cloudfare" class="h-20 mx-2" title="cloudfare"/>
    <img src="/contact/github.png" alt="github" class="h-20 mx-2" title="github"/>
    <img src="/contact/vite.svg" alt="vite" class="h-20 mx-2" title="vite"/>
  </div>
</div>
<div class="p-1  bg-gradient-to-r from-yellow-500 via-red-500 to-purple-500 absolute bottom-0 right-0 left-0"></div>
```
