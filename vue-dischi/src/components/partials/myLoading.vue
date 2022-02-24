<template>

    <div class="container-load" v-if="loading">
        <span>Loading...</span>
    </div>

</template>

<script>
export default {
    name: 'myLoading',
    props:{
        loading: Boolean,
    }
}
</script>

<style lang="scss" scoped>

    .container-load {
        position: fixed;
        left: 0;
        bottom: 0;
        width: 100vw;
        height: calc(100vh - 60px);
        display: flex;
        justify-content: center;
        align-items: center;
        background-color: #1E2D3B;
    
        span {
            font-size: 40px;
            color: #fff;
        }
    }
    
</style>