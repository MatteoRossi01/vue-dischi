<template>
  <div class="container-header">

    <a class="" href="#">
        <img :src="img" alt="Logo Spotify">
    </a>

    <select v-model="selectedGenre" @change="$emit('selectedGenreEvt', selectedGenre)" name="" id="">
        <option value="">Scegli un genere</option>
        <option v-for="(genre, index) in genresList" :value="genre" :key="index">{{genre}}</option>
    </select>

  </div>
</template>

<script>
export default {
    name: 'myHeader',
    props: {
        'genresList': Array
    },
    data(){
        return{
            img: require("../assets/img/Spotify_App_Logo.svg.png"),

            selectedGenre: '',
        }
    },
}
</script>

<style lang="scss" scoped>
@import "../assets/style/general.scss";
.container-header{
    background-color: #000;
    height: 60px;
    width: 100%;
    display: flex;
    align-items: center;
}

img {
    width: 50px;
    height: 50px;
    margin-left: 20px;
}
</style>