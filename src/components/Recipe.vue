<template>
  <div class="recipe">
    <img :src="recipe.image" :alt="recipe.id"/>
    <h3>{{recipe.title}}</h3>
    <p v-html="recipe.summary"/>
    <div class="btn-container">
      <button v-if="count > 0" @click="remove" class="remove" >-</button>
      <p v-if="count > 0">{{count}}</p>
      <button @click="add" :class="count > 0 && 'remove' " >+</button>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Recipe',
  props: {
    recipe: Object,
  },
  data(){
    return{
      count: 0
    }
  },
  methods:{
    remove(){
      this.count -= 1;
      this.$emit('remove')
    },
    add(){
      this.count += 1;
      this.$emit('add')
    }
  },
  emits:['add','remove']
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

 button{
   all:unset;
   cursor: pointer;
   background:green;
   color:white;
   font-weight:bold;
   font-size: 20px;
   width:24px;
   height:24px;
   border-radius:32px;
   margin-left:auto;
 }
 .remove{
   margin: 0;
 }
 .btn-container{
   display:flex;
   justify-content: space-between;
   padding:4px 24px;
 }
</style>