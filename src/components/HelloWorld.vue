<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <div id="tutorial-one" v-cloak>
      {{greeting}}
      <input v-model="greeting" />
      <hr />
      <div class="tutorial-box1" v-if="isVisible1"></div>
      <div class="tutorial-box2" v-else-if="isVisible2"></div>
      <div class="tutorial-box3" v-else></div>
      <hr>
    </div>
    <p>
      This is my first project
      <a href="https://github.com/Quindevreede?tab=repositories" target="_blank" rel="noopener">GitHub Link</a>.
    </p>
    <h3>Some Links</h3>
    <ul>
      <li><a href="https://github.com/vuejs/vue-cli/tree/dev/packages/%40vue/cli-plugin-babel" target="_blank" rel="noopener">babel</a></li>
      <li><a href="https://github.com/vuejs/vue-cli/tree/dev/packages/%40vue/cli-plugin-eslint" target="_blank" rel="noopener">eslint</a></li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data: function () {
    return {
      greeting: "Type Something",
      isVisible1: false,
      isVisible2: false,
    };
  },
  props: {
    msg: String
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
.tutorial-box1 {
  background-color: mediumseagreen;
  height: 100px;
  width: 100px;
}
.tutorial-box2 {
  background-color: greenyellow;
  height: 100px;
  width: 100px;
}
.tutorial-box3 {
  background-color: darkslategray;
  height: 100px;
  width: 100px;
}
[v-cloak] {
  display: none;
}
</style>
