<template>
  <div id="app">
    <HeaderBar/>
    <MainComponent/>
    <ul>
      <li v-for="movie in movies" :key="movie.id" >
        {{movie.original_title}}
      </li>
    </ul>
  </div>
</template>

<script>
import axios from 'axios';
import HeaderBar from './components/HeaderBar.vue';
import MainComponent from './components/MainComponent.vue';

export default {
  name: 'App',
  components: {
    HeaderBar,
    MainComponent
},
  data(){
    return{
      movies: [],
      tvSeries: [],
      api_key: '25c2b2a4e398c512c00e56a4e4c2468a',
      query: 'return',
      BASE_URI: 'https://api.themoviedb.org/3',
    }
  },
  methods:{
    fetchMovies(){
      axios.get(`${this.BASE_URI}/search/movie`),{
        params: {
          api_key: this.api_key,
          query: this.query
        }
      }
      .then((res) => {
        console.log(res)
        this.movies = res.data.results 
      })
    },
    fetchTvSeries(){
      axios.get(`${this.BASE_URI}/search/tv`),{
        params: {
          api_key: this.api_key,
          query: this.query
        }
      }
      .then((res) => {
        console.log(res)
        this.tvSeries = res.data.results
      })
    },

  },
  beforMount(){
    this.fetchMovies()
  }

}

</script>

<style lang="scss">

</style>
