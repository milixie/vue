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

组件名称不能使用驼峰式写法，这样会报错，需要使用`-`中划线
```
Vue.component('my-message', {});
```
组件中使用`slot`这个插口，才可以在组件使用的时候继续在组件中添加内容

```
Vue.component('my-com', {
  template: '<div><p>标题</p><slot>这部分不会显示的，如果在组件中有内容会显示出来的，如果没有这个 slot 插入的话，你在组件中写的内容不会显示出来</slot></div>'
});

<div>
  <my-com>
    <p>这里是新建的内容，会显示出来的</p>
  </my-com>
</div>

```

多个slot 使用`name`这个属性去标识
```
 Vue.component('my-slot', {
    template: `
              <div>
              <header>
              <slot name="header">这里是标题</slot>
              </header>
              <div class="content">
              <slot>默认的 slot </slot>
              </div>
              <footer>
              <slot name="footer">这里是底部</slot>
              </footer>
              </div>
`
  });
  
//  使用
  <my-slot>
			<h1 slot="header">Title</h1>
			<p>content 1</p>
			<p>content 2</p>
			<p>content 3</p>
			<div slot="footer">bottom</div>
		</my-slot>

```


