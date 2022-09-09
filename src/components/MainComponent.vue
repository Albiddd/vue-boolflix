<template>
    <main>
        <div>
            <h2>Movies</h2>
            <MoviesContainer
                v-for="movie in movies"
                :key="movie.id"
                :src="`https://www.themoviedb.org/t/p/original${movie.poster_path}`"
                :name="movie.title"
                :originalName="movie.original_title"
                :language="movie.original_language"
                :vote="movie.vote_average"/>
        </div>
        <div>
            <h2>TV Series</h2>
            <MoviesContainer
                v-for="movie in tvSeries"
                :key="movie.id"
                :src="`https://www.themoviedb.org/t/p/original${movie.poster_path}`"
                :name="movie.name"
                :originalName="movie.original_name"
                :language="movie.original_language"
                :vote="movie.vote_average"/>
        </div>
    </main>
  </template>
  
  <script>
    import MoviesContainer from './MoviesContainer.vue';
    export default {
        name: "MainComponent",
        props: {
            movies: Array,
            tvSeries: Array
        },
        components: { MoviesContainer },

    }
  </script>
  
  <!-- Add "scoped" attribute to limit CSS to this component only -->
  <style scoped lang="scss">
  
    main{
        padding: 10px 30px;
        h2{
            color: rgba(245, 245, 245, 0.722);
        }
    }
  </style>