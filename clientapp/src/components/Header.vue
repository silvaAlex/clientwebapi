<template>
  <div id="nav">
    <router-link to="/">Home</router-link>
    <router-link to="/todo-api">Todos</router-link>
    <router-link to="/about">Sobre</router-link>
  </div>
</template>

<script>
export default {
  name: "Header"
};
</script>

<style lang="scss" scoped>
$body-bg: #f8f9fa;
$light-color: #fff;
$link: #42b983;

#nav {
  background-color: $body-bg;
  border-color: $body-bg;
  margin: 15px 20px;
  padding: 20px;

  a {
    font-weight: bold;
    color: $link;
    padding: 20px;
    text-decoration: none;
  }

  a.router-link-exact-active {
    color: $light-color;
    background: $link;
  }
}
</style>
