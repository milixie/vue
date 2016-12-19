<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <h1>reverse h1 <br> {{ msg.split('').reverse().join('') }}</h1>
    <h2>Essential Links</h2>
    <ul>
      <li v-bind:class="[activeClass, errClass]"><a href="https://vuejs.org" target="_blank">Core Docs</a></li>
      <li><a href="https://forum.vuejs.org" target="_blank">Forum</a></li>
      <li><a href="https://gitter.im/vuejs/vue" target="_blank">Gitter Chat</a></li>
      <li v-bind:class="[isActive ? 'active': '', 'text-danger']"><a href="https://twitter.com/vuejs" target="_blank">Twitter</a></li>
      <br>
      <li :class="[{ active: isActive, errClass }]"><a href="http://vuejs-templates.github.io/webpack/" target="_blank">Docs for This Template</a></li>
    </ul>
    <h2>Ecosystem</h2>
    <ul>
      <li class="static" ><a href="http://router.vuejs.org/" target="_blank">vue-router</a></li>
      <li class="static" v-bind:class="{ active: isActive, 'text-danger': hasError }"><a href="http://vuex.vuejs.org/" target="_blank">vuex</a></li>
      <li class="static" ><a href="http://vue-loader.vuejs.org/" target="_blank">vue-loader</a></li>
      <li class="static" ><a href="https://github.com/vuejs/awesome-vue" target="_blank">awesome-vue</a></li>
    </ul>
    <div class="wrap">
      <ul>
        <li v-for="lis in lists">{{ lis.text }}</li>
        <li v-bind:title="content">this is bind </li>
        <li v-if="seen">v if type when true you can see me</li>
        <li>
          <p>{{ inputText }}</p>
          <input v-model="inputText">
        </li>
        <li><button v-bind:disabled="abled">toggle button</button></li>
        <li>{{ ok ? 'YES': 'NO' }}</li>
        <li><a :href="url">home page</a></li>
        <li><button @click="doTest">do</button></li>
      </ul>
    </div>
  </div>
</template>

<script>
  export default {
    name: 'hello',
    data () {
      return {
        msg: 'mili lalalal Welcome to Your Vue.js App mili',
        lists: [{
          text: 'v for lists 1'
        }, {
          text: 'v for lists 2'
        }, {
          text: 'v-for lists 3'
        }],
        content: `bind time is ${new Date()}`,
        seen: false,
        inputText: 'hello mili!',
        abled: false,
        ok: true,
        url: 'https://github.com/mili',
        isActive: true,
        hasError: false,
        activeClass: 'active',
        errClass: 'text-danger'
      }
    }
  }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  h1, h2 {
    font-weight: normal;
  }

  ul {
    list-style-type: none;
    padding: 0;
  }

  li {
    display: inline-block;
    margin: 10px;
  }

  li.static {
    font-size: 12px;
    margin: 20px;
    display: block;
  }

  li.active {
    font-size: 30px;
  }

  li.text-danger a {
    color: red;
  }

  a {
    color: #42b983;
  }

  .wrap li {
    display: block;
  }
</style>
