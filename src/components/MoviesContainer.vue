<template>
    <div class="container">
        <div class="movie-card">

            <!-- <img :src="src" :alt="name"/> -->

            <div class="info-box">
                <div class="info">
                <strong>Titolo: </strong>
                {{ name }}
                </div>

                <div class="info">
                <strong>Titolo originale: </strong>
                {{ originalName }}
                </div>

                <div class="info">
                <strong>Lingua: </strong>
                {{ language }}
                </div>

                <div class="info">
                <strong>Voto: </strong>
                {{ Math.round(vote / 2) }}
                </div>
            </div>

        </div>
    </div>
  </template>
  
  <script>
  export default {
    name: 'MoviesContainer',
    props: {
      name: String,
      originalName: String,
      language: String,
      vote: Number,
      src: String
    }
  }
  </script>
  
  <!-- Add "scoped" attribute to limit CSS to this component only -->
  <style scoped lang="scss">
  
    .container{
        
    }  

  </style>