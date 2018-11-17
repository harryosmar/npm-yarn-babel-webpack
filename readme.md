# Usage
1. `git clone git@github.com:harryosmar/npm-yarn-babel-webpack.git`
2. `cd npm-yarn-babel-webpack`
3. `yarn install`
4. `yarn run build`
5. `yarn run dev`


## Step flow of this project creation
1. create `package.json` file is created.
```
yarn init --yes
```

2. Time to install the `dev` dependencies
```
yarn add --dev webpack babel-core@6 babel-loader@7 babel-preset-react babel-preset-es2015 node-sass css-loader sass-loader style-loader
```

3. Install react
```
yarn add react react-dom
```

4. create `webpack.config.js`
- Our entry point is the `src/index.jsx` file
- Let’s set our output directory to be `output` and output filename `bundle.js`
- Now, we need to set up our `loaders`. For files that end with extension `.jsx`, we will use `babel-loader` with `es2015` and react` presets.
- For files that end with extension `.scss`, we will use `sass-loader`, `css-loader`, and `style-loaders`.

5. Now we need to run webpack.
The easiest way to do it is to add it into `package.json`
```
"scripts": {
    "build": "webpack -p"
}
```
The flag `-p` stands for `production`.
Open terminal and type in
```
yarn run build
```
It will create file `output/bundle.js


6. We need hot loading for faster development.
The easiest and the best solution is to use `Webpack Dev Server`.
Add the following to the root of webpack config:
```
devServer: {
   contentBase: './src',
   publicPath: '/output'
}
```
These two lines tell the `webpack dev server`
- to read content from `src` directory
- to serve the `assets` under `/output` URL path.

7. Now, we need to go to terminal and install webpack dev server
```
yarn add --dev webpack-dev-server
```

8. Once webpack `dev server` is installed, let’s add another script to `package.json` to run it. Under `scripts`, add the following:
```
"dev": "webpack-dev-server --hot --inline"
```
Open terminal and type in
```
yarn run dev
```

## links
- https://medium.com/front-end-hacking/what-are-npm-yarn-babel-and-webpack-and-how-to-properly-use-them-d835a758f987