<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <div id="tutorial-one" v-cloak>
      <login-form />
      <h4>TEXT PARROT</h4>
      <p>text input will be duplicated above</p>
      <input @keyup.enter="greet(greeting + '!!!')" v-model="greeting" placeholder="type something..."/>
      <hr />
      <button @click="toggleBox">Toggle Box</button>
      <div class="tutorial-box" v-if="isVisible"></div>
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
      greeting: "",
      isVisible: false,
    };
  },
  methods: {
    toggleBox() {
      this.isVisible = !this.isVisible
      // Met this. kun je bij de isVisible: false
    },
    greet(greeting) {
      console.log(greeting);
    }
  },
  props: {
    msg: String
  }
}
app.component('login-form', {
  template: `
  <form @submit.prevent="handleSubmit">
  <h1>{{ title }}</h1>
<!--  <p v-for="(str, i) in inputs" v-bind:key="i">{{ str }}</p>-->
  <custom-input
      v-for="(input, i) in inputs"
      v-bind:key="i"
      v-model="input.value"
      v-bind:label="input.label"
      v-bind:type="input.type"/>
  <button>LOG IN</button>
  </form>
  `,
  components: ['custom-input'],
  data() {
    return {
      title: 'Login Form',
      inputs:[
        {
          label: 'Email',
          value: '',
          type: 'email'
        },
        {
          label: 'Password',
          value: '',
          type: 'password'
        }
      ],
      email: '',
      password: '',
      emailLabel: 'Email',
      passwordLabel: 'Password'
    }
  },
  methods: {
    handleSubmit() {
      console.log(this.inputs[0].value, this.inputs[1].value);
    }
  }
})
app.component('custom-input', {
  template: `
  <label>
  {{ label }}
  <input v-bind:type="type" v-model="inputValue">
  </label>
  `,
  props: ['label', 'type', 'modelValue'],
  computed: {
    inputValue: {
      get() {
        return this.modelValue
      },
      set(value) {
        console.log(value)
        this.$emit('update:modelValue', value)
      }

    }
  }
  // data() {
  //   return {
  //     inputValue: ''
  //   }
  // }
})
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
* {
  margin: 0;
}
h1 {
  margin: 25px;
}
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
.tutorial-box {
  background-color: mediumseagreen;
  height: 100px;
  width: 100px;
}
[v-cloak] {
  display: none;
}
input {
  margin: 10px;
  display: block;
}
</style>
