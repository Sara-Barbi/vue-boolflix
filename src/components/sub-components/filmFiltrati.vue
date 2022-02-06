<template>
<div>
    <img :src="`https://image.tmdb.org/t/p/w154${prodotto.immagine}`" alt="">
    <li>{{prodotto.titolo}}</li>
    <li>{{prodotto.titolo_originale}}</li>     
    <img :src="require(`../../assets/img/${prodotto.lingua}.png`)" alt="">

    <li v-if="getStelle(prodotto.voto)==0"><i class="bi bi-star"></i><i class="bi bi-star"></i><i class="bi bi-star"></i><i class="bi bi-star"></i><i class="bi bi-star"></i></li>
    <li v-else-if="getStelle(prodotto.voto)==1"><i class="bi bi-star-fill"></i><i class="bi bi-star"></i><i class="bi bi-star"></i><i class="bi bi-star"></i><i class="bi bi-star"></i></li>
    <li v-else-if="getStelle(prodotto.voto)==2"><i class="bi bi-star-fill"></i><i class="bi bi-star-fill"></i><i class="bi bi-star"></i><i class="bi bi-star"></i><i class="bi bi-star"></i></li>
    <li v-else-if="getStelle(prodotto.voto)==3"><i class="bi bi-star-fill"></i><i class="bi bi-star-fill"></i><i class="bi bi-star-fill"></i><i class="bi bi-star"></i><i class="bi bi-star"></i></li>
    <li v-else-if="getStelle(prodotto.voto)==4"><i class="bi bi-star-fill"></i><i class="bi bi-star-fill"></i><i class="bi bi-star-fill"></i><i class="bi bi-star-fill"></i><i class="bi bi-star"></i></li>
    <li v-else><i class="bi bi-star-fill"></i><i class="bi bi-star-fill"></i><i class="bi bi-star-fill"></i><i class="bi bi-star-fill"></i><i class="bi bi-star-fill"></i></li>

   
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
  @import url("https://cdn.jsdelivr.net/npm/bootstrap-icons@1.8.0/font/bootstrap-icons.css"); 
  .bi-star-fill{
    color: rgb(233, 233, 91);
  }
  

</style>