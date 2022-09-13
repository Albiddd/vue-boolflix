<template>
  <div id="app">
    <HeaderBar @search="onSearch" @reset="reset" @selectedCat="selectCat" :active="currentCat" />
    <MainComponent :movies="movies" :tvSeries="tvSeries" :search="query" :showMovies="showMovies" :showTv="showTv" />
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
      showMovies: true,
      showTv: true,
      currentCat: 0,
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
      reset(){
        this.query = '';
        this.fetchPopularMovies();
        this.fetchPopularSeries();
        this.currentCat = 0;
        this.showMovies = true;
        this.showTv = true;
      },

      selectCat(i){
        if(i == 1){
          this.showMovies = true;
          this.showTv = false;
        } else if(i == 2){
          this.showMovies = false;
          this.showTv = true;
        }else{
          this.showMovies = true;
          this.showTv = true;
        }
        this.currentCat = i;
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
