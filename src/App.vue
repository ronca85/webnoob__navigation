<template>
  <div id="app">
    <Sidebar />
  </div>
</template>

<script>
import Sidebar from './components/Sidebar'
export default {
  components: {
    Sidebar
  }
}
</script>

<style lang="scss">
  * {
    margin: 0;
    box-sizing: border-box;
  }

  body {
    font-size: 1rem;
    font-family: Tahoma, serif;
    background-color: #ccc;
    color: #333;
  }

  #app {
    position: relative;
    min-height: 100vh;
    width: 100%;
  }
</style>

