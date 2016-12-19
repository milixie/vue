<template>
  <div class="mili">
    <h1 v-if="dif">颜色相同</h1>
    <h1 v-else>颜色不同</h1>
    <ul v-if="!dif">
      <li v-for="(lis, i) of lists" v-bind:style="{color: lis.color}">{{ lis.color }} - {{ i }}</li>
    </ul>
    <ul v-else>
      <li v-for="lis in lists" style="color: #000;">{{ lis.color }}</li>
    </ul>
    <div v-if="loginType == 'username'">
      <label>username</label>
      <input type="text" name="" placeholder="please input your username">
    </div>

    <div v-else-if="loginType == 'email'">
      <label>email</label>
      <input type="text" name="" placeholder="please input your email">
    </div>

    <div v-else>
      <label>text</label>
      <input type="text" name="" placeholder="please input text">
    </div>

    <div v-show="showMsg">
      {{ msg }}
    </div>
    <p> 对象遍历 v-for </p>
    <ul>
      <li v-for="(value, key, index) in infos">{{ index }} - {{ key }} - {{ value }}</li>
    </ul>
    <p> 整数遍历 v-for </p>
    <span v-for="n in 9">{{ n }}</span>
    <div>
      <button type="button" v-on:click="count += 1">点击增加次数</button>
      <p>这个按钮被点击了{{ count }}次</p>
      <button type="button" v-on:click="greet">点击出现弹框</button>
    </div>
  </div>

</template>



<script>
  export default {
    name: 'Mili',
    data () {
      return {
        dif: false,
        lists: [{
          color: 'red'
        }, {
          color: 'green'
        }, {
          color: 'blue'
        }, {
          color: 'yellow'
        }, {
          color: 'lightblue'
        }],
        loginType: 'username',
        showMsg: true,
        msg: 'v-show if true you can see me',
        infos: {
          firstname: 'mili',
          lastname: 'xie',
          age: 22
        },
        count: 0
      }
    }
  }
</script>
