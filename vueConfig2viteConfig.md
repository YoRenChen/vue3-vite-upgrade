# 从 webapck 到 vite 的转换
## 前言
本文是项目中的一部分，主要阐述在本项目中把 webpack 改成 vite 的过程内容。
但由于使用的VueCli，所以只是直接修改`vue.config.js`成为`vite.config.ts`。
## 前期准备
### 包管理
```
改版前
# package.json
"dependencies": {
  "vue": "^2.6.11",
  "vue-class-component": "^7.2.3",
  "vue-property-decorator": "^8.4.2",
  ...
},
"devDependencies": {
  "@vue/cli-service": "~4.5.0",
  "vue-template-compiler": "^2.6.11"
  ...
}
```
## 从 webpack.config.ts 到 vite.config.ts
### 环境变量的改变
## vite 兼容 vue2.0
