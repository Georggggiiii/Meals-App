<template>
    <HeaderComp />
  <router-view/>
</template>

<script>
import HeaderComp from '@/components/HeaderComp.vue'

export default {
  components: {
    HeaderComp
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
</style>
