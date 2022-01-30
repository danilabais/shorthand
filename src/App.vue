<template>
  <div class="app">
    <SideBar/>
    <div class="w-100 bg-light" style="height:100vh">
    <NavBar/>
    <router-view/>
    </div>
    <!-- <router-link to="/">Home</router-link> |
    <router-link to="/about">About</router-link>
  <router-view /> -->
  </div>
</template>


<script>
import SideBar from '@/components/SideBar.vue'
import NavBar from '@/components/NavBar.vue'
export default {
  components: {
    SideBar,
    NavBar
  }

}
</script>


<style>
.app {
  display: flex;
}
p {
  font-size: 4rem;
}


</style>
