<template>
<Header />
<HelloWorld :key="compKey"/>
<button @click="forceRerender">Refresh</button>
<Footer />
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
import Header from './components/Header.vue'
import Footer from './components/Footer.vue'

export default {
  data(){
 return {
   compKey:0,
 }
  },
  components: {
    Header,
    HelloWorld,
    Footer
  },
  methods: {
    forceRerender(){
      this.compKey += 1;
    }
  }

}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
