<template >
<div class="content">
  <h1>Recipe site</h1>
  <div class="recipes">
    <div v-for="el in myArr" :key="el">
      <Recipe :recipe="el" />
    </div>
  </div>
  <button @click="getData()">GET DATA</button>
  </div>
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'
import Recipe from './components/Recipe.vue';

export default {
  name: 'App',
  components: {
    Recipe,
  },
  data(){
    return{
     myArr: []
    }
  },
  methods: {
    async getData(){
      let res = await fetch('https://api.spoonacular.com/recipes/random?number=10&apiKey=ac54b2c3f7be4b98b26f59ef491867d6');
      let data = await res.json();
      console.log(data)
      this.myArr = data.recipes;
    }
  },
  created(){
    this.getData();
  }
}
</script>

<style>
  *{
    margin:0;
    padding: 0;
    box-sizing: border-box;
  }

  #app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    margin-top: 60px;
  }

  .recipes{
    display:grid;
    grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
    gap:16px;
  }
</style>
