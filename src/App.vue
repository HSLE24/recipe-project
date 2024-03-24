<template>
  <div id="app">
    <div class="container text-center">
      <NavComp></NavComp>
      <h1 class="mainLogo">오늘의 레시피<i class="fa-solid fa-cookie-bite"></i></h1>
      <MainComp></MainComp>
    </div>
  </div>
</template>

<script>
import NavComp from './components/NavComp';
import MainComp from './components/MainComp';

export default {
  name: 'App',
  components: {
    MainComp, NavComp
  }
}
</script>

<style>
.mainLogo{
  padding-top: 1em;
  font-weight: bold;
}
</style>
