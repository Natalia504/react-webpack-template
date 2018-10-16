### React Webpack Setup
#### Webpack & Babel
To duplicate a repository without forking it, you can run a special clone command, then mirror-push to the new repository.
1. Create a [new-repo] on GitHub.
2. Create a bare clone of this repository: 
*`git clone --bare https://github.com/Natalia504/react-webpack-template.git`. 
3. Mirror-push to the new repository: 
*`cd react-webpack-template` 
*`git push --mirror https://github.com/user/[NEW-REPO].git`
4. Remove the temporary local repository you created in step 2: 
*`rm -rf react-webpack-template.git`.
5. You now have `react-webpack-template` pushed into your new repo. Now clone the new repo, so you have it locally. 
6. cd into your new repo and install dependencies: *`npm i`

- - - - 
<details>
    <summary>Details</summary>
    <p>

`npm init`  
`npm i --save react react-dom`  
`npm i --save-dev babel-core babel-loader babel-preset-react`  
`npm i --save-dev webpack webpack-dev-server html-webpack-plugin`  

### Configure Webpack
Create *webpack.config.js* in the root of your project.
Webpack needs to know three things:
1. What JavaScript file it should transform (i.e. entry point);
2. Which transformations it should use on that file (i.e. module);
3. Where the new, transformed file should go (i.e. output);

```javascript 
var path = require('path');
var HtmlWebpackPlugin = require('html-webpack-plugin');

module.exports = {
  entry: './src/index.js',
  output: {
    path: path.resolve(__dirname, 'dist'),
    filename: 'index_bundle.js'
  },
  module: {
    rules: [
      { test: /\.(js)$/, exclude: /node_modules/, use: 'babel-loader' },
      { test: /\.css$/, use: [ 'style-loader', 'css-loader' ]}
    ]
  },
  plugins: [
    new HtmlWebpackPlugin({
      template: 'src/index.html'
    })
  ], 
  mode: process.env.NODE_ENV === 'production' ? 'production' : 'development'

};
```
</p>
</details>
