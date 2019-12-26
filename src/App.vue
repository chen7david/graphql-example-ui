<template>

  <v-app>
    <Navbar/>
    <div id="nav">
      <router-link to="/">Home</router-link> |
      <router-link to="/about">About</router-link>
    </div>
    <v-content>
      <router-view/>
    </v-content>
    
  </v-app>
</template>

<script>
import Navbar from './components/ui/Navbar'
export default {
  name:'App',
  components:{
    Navbar
  }
}
</script>

<style>

</style>
