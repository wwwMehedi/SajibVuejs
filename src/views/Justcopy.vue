<template>
  <div id="app">
  <div>
<img src="../assets/imgone.jpg">
  </div>
    <select v-model="item">
      <option v-for="(l,index) in list" :key="index" :value="index">{{l}}</option>
    </select>

    {{item}}
  </div>
</template>

<script>

export default {
  name: "App",
  data() {
    return {
      title: "Pick one",
      list: ['hi1', 'hi2','hi3'],
      item: 2
    };
  }
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>