---
layout: post
title: "Adding SASS/SCSS to your Current Create React App Project without Ejecting"
categories:
  - React
  - Git
  - Mac
tags:
  - Mac
  - Git
  - React
---
I’ve usually used frameworks for CSS and didn’t really worry too much about having SCSS or SASS support for my React projects, but on a recent project of mine, I’ve decided that I’m going to build my own CSS framework and grid for myself, since I wanted some of my own tweaking flexibility. While building my own CSS framework, I’ve had so many redundancies in my CSS that I knew it was time that I just had to port to SCSS.
## Getting Started
The way we’re going to support SCSS is sort of how Webpack picks up our ES6 Javascript using Babel to recreate regular Javascript. We’ll be taking our SCSS files and then recreate regular CSS files that our `index.html` can read.
The way my project tree is structured is the following :
```
project-dir
├── .git
├── .gitignore
├── node_modules
├── package.json
├── public
│   ├── stylesheets
│   │   └── index.css   
│   └── index.html
└── src
    ├── components
    ├── App.js
    └── index.js
```
And I hope you use it as a reference for this blog. We’ll create a new folder for our SCSS files so that their separate from the CSS folder when their built. Let’s create a new `index.scss` file in our new folder with the following :
```
$ mkdir public/scss-stylesheets
$ touch public/scss-stylesheets/index.scss
```
After your tree should now look like this :
```bash
project-dir
├── .git
├── .gitignore
├── node_modules
├── package.json
├── public
│   ├── scss-stylesheets
│   │   └── index.scss   
│   ├── stylesheets
│   │   └── index.css   
│   └── index.html
└── src
    ├── components
    ├── App.js
    └── index.js
```

You’ll also want to install the following npm package:

```bash
$ npm i --save-dev node-sass
```

Then in your `package.json` file located in your project root directory add the following two lines to `scripts`:
```javascript
"script": {
    "build-css": "node-sass public/scss-stylesheets -o public/stylesheets",
    "watch-css": "npm run build-css && node-sass public/scss-stylesheets -o public/stylesheets --watch --recursive",
    ...
}
```

You can change entry path `public/scss-stylesheets` on both `build-css` and `watch-css` to any folder you prefer instead. Same holds true for the output path `public/stylesheets` for the code above. The `build-css` let you build the SCSS files to CSS files once, but if you want your project do this while you code, you run `watch-css` and it’ll reload as you change you SCSS file. You could try this with the following :
```
$ npm run watch-css
```
Now you might be thinking we’re already watching our react project when we run `npm start` and we’d have to then also watch SCSS with `npm run watch-css`. A bit of an annoyance, so why don’t we fix that bit too, so that SCSS is also watched when `npm start` is ran. We’re going to need the following package to be installed :
```
$ npm install --save-dev npm-run-all
```
Then change the following lines from your package.json ( `—` are lines we’re getting rid of while `+` are lines we’re adding) :
```javascript
"scripts": {
     "build-css": "node-sass src/ -o src/",
     "watch-css": "npm run build-css && node-sass src/ -o src/ --watch --recursive",
-    "start": "react-scripts start",
-    "build": "react-scripts build",
+    "start-js": "react-scripts start",
+    "start": "npm-run-all -p watch-css start-js",
+    "build": "npm run build-css && react-scripts build",
     "test": "react-scripts test --env=jsdom",
     "eject": "react-scripts eject"
   }
  ```

Once you’re done with it all you can now just write the following and you should have SCSS support on your project :
```
$ npm start
```

## Bonus : .gitignore

So that we’re not adding redundant code to our git repo, we can add the following folder path to our `.gitignore` :
```
public/stylesheets
```
Hope you liked my posts! I’d love any feedback and follow me more posts.
