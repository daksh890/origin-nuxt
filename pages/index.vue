<template>
    <div class="home">
        <Header/>
        <div class="login">
            <Signin/>
        </div>
    </div>
</template>

<script setup lang="ts">
    import Header from '~/components/Header/header.vue';
    import Signin from '~/components/Signin/signin.vue';
</script>

<style>
    body, html{
        margin:0;
        padding:0;
    }
    .home{
        width:100%;
        height:100%;
        box-sizing: border-box;
    }
    .login{
        margin: 7rem auto;
        /* background-color: bisque; */
        width:100%;
    }
</style>