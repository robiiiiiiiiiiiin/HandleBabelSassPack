# HandleBabelSassPack

(Sorry, I didn't find a better name)

HandleBabelSassPack is a frontend developement environment setup using Webpack, Babel, Sass and Handlebars.

## Installation

Clone the repository, then run `npm install`

Then you should change the name, version, description, repository and author in package.json

## Usage

### HTML / Handlebars

You can use handlebars normally using `.hbs` extension.

On top of that, this configuration uses [handlebars-webpack-plugin](https://github.com/sagold/handlebars-webpack-plugin). This lets you split your html files into multiple files or templates using handlebars' partials, and it will be rendered at Webpack's build.

every `.hbs` file under `src/html` directory will be compiled separately into `dist/samePath/sameName.html`.

The `.hbs` files under `src/partials` can be imported into `.hbs` files as partials.

### CSS / Sass

Every `.scss`, `.sass` or `.css` files can be imported into `src/app.js`. Those files will be compiled and bundled into `dist/css/bundle.css`

### Javascript

`src/app.js` will be bundled and "Babelised" into `dist/js/bundle.js`. Therefore, you should put your JavaScript into `src/js` and import it into `src/app.js`.

### Pass data to handlebars template/partial

You can pass data to a partial like so:
```
{{> pathto/myPartial key=value key2=value}}
```

Or you can pass data using a `.json` file.
To do so, you must add your json file's path into webpack.config.js like so
```
data: require("./src/data/myData.json"),
data: path.join(__dirname, "src/data/myData.json"),
```
Then, you can pass this json file into your partial like that
```
{{> partials/myPartial data=myData}}
```

### NPM scripts

Use `npm run watch` to compile everything on the fly

Use `npm run preview` to run a live-server auto-refreshing on every save

Use `npm run build` to build your app for production
