<script setup>
import {  RouterView } from 'vue-router'
// import HelloWorld from './components/HelloWorld.vue'
</script>

<template>
  <!-- <header>
    <img alt="Vue logo" class="logo" src="@/assets/logo.svg" width="125" height="125" />

    <div class="wrapper">
      <HelloWorld msg="You did it!" /> 
      <div class="d-flex">
        <button class="btn btn-info" @click="redirect">Redirect</button>
        <button class="btn btn-info" @click="back">Previous</button>
        <button class="btn btn-info" @click="next">Next</button>
      </div>

      </div>
    </header> -->
    <!-- <nav>
      <RouterLink to="/">Home</RouterLink>
      <RouterLink :to="{name:'about'}">About</RouterLink>
      <RouterLink to="/jobs">Jobs</RouterLink>
      <RouterLink to="/api">Api</RouterLink>
      <RouterLink to="/music">Music</RouterLink>
    </nav> -->

  <RouterView />
</template>

<script>
  export default {
    methods: {
      redirect(){
        this.$router.push('/jobs')
      },
      back(){
        this.$router.go(-1)
      },
      next(){
        this.$router.go(1)
      }
    }
  }
</script>

<style scoped>

</style>
