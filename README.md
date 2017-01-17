vue 学习
=======
# vue-pro1

> A Vue.js project

## Build Setup

``` bash
# install dependencies
npm install

# serve with hot reload at localhost:8080
npm run dev

# build for production with minification
npm run build

# run unit tests
npm run unit

# run e2e tests
npm run e2e

# run all tests
npm test
```

For detailed explanation on how things work, checkout the [guide](http://vuejs-templates.github.io/webpack/) and [docs for vue-loader](http://vuejs.github.io/vue-loader).


## vue 组件

组件里面的数据data必须是一个函数，函数里面再返回具体的数据
```
const data = {
	  title: 'this is nav'
	};

	// 全局注册组件
  Vue.component('wrap-head', {
    template: `<header><p>{{ title }}</p><ul><li><a href="">Home</a></li><li><a href="">About</a></li><li><a href="">Login</a></li></ul></header>`,
		data: function () {
      return data;
		}
  });

```
组件中的名称不能使用 `content`，使用的话会报错
