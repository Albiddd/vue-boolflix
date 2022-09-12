<template>
  <div id="app">
    <HeaderBar @search="onSearch" />
    <MainComponent :movies="movies" :tvSeries="tvSeries" :search="query" />
    <!-- <ul>
      <li v-for="movie in movies" :key="movie.id" >
        {{movie.original_title}}
      </li>
    </ul> -->
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
      query: '',
      BASE_URI: 'https://api.themoviedb.org/3',
    }
  },

  methods:{
    onSearch(data){
        this.query = data
   
      axios.get((`${this.BASE_URI}/search/movie`),{
        params: {
          api_key: this.api_key,
          query: this.query
        }
      })
      .then((res) => {
        console.log(res)
        this.movies = res.data.results 
      })
    
      axios.get((`${this.BASE_URI}/search/tv`),{
        params: {
          api_key: this.api_key,
          query: this.query
        }
      })
      .then((res) => {
        console.log(res)
        this.tvSeries = res.data.results
      })
    },
      fetchPopularMovies(){
        axios.get((`${this.BASE_URI}/movie/popular`),{
          params: {
            api_key: this.api_key,
          }
        })
        .then((res) => {
          console.log(res)
          this.movies = res.data.results 
        })
      },
      fetchPopularSeries(){
        axios.get((`${this.BASE_URI}/tv/popular`),{
          params: {
            api_key: this.api_key,
          }
        })
        .then((res) => {
          console.log(res)
          this.tvSeries = res.data.results
        })
      },
  },
  beforeMount(){
    this.fetchPopularMovies()
    this.fetchPopularSeries()
  }
  }


</script>

<style lang="scss">
  @import './styles//general.scss';
  #app{
    width: 100%;
    height: 100vh;
    background-color: black;
   overflow: hidden;
  }
</style>
