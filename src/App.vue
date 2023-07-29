<template>
  <div id="app">
    <HelloWorld msg="Hello Vue in CodeSandbox!" class="test" />
  </div>
</template>

<script>
import HelloWorld from "./components/HelloWorld";

export default {
  name: "App",
  components: {
    HelloWorld,
  },
};
</script>

<style scoped>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.test {
  background-color: beige;
}
>>> .btn {
  background-color: rosybrown;
  color: yellow;
  font-size: 22px;
}

/* 样式穿透到子组件 */
>>> span {
  color: green;
}
</style>
