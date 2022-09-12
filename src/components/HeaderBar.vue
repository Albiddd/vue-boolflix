<template>
    <header>
        <div class="container">
            <div class="logo">
                BOOLFLIX
            </div>
            <div class="search-bar">    
                <input v-model="search" type="text" @keyup.enter="$emit('search', search)" placeholder="Search a title">
                <div>
                    <img src="../assets/search.png" alt="">
                </div>
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
    
    header{
        margin-bottom: 30px;
        .container{
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 15px 30px;
            .logo{
                color: red;
                font-size: 36px;
                font-weight: 700;
            }
            .search-bar{
                display: flex;
                height: 36px;
                border: 2px solid rgba(255, 255, 255, 0.367);
                input{
                    background-color: rgba(0, 0, 0, 0.282);
                    padding: 5px;
                    font-size: 18px;
                    border: none;
                    color: white;
                    outline: none;
                }
                div{
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