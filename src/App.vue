<template>
  <div id="app">
    <Header v-bind:appName="name" />
    <router-view />
    <!-- <h3>Inject your own html here</h3>
    <form @submit.prevent=onSubmit>
      <input v-model="rawHTML" type='text'>
      <input type="submit">
    </form> -->
  </div>
</template>

<script>
import Header from './components/layout/Header'
export default {
  name: 'app',
  components: {
    Header
  },
  methods: {
    onSubmit() {
      console.log('this is a dangerous practice')
      this.name = this.rawHTML
    }
  },
  data() {
    return {
      name: '<h1>Mikes App</h1>',
      rawHTML: ''
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

#nav {
  padding: 30px;
}

#nav a {
  font-weight: bold;
  color: #2c3e50;
}

#nav a.router-link-exact-active {
  color: #42b983;
}
</style>
