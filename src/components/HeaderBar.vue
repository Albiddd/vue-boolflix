<template>
    <header>
        <div class="container">
            <div class="search-bar">
            <input v-model="search" type="text">
            </div>
        </div>
    </header>
  </template>
  
  <script>
  export default {
    name: 'HeaderBar',
    props: {
    },
    data(){
        return{
            search:'',
        }
    }
  }
  </script>
  
  <!-- Add "scoped" attribute to limit CSS to this component only -->
  <style scoped lang="scss">
  
  </style>