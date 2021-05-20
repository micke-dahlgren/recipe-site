<template>
  <div class="recipe">
    <img :src="recipe.image" :alt="recipe.id"/>
    <h3>{{recipe.title}}</h3>
    <p v-html="recipe.summary"/>
  </div>
</template>

<script>
export default {
  name: 'Recipe',
  props: {
    recipe: Object,
  },
  emits:['add']
}
</script>

<style scoped>
.recipe{
  width: 200px;
}
img{
  width: 100%;
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