
- Fala da história
https://webpack.js.org/
- Fala do porque existe o babel (era 6to5)
https://babeljs.io/
- Mostra convertendo um arquivo React
  - Explica o JSX

## Primeiros passos
- Cria um js
- Criar o MINIMO necessário do webpack
```json
{
  "devDependencies": {
    "webpack": "^5.4.0",
    "webpack-cli": "^4.2.0",
    "webpack-dev-server": "^3.11.0"
  }
}
```


```js
module.exports = {
  entry: './src/index.js',
  output: {
    path: __dirname + '/dist',
    filename: 'bundle.js',
  },
  resolve: {
    extensions: ['.js']
  },
}
```

- Add esse Script: `"build:watch": "webpack --watch --mode production",`

## Avançando no rolê

- Vamos adicionar o suporte pro React!

```json
{
  "react": "^17.0.1",
  "react-dom": "^17.0.1"
}
```

- E agora pro babel
```json
{
  "@babel/core": "^7.12.3",
  "@babel/preset-env": "^7.12.1",
  "@babel/preset-react": "^7.12.5",
  "babel-loader": "^8.2.1",
}
```

```js
const HtmlWebpackPlugin = require('html-webpack-plugin');

module.exports = {
  entry: './src/index.js',
  output: {
    path: __dirname + '/dist',
    filename: 'bundle.js',
  },
  resolve: {
    extensions: ['.js']
  },
  module: {
    rules: [
      {
        test: /\.js$/,
        loader: 'babel-loader',
        exclude: /node_modules/
      },
    ]
  },
  plugins: [
    new HtmlWebpackPlugin({
      template: __dirname + '/src/index.html',
      filename: 'index.html',
      inject: 'body'
    })
  ]
};
```


- Indica meu vídeo
  - Recriando o React


