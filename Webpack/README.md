## Workflows and Webpack
* Lets the dev write clean and understandable code and then build it ship to a format understandable to the browser.

## The role of Node.js and NPM
* NPM is the node's package manager and it's present in package.json file.
* Package.json has the following structure:
  * dependencies - The actual project dependencies required for prod.
  * devDependencies - Development dependencies like babel, webpack, loaders(CSS Loaders) and configs etc.
* All the dependencies are sent to a folder called node_modules and this need not be shipped at all. Only the package.json file needs to be shipped.
* npm install to download and resolve the dependencies and put in node_modules folder.
* npm also allows you to define some scripts to be run. For example a build script to be defined in package.json and then user can provide the command npm build to execute the script.

## How webpack works: Entry and output
* webpack.config.js file have the entry and output sections.
* Entry section specifies the main.js file
* Output section is related to location and the name of the bundle file.
  ```
  var path = require('path')
  var webpack = require('webpack')
  
  module.exports = {
   entry: './src/main.js'
   output: {
     path: path.resolve(_dirname, './dist'),
     publicpath: '/dist/'
     filename: 'bundle.js'
   },
   //Other props here
  }
  ```
