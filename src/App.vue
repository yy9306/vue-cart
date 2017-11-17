<template>
  <div id="app">
     <helloworld @cartAdd="cartAdd"></helloworld>
     <HelloJun ref="Jun"></HelloJun>
  </div>
</template>

<script>
import helloworld from 'components/HelloWorld'
import HelloJun from 'components/HelloJun'
export default {
  name: 'app',
  components: {
    helloworld, HelloJun
  },
  methods: {
    cartAdd (el) {
      this.$refs.Jun.drop(el)
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
}
</style>
