---
description: 바벨맨
---

# Babel

## Babel CLI 설치

```bash
# 프로젝트 폴더 생성
$ mkdir foo-project && cd foo-project

# package.json 생성
$ npm init -y

# babel-core, babel-cli 설치
$ npm install --save-dev @babel/core @babel/cli
```

## .babelrc 설정 

```bash
# env preset 설치
$ npm install --save-dev @babel/preset-env

```

### .babelrc 생성

루트에 **.babelrc** 파일을 생성하고 아래와 같이 작성한다

```javascript
{
  "presets": ["@babel/preset-env"]
}
```

## build 추가

```javascript
{
  "name": "es6-project",
  "version": "1.0.0",
  "scripts": {
    "build": "babel src/js -w -d dist/js"
  },
  "devDependencies": {
    "@babel/cli": "^7.7.0",
    "@babel/core": "^7.7.2",
    "@babel/preset-env": "^7.7.1"
  }
}
```

* -w 타깃 폴더에 있는 모든 파일들의 변경을 감지하여 자동으로 트랜스파일한다. \(--watch 옵션의 축약형\)
* -d 트랜스파일링된 결과물이 저장될 폴더를 지정한다. \(--out-dir 옵션의 축약형\)

## 실행

```bash
$ npm run build
```

## 

## 참조사이트

{% embed url="https://poiemaweb.com/es6-babel-webpack-1" %}









