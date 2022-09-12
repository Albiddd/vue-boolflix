<template>
    <main>
        <div>
            <h2>{{search == '' ? 'Popular Movies' : 'Movies Found'}}</h2>
            <div class="card-wrapper">

                <MoviesContainer
                    v-for="movie in movies"
                    :key="movie.id"
                    :src="`https://www.themoviedb.org/t/p/w500${movie.poster_path}`"
                    :titleName="movie.title"
                    :originalName="movie.original_title"
                    :language="movie.original_language"
                    :vote="movie.vote_average"
                    :overview="movie.overview"/>

            </div>
        </div>
        <div>
            <h2>{{search =='' ? 'Popular TV Series' : 'TV Series Found'}}</h2>
            <div class="card-wrapper">
                <MoviesContainer
                    v-for="movie in tvSeries"
                    :key="movie.id"
                    :src="`https://www.themoviedb.org/t/p/w500${movie.poster_path}`"
                    :titleName="movie.name"
                    :originalName="movie.original_name"
                    :language="movie.original_language"
                    :vote="movie.vote_average"
                    :overview="movie.overview"/>

            </div>
        </div>
    </main>
  </template>
  
  <script>
    import MoviesContainer from './MoviesContainer.vue';
    export default {
        name: "MainComponent",
        props: {
            movies: Array,
            tvSeries: Array,
            search:{
                type: String,
                default:'',
            }
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
        .card-wrapper{
            display: flex;
            gap: 10px;
            padding: 10px 0;
            margin: 15px 0 60px 0;
            overflow-y: hidden;
            overflow-x: scroll;
        }
    }
  </style>