# Introduction to Webpack
Here I would share my understanding according to the [webpack guide](https://webpack.js.org/guides/) . And by the way point out those points that our project touches.

## What is Webpack
A JS **Static** Module bundler. 
1. Bundle dynamically by dependency graph
2. Bundle static modules

* An NPM package(so it’s based on Node.js)
* Not a task runner(e.g. Grunt, Gulp, npm scripts)


## Why do we use Webpack
1. Modulization need while develop. 

    **JS**
	* CommonJS — require(‘.a.js’)
	* AMD — requirejs
	* ES6 — import

    **CSS**
	* SCSS
	* LESS

    **Images, fonts, .etc**

2. After modulized, project files are not runnable by itself.
	* Needs translation, bundling

3. It’s the result of [evolution](http://webpack.wuhaolin.cn/1%E5%85%A5%E9%97%A8/1-2%E5%B8%B8%E8%A7%81%E7%9A%84%E6%9E%84%E5%BB%BA%E5%B7%A5%E5%85%B7%E5%8F%8A%E5%AF%B9%E6%AF%94.html)

	1. NPM Script 
		* Out of the box. 
		* Too simple, not many hooks available.
	2. Grunt
		* Tasks + dependency
		* Flexible, Reusable plugins that encapsulate common tasks
		* Needs lots of config
	3. Gulp
		* Workflow
		* task, run, watch, src, dest
		* Stronger than Grunt, but also needs lots of config to run.
	4. Webpack
		* Everything is a module.
		* Good at handling modulized projects; Plugins; Active community;
		* Cons: could only adapt to modulized projects.


## How to use Web pack
1. [Ways to config](https://webpack.js.org/guides/getting-started/#creating-a-bundle)
	* npx webpack --param
	* npx webpack --config webpack.config.js
	* npm scripts

2. Core concepts —Take config file from our project as an example
	* entry
	What we use as the roots of dependency graph

	* output
	Define where the bundled files would go to
	publicPath: When insert bundled files to index.html, the prefix to add before filename. —change it to watch the effect .
	* loaders — Asset Management: CSS/SCSS, Images/Font files, data files

	* plugins — Output Management and others, more powerful than loaders.
		
		HtmlWebpackPlugin
		1. Add bundles. 
		2. Replace variables
		3. Generate new index.html

		CleanWebpackPlugin -- Clean up before build


## Good Practices
### Output
1. Lazy-load
2. Code splitting — Optimise load time.
		* Entry Points
		* Prevent Duplication — CommonsChunkPlugin 
		* Dynamic  Imports
3. Caching
		* hash
4. Tree-shaking — UglifyJSPlugin
5. Source map

### Develop
1. DevServer + Hot Module Replacement
2. Shimming  
	* Provide package as global
	* Browser polyfill
3. Babel — to support ES2015
4. PWA support, offline web APP

### Modulize webpack configs
1. webpack-merge — divide config to common, develop, production.
