<template>
    <div class="img-box">
        <!-- id, title, image -->
        <img :src="rData.image" class="recipe-img">
        <span class="recipe-title">{{ rData.title }}</span>
    </div>
</template>

<script>
export default {
    name: 'SearchListItem',
    props: {
        rData: Object
    }
}
</script>

<style>
.img-box{
    display: flex; 
    flex-direction: column;
    width:400px;
    margin: 1em;
}
.recipe-img{
    border-radius: 24px;
}
.recipe-title{
    padding: 1em 0.2em 1em 0.2em;
}
</style>
