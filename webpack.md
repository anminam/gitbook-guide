---
description: 웹팩맨
---

# Webpack

## Webpack 이란?

* [Webpack](https://webpack.js.org/)은 의존 관계에 있는 모듈들을 하나의 자바스크립트 파일로 번들링하는 모듈 번들러이다
* Webpack을 사용하면 의존 모듈이 하나의 파일로 번들링되므로 별도의 모듈 로더가 필요없다.



## Webpack 설치

Becoming a super hero is a fairly straight forward process:

```bash
# Webpack V4는 webpack-cli를 요구한다
$ npm install --save-dev webpack webpack-cli
```

Once you're strong enough, save the world:

{% code title="hello.sh" %}
```bash
# Ain't no code for that yet, sorry
echo 'You got to trust me on this, I saved the world'
```
{% endcode %}

## babel-loader

전시간에 만든것을 로드한다

```bash
# babel-loader 설치
$ npm install --save-dev babel-loader
```



## webpack.config.js

```javascript
const path = require('path');

module.exports = {
  // enntry file
  entry: './src/js/main.js',
  // 컴파일 + 번들링된 js 파일이 저장될 경로와 이름 지정
  output: {
    path: path.resolve(__dirname, 'dist/js'),
    filename: 'bundle.js'
  },
  module: {
    rules: [
      {
        test: /\.js$/,
        include: [
          path.resolve(__dirname, 'src/js')
        ],
        exclude: /node_modules/,
        use: {
          loader: 'babel-loader',
          options: {
            presets: ['@babel/preset-env'],
            plugins: ['@babel/plugin-proposal-class-properties']
          }
        }
      }
    ]
  },
  devtool: 'source-map',
  // https://webpack.js.org/concepts/mode/#mode-development
  mode: 'development'
};
```

## 실행

```bash
$ npm run build
```



## 참조사이트

{% embed url="https://poiemaweb.com/es6-babel-webpack-2" %}



