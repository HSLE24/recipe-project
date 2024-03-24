<template>
    <div>
        <div class="interval"></div>
        <div class="category-bar">
          <span v-for="(cuisine, index) in cuisines" :key="index" @click="selectCuisine(cuisine)">
            <span  v-if="selectedCuisine == cuisine" class="active-category">{{ cuisine }}</span>
            <span  v-else>{{ cuisine }}</span>
          </span>
        </div>
        <div class="interval"></div>
        <div class="d-flex" role="search">
          <input class="form-control me-2" type="search" placeholder="Search" aria-label="Search" v-model="searchTxt">
          <button class="btn btn-outline-success" @click="requestAPI">Search</button>
        </div>
        <div class="interval-2"></div>
        <SearchList v-bind:propsrecipe="recipeData"></SearchList>
        <div class="interval"></div>
    </div>
</template>

<script>
import axios from 'axios';
import SearchList from './SearchList.vue';

export default {
    name: 'MainComp',
    data(){
      return {
        cuisines: ['American','British','Chinese','French','Indian','Italian'
        ,'Japanese','Korean','Spanish','Thai','Vietnamese'],
        selectedCuisine: 'Korean',
        searchTxt: '',
        recipeData: []
      }
    },
    components: {
        SearchList
    },
    methods: {
      selectCuisine: function(cuisine){
        this.selectedCuisine = cuisine;
        console.log(this.selectedCuisine)
      },
      requestAPI: function(){
        console.log("???")
        let self = this;

        axios({
          method: 'get',
          url: 'https://api.spoonacular.com/recipes/complexSearch',
          params: {
            apiKey: '7dccf51e73e141d3844446d0dabc01f1',
            query: this.searchTxt,
            cuisines: this.selectedCuisine
          }
        }).then(function(response){
          console.log(response.data);
          self.recipeData = response.data.results;
        }).catch(function(){
          console.log("뭔가 문제가 있어요");
        })
      }
  },
  created(){
    console.log("created")
    this.requestAPI();
  }
}
</script>

<style>
.interval{
  padding-top: 1em;
}
.interval-2{
  padding-top: 2em;
}
.category-bar{
  display:flex; 
  flex-direction: row; 
  justify-content: space-around;
}
.active-category{
  color: blue;
  font-weight: bold;
}
.category-bar span{
  cursor: pointer;
}
</style>
