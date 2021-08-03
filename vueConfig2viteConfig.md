# 从 webapck 到 vite 的转换
## 前言
本文是项目中的一部分，主要阐述在本项目中把 webpack 改成 vite 的过程内容。
但由于使用的VueCli，所以只是直接修改`vue.config.js`成为`vite.config.js`。
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

改版前
# package.json
"devDependencies": {
- "vue-template-compiler": "^2.6.11"
+ "vite": "^2.3.7",
+ "vite-plugin-compression": "^0.2.5",
+ "vite-plugin-style-import": "^1.0.0",
+ "vite-plugin-vue2": "^1.6.2"
  ...
}
```
## 从 vue.config.js 到 vite.config.js
### 环境变量引用的改变
```
# webpack
process.env.NODE_ENV === 'production'

# vite
import.meta.env.NODE_ENV === 'production'
```
### 引用源码资源
```
# webapck
@import '~ant-design-vue/es/style/themes/default.less';

# vite 使用相对路径
@import '../../../node_modules/ant-design-vue/es/style/themes/default.less';
```
### 忽略第三方插件
```
# webpack
const plugins = [
  new webpack.IgnorePlugin(/^\.\/locale$/, /moment$/),
]

# vite
optimizeDeps.exclude
```
## vite 兼容 vue2.0
## Vite 基本特性
[Vite 文档](https://cn.vitejs.dev/guide/why.html#slow-server-start)
1. EsBulid 预构建依赖
2. 利用 HTTP 头来加速整个页面的重新加载，源码模块使用协商请求(304 Not Modified)， 依赖模块用强缓存(Cache-Control: max-age=)

