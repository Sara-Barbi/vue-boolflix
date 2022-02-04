<template>
<div>
    <img :src="`https://image.tmdb.org/t/p/w154${prodotto.immagine}`" alt="">
    <li>{{prodotto.titolo}}</li>
    <li>{{prodotto.titolo_originale}}</li>     
    <img :src="require(`../../assets/img/${prodotto.lingua}.png`)" alt="">
    <li>{{prodotto.voto}}</li>
   
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