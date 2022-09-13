<template>
    <header>
        <div class="container">
            <div class="logo">
                <img @click="$emit('reset')" src="../assets/Boolflix-logo.png" alt="">
            </div>
            <div class="nav">
                

                <span v-for="category,i in categories"
                :key="i"
                :class="i == active? 'active' : ''"
                @click="$emit('selectedCat', i)">

                {{category}}
                </span>

            </div>
            <div class="search-bar">    
                <input v-model="search" type="text" @keyup.enter="$emit('search', search)" placeholder="Search a title">
                <div class="search-button">
                    <img @click="$emit('search', search)" src="../assets/search.png" alt="">
                </div>
            </div>
        </div>
    </header>
  </template>
  
  <script>
  export default {
    name: 'HeaderBar',
    props: {
        active: Number,
    },
    data(){
        return{
            search:'',
            categories: ['Home', 'Movies', 'TV Series']
        }
    },

  }
  </script>
  
  <!-- Add "scoped" attribute to limit CSS to this component only -->
  <style scoped lang="scss">
    
    header{
        margin-bottom: 10px;
        .container{
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 10px 30px;
            .logo{
                padding-top: 5px;
                cursor: pointer;
            }
            .nav{
                color: rgba(245, 245, 245, 0.842);
                font-weight: 600;
                span{
                    padding: 0 8px;
                    cursor: pointer;
                    transition: linear 0.2s;
                    &:hover{
                        color: rgba(245, 245, 245, 0.684);
                    }
                }
                .active{
                    color: white;
                }
            }
            .search-bar{
                display: flex;
                height: 36px;
                border: 2px solid rgba(245, 245, 245, 0.842);
                input{
                    background-color: rgba(0, 0, 0, 0.282);
                    padding: 5px;
                    font-size: 18px;
                    border: none;
                    color: white;
                    outline: none;
                }
                .search-button{
                    background-color: rgba(0, 0, 0, 0.282);
                    height: 100%;
                    width: 30px;
                    padding: 5px 5px 7px 5px;
                    display: flex;
                    align-items: center;
                    img{
                        max-width: 100%;
                        filter: invert(0.5);
                    }
                    &:hover img{
                        filter: invert(1);
                        cursor: pointer;
                    }
                }
            }
        }
    }

  </style>