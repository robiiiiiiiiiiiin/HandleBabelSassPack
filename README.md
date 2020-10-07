# HandleBabelSassPack

(Sorry, I didn't find a better name)

HandleBabelSassPack is a pre-maid architecture and configuration to develop using Webpack, Babel, Sass and Handlebars.

The overall is using npm

## Installation

Clone the repository, then run `npm install`

## Usage

### HTML / Handlebars

You can use handlebars normally using `.hbs` extension.

On top of that, this configuration uses [handlebars-webpack-plugin](https://github.com/sagold/handlebars-webpack-plugin). This lets you separate your html files into multiple files using handlebars' partials, and it will be rendered on Webpack's build.

every `.hbs` file directly under `src/` directory will be compiled separately into `dist/sameName.html`.

The `.hbs` files under `src/partials` can be imported into `src/*.hbs` files as partials. You can add one level of directory to `src/partials`, but if you add two levels or more, you'll have to adapt this part of the configuration into `webpack.config.js`

```
// In your .hbs files, you must import partial with only firstParent/filename
// You need to add a line for each folder level
partials: [
path.join(process.cwd(), "src", "partials", "*.hbs"),
path.join(process.cwd(), "src", "partials", "*", "*.hbs")
],
```

### CSS / Sass

Every `.scss`, `.sass` or `.css` files can be imported into `src/app.js`. Those files will be compiled and bundled into `dist/css/bundle.css`

### Javascript

`src/app.js` will be bundled and "Babel'ised" into `dist/js/bundle.js`. Therefore, you should put your JavaScript into `src/js` and import it into `src/app.js`.

### NPM scripts

Use `npm run watch` to compile everything on the fly

Use `npm run preview` to run a live-server auto-refreshing on every save

Use `npm run build` to build your app for production