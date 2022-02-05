<template>
<div>
    <img :src="`https://image.tmdb.org/t/p/w154${prodotto.immagine}`" alt="">
    <li>{{prodotto.titolo}}</li>
    <li>{{prodotto.titolo_originale}}</li>     
    <img :src="require(`../../assets/img/${prodotto.lingua}.png`)" alt="">

    <li v-if="getStelle(prodotto.voto)==0">5 stelle vuote</li>
    <li v-else-if="getStelle(prodotto.voto)==1">4stelle vuote,1 piena</li>
    <li v-else-if="getStelle(prodotto.voto)==2">3stelle vuote, 2 piene</li>
    <li v-else-if="getStelle(prodotto.voto)==3">2 stelle vuote, 3 piene</li>
    <li v-else-if="getStelle(prodotto.voto)==4">1 stella vuota,4 piene</li>
    <li v-else>0 stella vuota,5 piene</li>

   
</div>
  
</template>

<script>
export default {
  name:'filmFiltrati',
  props:{                          
    prodotto: Object

  },
  methods:{
    getStelle(num){
        return Math.round((num)/2).toFixed(0)
    }

  }
}
</script>

<style>
        

</style>