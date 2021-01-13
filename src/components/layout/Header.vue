<template>
  <header class="header">
    <v-app-bar app color="primary" dark>
      <span v-html="appName"></span>
      <div id="nav">
        <router-link to="/">Home</router-link> |
        <router-link to="/about">About</router-link> |
        <router-link to="/slideShow">SlideShow</router-link>
      </div>
      <v-spacer></v-spacer>
      <v-icon>mdi-open-in-new</v-icon>
    </v-app-bar>
  </header>
</template>

<script>
export default {
  name: 'Header',
  props: ['appName']
}
</script>

<style scoped>
.header {
  background: #333;
  color: #fff;
  text-align: center;
  padding: 10px;
}
.header a {
  color: #fff;
  padding-right: 5px;
  text-decoration: none;
}
</style>
