<script>
    export default {
        props: ['purpleWord', 'cyanWord', 'orangeWord']
    }
</script>

<template>
    <h1>
        <span class="header_purple">{{purpleWord}}</span> 
        <span class="header_cyan">{{cyanWord}}</span> 
        <span class="header_orange">{{orangeWord}}</span>
    </h1>
</template>

<style scoped>
    h1 {
        font-size: 1.7em;
        text-transform: uppercase;
        margin: 30px 0;
        display: flex;
        justify-content: center;
        gap: 10px;
        flex-wrap: wrap;
    }

    .header_purple {
        color: #976297;
    }

    .header_cyan {
        color: #00A19A;
    }

    .header_orange {
        color: #EC8B41;
    }

    @media screen and (min-width: 1024px){
        h1 {
            font-size: 3em;
            gap: 30px;
        }   
    }
</style>