<template>
  <div class="app">
    <img src="./assets/logo.png" height="128">
    <siswa></siswa>
    <!-- <Siswa/> -->
  </div>
</template>

<script>
import Siswa from './components/Siswa'

export default {
  name: 'app',
  components: {
    Siswa
  }
}
</script>

<style>
.app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 30px;
}
</style>
