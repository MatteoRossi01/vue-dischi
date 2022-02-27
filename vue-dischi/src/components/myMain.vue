<template>
    <main>

        <myLoading :loading="loading"/> 

        <div class="container-main">
            
            <div class="vinyl-card" v-for="(album,index) in filteredAlbum" :key="index">
                
                <img :src="album.poster" alt="Vinyl Poster">
                
                <div class="card-text text-center">
                    <span class="title-vinyl text-uppercase">{{album.title}}</span>
                    <div class="text-gray">
                        <span>{{album.author}}</span>
                        <span>{{album.year}}</span>
                    </div>
                </div> 
                
            </div>
  
        </div>

    </main>
</template>

<script>
const axios = require('axios');

import  myLoading from './partials/myLoading.vue'

export default {
    name:'myMain',

    components :{
        myLoading
    },

    props: {
        'selectedGenre': String
    },

    data(){
        return{
            albumList: [],
            genres: [],
            loading: true,
        }
    },

    computed: {
        filteredAlbum () {

            if (this.selectedGenre == '') {
                return this.albumList;
            } else {
                return this.albumList.filter( album => {
                    return album.genre == this.selectedGenre;
                });
            }
        },
        
    },

    methods : {

        getAlbum(){
           axios.get('https://flynn.boolean.careers/exercises/api/array/music')
            
            .then((response) => {
                this.albumList = response.data.response;

                this.albumList.forEach(album => {
                    if (!this.genres.includes(album.genre)) {
                        this.genres.push(album.genre);
                    }
                });

                this.$emit('genresReady', this.genres);
                
            })
            .catch(function (error) {
                console.log(error);
            })

            setTimeout(() => {
                this.loading = false;
            }, 400);
  
        }
    },
    created(){
        this.getAlbum()
    },
}
</script>

<style lang="scss" scoped>
@import "../assets/style/general.scss";

    main{
        height: calc(100vh - 60px);
        width: 100%;
        background-color: #1E2D3B;
        display: flex;
        justify-content: center;
        align-items: center;

        .container-main {
            width: 62%;
            height: 520px;
            margin-top: 20px;
            display: flex;
            flex-direction: row;
            justify-content: space-around;
            flex-wrap: wrap;

            .vinyl-card {
                width: 18%;
                height: 250px;
                background-color: #2E3A46;
                display: flex;
                flex-direction: column;
                align-items: center;
                cursor: pointer;

                img {
                    margin-top: 20px;
                    width: 115px;
                    height: 115px;
                }

                .card-text {
                    width: 80%;
                    height: 90px;
                    line-height: 16px;
                    margin-top: 10px;
                    display: flex;
                    flex-direction: column;
                    

                    .title-vinyl {
                        color: #fff;
                        font-size: 16px;
                        font-weight: 600;
                    }

                    .text-gray {
                        display: flex;
                        flex-direction: column;
                        margin-top: 20px;
                        font-size: 14px;
                        color: #808078;
                        line-height: 16px;
                    }
                }
            }
        }   
    }
</style>