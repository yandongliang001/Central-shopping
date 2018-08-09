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
公共组件中涉及到用户登陆信息和登陆用户的购物车信息等，其中用户是否登陆用Top.vue中的 myLogin 变量判断，登陆了，该登陆用户购物车中是否有商品用 myShop 变量判断。初始都为false，无用户登陆，购物车无商品。
