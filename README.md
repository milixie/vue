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



### vue父子组件之间的通信

方法一：使用外部的状态管理模式：例如 vuex，通过 mutations 去更新状态值，实现通信

方法二：使用 `$emit` and `v-on` 去实现通信

例如：
```
//这是子组件 test，使用 $emit 去触发事件
<div @click="updateStatus">更新状态</div>

methods: {
  updateStatus() {
    this.$emit('update', 1);
  }
}

//这是父组件 app，使用 v-on 去监听事件
<test v-on:update="updateCurrentStatus">xxx</test>

methods: {
  updateCurrentStatus(val) {
    console.log(val); //1
  }
}

```

### vue全局配置

```
vue.config
```

### 全局 API

```
Vue.extend(options);
是一个类继承方法，用来生成一个 Vue 的子类构造函数

Vue.component('componentName', options);
注册组件的方法，在传递 options 的时候，它会在内部调用 Vue.extend()

Vue.nextTick([cb, context]);
在 DOM 更新循环结束之后执行延迟回调，在更新数据之后使用这个方法，获取更新后的 DOM

Vue.set(target, key, value);
设置对象的属性
const obj = {};
Vue.set(obj, 'name', 'milixie');
console.log(obj); // {name: 'milixie'}

Vue.delete(target, key);
删除对象的属性
Vue.delete(obj, 'name');
console.log(obj); //{}

Vue.directive(id, [definition]);
注册或者获取全局指令
Vue.directive('power', function() {
  bind: function(){
    console.log('test directive')
  },
  inserted: function () {},
  update: function () {},
  componentUpdated: function () {},
  unbind: function () {}
});

返回已经注册的指令
const my_power = Vue.directive('power');

在页面中
<div v-power></div>
在控制台会打印出 test directive

Vue.filter(id, [definition]);
注册或者获取全局过滤器
Vue.filter('cash', function(value){
  return (value/100).toFixed(2);
});
使用：
<div>{{price | cash}}</div>

Vue.use(plugin);
使用插件
import plugin from '../vue/plugin';
Vue.use(plugin);

- Vue.mixin(mixin) 
全局混合（没理解清晰）

- Vue.compile(template)
在 render 函数中编译模板字符串(没理解清晰)

Vue.version 
vue 的版本号
console.log(Vue.version);

```

### 选项 | 数据
```

- data:Vue 实例数据对象
当一个组件被定义， data 必须声明为返回一个初始数据对象的函数，每次创建一个新实例后，能够调用 data 函数返回初始数据的一个全新副本数据对象

可以通过 JSON.parse(JSON.stringify(vm.$data))将源数据进行深拷贝

注意：
==
不应该对data 使用箭头函数，因为箭头函数绑定了父级作用域的上下文

- props
接收来自父组件的数据

父组件中：
<coupon :show="is_show"></coupon>

子组件 coupon中
props: ['show']

- propsData (理解不清晰)
只用于 new 创建的实例

const vm = new Cm({
    propsData: {msg: 'hhhh'}
});

- computed
计算属性，计算的结果会被缓存，如果里面的值没有变化的话就不会重新计算，只有当里面的值动态变化的时候才会重新计算

- methods
方法，不可以使用箭头函数，理由是箭头函数绑定了父级作用域的上下文，所以 this 将不会按照期望指向 Vue 实例

- watch
一个对象，键是需要观察的表达式，值是对应的回调
watch: {
  length(){
    len = this.list.length;
  }
}

```

### 选项 | DOM

```
el:
在实例挂载vm.$mount()后可以访问，vm.$el

template | render | renderError

```

### 选项 | 生命周期

![生命周期图](https://cn.vuejs.org/images/lifecycle.png）
















