<template>
  <div class="container-fluid">

    <div class="navbar my_navbar">

        <a class="navbar-brand my_style-brand" href="#">
            <img :src="img" alt="">
        </a>

    </div>

  </div>
</template>

<script>
export default {
    name: 'myHeader',
    data(){
        return{
            img: require("../assets/img/Spotify_App_Logo.svg.png")
        }
    }
}
</script>

<style lang="scss" scoped>
@import "../assets/style/general.scss";
.my_navbar{
    background-color: #000;
    height: 60px;
}

img {
    width: 50px;
    height: 50px;
    margin-left: 20px;
}
</style>