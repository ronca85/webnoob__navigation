<template>
<div id="sidebar-header">
  <div class="logo"></div>
  <div class="name">Ime Prezime</div>
  <div class="group">Admin</div>
</div>
</template>

<script>
export default {
}
</script>

<style lang="scss" scoped>
#sidebar-header {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  height: 250px;
  background: radial-gradient(rgb(27, 150, 233), rgb(98, 192, 255));
  color: #fefefe;
  .logo {
    background-image: url('https://placedog.net/120');
    background-position: center;
    background-size: cover;
    width: 120px;
    height: 120px;
    border-radius: 9999px;
  }
  .name {
    font-size: 1.4rem;
  }
}
</style>

