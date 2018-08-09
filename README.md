# central-shopping

> A Vue.js project

## Build Setup

``` bash
# install dependencies
npm install

# serve with hot reload at localhost:8080
npm run dev

# build for production with minification
npm run build

# build for production and view the bundle analyzer report
npm run build --report

# run unit tests
npm run unit

# run e2e tests
npm run e2e

# run all tests
npm test
```

For a detailed explanation on how things work, check out the [guide](http://vuejs-templates.github.io/webpack/) and [docs for vue-loader](http://vuejs.github.io/vue-loader).
###  结构
整体结构分为goshopping（购物车组件）、index（首页组件）、list（列表组件）、login（登陆组件）、page（详情组件）、public（公共组件）；
公共组件中涉及到用户登陆信息和登陆用户的购物车信息等，其中用户是否登陆用Top.vue中的 myLogin 变量判断，登陆了，该登陆用户购物车中是否有商品用 myShop 变量判断。初始都为false，无用户登陆，购物车无商品。因为换项目组的原因，这个项目暂时搁置一下。
对top.vue组件的详细说明：因为涉及到用户是否登陆，所以展示的东西都不一样，在top.vue模块中对这块的变化，已经在构建模块的时候充分考虑到了，所以后续再继续写的话，请仔细阅读源码，不用再做额外的更改。
bottom.vue模块可以直接使用，不用考虑是否用户登陆等信息。
qtzz.vue模块打算写底部上面一层，轻松购物、天天低价等这些信息的。
###信息
项目启动直接 npm start。浏览器会自动打开   端口配置为9090
