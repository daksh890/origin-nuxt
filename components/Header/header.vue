<template>
    <div class="header">
        <div class="logo">
            <img alt="logo" src="/logo.png"/>
        </div>
        <div class="nav">
            <RouterLink to="/">Homepage</RouterLink>
        </div>
    </div>
</template>



<style scoped>
    .header{
        box-sizing:border-box;
        height:5rem;
        width:100%;
        margin:0;
        padding:0 2rem;
        position:sticky;
        top:0;
        display: flex;
        background-color: black;
        flex-direction: row;
        align-items: center;
        justify-content: space-between;
        color:white;
    }
    
    .logo img{
        width:5rem;
    }
    .nav{
        margin-right: 6rem;
    }
    .nav a{
        text-decoration: none;
        font-size: 1rem;
        color:white;
        cursor:pointer;

    }

</style>