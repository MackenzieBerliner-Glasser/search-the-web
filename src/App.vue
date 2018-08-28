<template>
  <div id="app">
    <header>
      <img src="./assets/logo.jpg">
      <nav>
        <router-link to="/">Home</router-link>
        <router-link to="/list">List</router-link>
      </nav>
    </header>

    <main>
      <router-view></router-view>
    </main>
  </div>
</template>

<script>


export default {
  name: 'app',
  components: {
  }
};
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}

header {
  height: 200px;
  background: lightgoldenrodyellow;
  display: flex;
  align-items: center;
  justify-content: space-between;
}
header img {
  height: 100%;
}
nav a {
  text-decoration: none;
  background-color: lightcoral;
  color: white;
  margin: 3px;
  padding: 3px;
  border: 1px solid black;
}
main {
  padding: 8px;
}
</style>
