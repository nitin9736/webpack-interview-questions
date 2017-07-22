# Webpack interview questions (EARLY DRAFT VERSION)


## Table of Contents

* [Concepts](#concepts)
* [Config file](#config-file)
* [Loaders](#loaders)
* [Plugins](#plugins)
* [Debugging](#debugging)
* [Optimization](#optimization)
* [Migration](#migration)
* [Advanced-questions](#advanced-questions)


#### Concepts
* What is webpack?
* What is the main difference between webpack and other build tools like gulp or grunt?
* What is bundle in webpack?
* In which environment webpack works?

#### Config file
* What is the format of webpack's config file.
* What is `entry` point?
* Where loaders should be defined?

#### Loaders
* What is loader in webpack
* Do loaders work in synchronous or asynchronous way?
* Is it possible to use multiple loaders in `rules` single object?
* Name loaders you think are very important and helpful
 
#### Plugins
* Describe plugin in webpack
* What is difference between loader and plugin
* Name plugins you think are very important and helpful

#### Debugging

#### Optimization
* Briefly describe long-term caching and how to achieve it using webpack?
* What is difference between
  
    ```javascript
       ...
       output: {
        filename: "[name].[hash].js"
       }
       ...
   ```
        and
   ```javascript
      ...
       output: {
        filename: "[name].[chunkhash].js"
       }
       ...
    ```
* Describe CommonsChunkPlugin
* What analyzes tools you use to inspect your webpack bundle?

#### Migration

#### Advanced questions


## Answers

#### Concepts answers
* What is webpack? 
  
  A: webpack is a module bundler for javascript applications. Webpack recursively builds every module in your application, then packages all of those modules into a small number of bundles.
  
* What is the main difference between webpack and other build tools like gulp or grunt?

 A:

* What is bundle in webpack?

 A:

* In which environment webpack works?

 A: node.js
 
#### Config file answers
* What is the format of webpack's config file.
  
  A: webpack's config file is javascript file in commonjs module pattern.

* What is `entry` point?
* Where loaders should be defined?

  A: in the rules property
  
#### Loaders answers
* What is loader in webpack
  
  A: Loaders are transformations that are applied on the source code of a module. webpack supports modules written in a variety of languages and preprocessors, via loaders. Loaders describe to webpack how to process non-javaScript modules and include these dependencies into your bundles.
  
* Do loaders work in synchronous or asynchronous way?
  
  A: Both. Loaders can work synchronous or asynchronous.

* Is it possible to use multiple loaders in `rules` single object?
  
  A: Yes, its possible to chain loaders.

* Name loaders you think are very important and helpful

  A: raw-loader, url-loader, html-loader, file-loader, style-loader, css-loader, script-loader, babel-loader, loaders for typescript, coffescript, less, sass, pug, markdown, etc.
 
#### Plugins answers
* Describe plugin in webpack
* What is difference between loader and plugin
* Name plugins you think are very important and helpful
  A: CommonsChunkPlugin, DefinePlugin, HtmlWebpackPlugin, ExtractTextWebpackPlugin, CompressionWebpackPlugin
  
#### Debugging answers

#### Optimization answers
* Briefly describe long-term caching and how to achieve it using webpack?
 
  A:  Browsers should cache static assets to save traffic and users time. But after each change or bugfix, browser have to download newer version of files. The most easy way to achieve this is changing file name. It could be buildId or unique hash in the end of file's name like
    
   ```javascript
       app.js?build=1
       app.js?build=2
    ```  
   or 

    ```javascript
     app.js.2a6c1fee4b5b0d2c9285.js
     app.js.70b594fe8b07bcedaa98.js
     ```
  
    To achieve this using webpack simple configuration should be done
  
  
    ```javascript
      module.exports = {
       ...
       output: {
        filename: "[name].[hash].js"
       }
       ...
      }
    ```

* What is difference between `hash` and `chunkhash`
   
   : [hash] will generate unique hash for each build and use it for all chunks. Replace `[hash]` with `[chunkhash]` to generate unique hashes for each chunk. This is useful when you dont want to re-download vendors (dependencies) file but you have changes in your application code and want to update it.
   
* Describe CommonsChunkPlugin

 A: 
 
* What analyzes tools you use to inspect your webpack bundle?
    
 A: webpack-bundle-analyzer plugin, official webpack analyze tool, webpack visualizer, webpack chart
 
#### Migration answers

#### Advanced questions answers
