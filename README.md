# Create React App Manually

The following are the steps to create a react app without using the command `npx create-react-app project-name`.


1. Create folder
	```
	mkdir project-name
	cd project-name
	```

2. Initialise node project and install necesary packages
	```
	npm init -y
	npm i --save-dev webpack webpack-cli webpack-dev-server
	npm i react react-dom
	npm i --save-dev babel-loader @babel/preset-env @babel/core @babel/plugin-transform-runtime @babel/preset-react babel-eslint @babel/runtime
	```

3. Create babel file
	```
	touch .babelrc
	```
  
4. Edit `.babelrc`
	```
	{
		"presets": ["@babel/preset-env", "@babel/preset-react"],
		"plugins": ["@babel/plugin-transform-runtime"]
	}
	```
 
5. Create webpack file
	```
	touch webpack.config.js
	```
  
6. Edit `webpack.config.js`
	```
	const path = require("path");
	
	module.exports = {
		mode: "development",
		entry: "./index.js",
		output: {
			path: path.resolve(__dirname, "dist"),
			filename: "main.js",
		},
		target: "web",
		devServer: {
			port: "3000",
			static: ["./public"],
			open: true,
			hot: true,
			liveReload: true,
		},
		resolve: {
			extensions: [".js", ".jsx", ".json", ".ts", ".tsx"],
		},
		module: {
			rules: [
				{
					test: /\.(js|jsx)$/,
					exclude: /node_modules/,
					use: "babel-loader",
				},
			],
		},
	};
	```

7. Modify scripts in `package.json`
	```
	"scripts": {
		"test": "echo \"Error: no test specified\" && exit 1",
		"start": "webpack-dev-server .",
		"build": "Webpack ."
	},
	```

8. Create public directory
	```
	mkdir public
	cd public
	touch index.html
	cd ..
	```
  
9. Edit `public/index.html`
	```
	<html lang="en">
		<head>
			<meta charset="UTF-8" />
			<meta http-equiv="X-UA-Compatible" content="IE=edge" />
			<meta name="viewport" content="width=device-width, initial-scale=1.0" />
			<title>React</title>
		</head>
		
		<body>
			<div id="root"></div>
			<script src="main.js"></script>
		</body>
	</html>
	```

10. Create source directory
	```
	mkdir src
	cd src
	touch App.js
	cd ..
	```
  
11. Edit src/App.js
	```
	import React from "react";  
	
	const App = () => {
		return (
			<div>
				<h1>Hello Folks!</h1>
			</div>
		);
	};
	
	export default App;
	```

12. Create index file
	```
	touch index.js
	```
  
13. Edit index.js
	```
	import React from "react";
	import ReactDOM from "react-dom";
	import App from "./src/App";
	
	ReactDOM.render(<App />, document.querySelector("#root"));
	```

14. Run react app
	```
	npm run build
	npm start
	```

