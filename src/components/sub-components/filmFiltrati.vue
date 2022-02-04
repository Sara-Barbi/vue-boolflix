<template>
<div>
    <li>{{prodotto.title}}</li>
    <li>{{prodotto.original_title}}</li>     
    <img :src="require(`../../assets/img/${prodotto.original_language}.png`)" alt="">
    <li>{{prodotto.vote_average}}</li>
   
</div>
  
</template>

<script>
export default {
  name:'filmFiltrati',
  props:{
    prodotto: Object

  }
}
</script>

<style>

</style>