# Webpack-Bilor-plate

Step 1:  create package.json
Using npm init command in your terminal 
>npm init

Step 2: Add details for package.json
After hitting command it will ask following details needs to be filled, if you want to leave any field leave empty just hit enter.

This utility will walk you through creating a package.json file.

Step 3: Install react
Now this is time to install react. Basically react has two parts such as react and react-dom. So now place below command in your terminal.

npm i react react-dom

or

npm install react react-dom


Step 4: Install webpack
npm i --save-dev webpack webpack-dev-server webpack-cli


Step 5: Install babel
npm i --save-dev babel-core babel-loader babel-preset-env babel-preset-react html-webpack-plugin


Step 6: Setup webpack config
1.	First create webpack.config.js in your root folder.
2.	Then create path and HtmlWebpackPlugin. 
3.	Now create module with object here we are using former syntax module.exports = {} 
4.	Add entry point on that object. It should be in our “./src/index.js” so create “src” folder under the root package and create index.js under src. 
5.	Add output. Which has our compile code has to go in one JavaScript file its goanna be a bundled file. Basically this is object in syntax.  So we need specify two things path to join current directory and the output folder. And Specify the file name we can give name here “example: bundle.js”.
6.	Next we are goanna add loader under the module object and in which under the rules array. Basically it is a regular expression put it in a “test” key.  And make sure to exclude the node_modules same. And added babel-loader inside the “use” object.
7.	Html webpack plugin basically create an index.html file while build the application to our target folder. For this first we have to create index.html inside the “src”. This plugin that simplifies creation of HTML files to serve your bundles. This can be done by build command. This index.html will add react application.  Here react dom will focus the id.
8.	Now add the basic code inside the html file. Here we no need to worry about to add the bundle.js file inside the script tag webpack will do for us. 
9.	Now add plugins in webpack.config file. Which can be an array pass index.html inside.

webpack.config.js

const path = require('path');
const HtmlWebpackPlugin = require('html-webpack-plugin');

module.exports = {
    entry:'./src/index.js',
    output:{
        path: path.join(__dirname,'/dist'),
        filename: 'bundle.js'
    },
    module:{
        rules:[
            {
                test: /\.js$/,
                exclude: /node_modules/,
                use:{
                    loader: 'babel-loader'
                }
            }
        ]
    },
    plugins:[
        new HtmlWebpackPlugin({
            template:'./src/index.html'
        })
    ]
}

  
10.	In order to use presets remember to install presets to compile ES6 and so on react presets we need to create a file “.babelrc” in the root directory. 

This file has JSON object to include the presets. Here we have to include “presets” as an array, no need to include babel-preset like that just add [“env”,”react”].

{
    "presets": ["env","react"]
}


Step 7: React code
Now in index.js add regular react code for Main dom. We are using babel so remember to write es6 syntax on it. So now create folder “components” inside the “src”, then create a file “App.js” 


Step 8: Add start script 
In package.json under scripts{ } add the key word “start” and place dev server “webpack-dev-server” options as follows
	--mode development   - stands for development or production….
	--open - stands for open automatically when we run the command.
	--hot - stands for hot reloading when we save something it will reload the page
  
  
Step 9: start server
Now type the command to start the dev server in your terminal.
> npm start




