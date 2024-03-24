<template>
    <div class="search-container">
        <SearchListItem v-for="recipe in propsrecipe" :key="recipe.id" v-bind:rData="recipe"></SearchListItem>
    </div>
</template>

<script>
import SearchListItem from './SearchListItem.vue';

export default {
    name: 'SearchList',
    components: {
        SearchListItem
    },
    props: {
        propsrecipe: Array
    },
}
</script>

<style>
.search-container{
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    align-items: center;
    text-align: center;
}
</style>
