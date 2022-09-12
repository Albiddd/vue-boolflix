<template>

        <div class="movie-card">

                <img v-if="src !== `https://www.themoviedb.org/t/p/w500null`"
                :src="src" :alt="originalName" class="poster" />
                
                <img v-else 
                class="empty-img" src="../assets/no-image.jpg" :alt="originalName" />


            
            <div class="info-container">
                
                <div class="info-box">
                    <div class="info">
                        <strong>Title: </strong>
                        {{ titleName }}
                    </div>
    
                    <div class="info">
                        <strong>Original title: </strong>
                        {{ originalName }}
                    </div>
    
                    <div class="info-lang">
                        <strong>Language: </strong>
                        <img :src="`https://crowdin.com/images/flags/${language}.png`" alt="">
                    </div>
    
                    <div class="info">
                        <strong>Vote: </strong>

                        <font-awesome-icon v-for="index in stars"
                        :key="index" icon="fa-solid fa-star" />
                        <font-awesome-icon v-for="index in 5-stars"
                        :key="index" icon="fa-regular fa-star" />
                        
                    </div>
        
                    <div class="info">
                        <strong>Overview: </strong>
                        {{ overview }}
                    </div>
                </div>
            </div>

        </div>
  </template>
  
  <script>

  export default {
    name: 'MoviesContainer',
    props: {
      titleName: String,
      originalName: String,
      language: String,
      vote: Number,
      src: String,
      overview: String
    },
    data(){
        return{

        }
    },
    computed:{
        stars(){
           return Math.floor(this.vote / 2)
        }
    }
  }
  </script>
  
  <!-- Add "scoped" attribute to limit CSS to this component only -->
  <style scoped lang="scss">
  
    .movie-card{
        position: relative;

        .poster{
            width: 300px;
            height: 100%;
            border-radius: 8px;

        }
        .empty-img{
            width: 300px;
            height: 100%;
        }
        .info-container{
            position: absolute;
            top: 0;
            width: 100%;
            height: 100%;
            color: white;
            background-color: rgba(0, 0, 0, 0.82);
            border-radius: 8px;
            isolation: isolate;
            display: flex;
            justify-content: center;
            align-items: center;
            transition: linear opacity 0.2s;
            opacity: 0;
            .info-box{
                padding: 20px;
                font-size: 14px;

                .info-lang img{
                    width: 22px;
                    vertical-align: middle;
                }
                
            }
        }
        &:hover{

            .info-container{
                 opacity: 1;
            }
        }

    }


  </style>