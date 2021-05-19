<template>
  <img :src="recipe.image" :alt="recipe.id"/>
  <h3>{{recipe.title}}</h3>
  <p v-html="recipe.summary"/>
</template>

<script>
export default {
  name: 'Recipe',
  props: {
    recipe: Object,
  }
}
</script>

<style scoped>
 img{
   width: 20vw;
 }
 p{
  text-align: left;
  display: -webkit-box;
  -webkit-line-clamp: 4; /* number of lines to show */
  -webkit-box-orient: vertical;
  overflow: hidden;
  text-overflow: ellipsis;
 }
</style>