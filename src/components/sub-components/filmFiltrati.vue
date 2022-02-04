<template>
<div>
    <img :src="`https://image.tmdb.org/t/p/w154${prodotto.immagine}`" alt="">
    <li>{{prodotto.titolo}}</li>
    <li>{{prodotto.titolo_originale}}</li>     
    <img :src="require(`../../assets/img/${prodotto.lingua}.png`)" alt="">
    <li>valutazione: <ul>
      <li><span v-if="prodotto.voto==0"></span>
          <span v-else-if="prodotto.voto==1"><i class="fa-thin fa-star"></i><i class="fa-thin fa-star"></i><i class="fa-thin fa-star"></i><font-awesome-icon icon="fa-thin fa-star" /><font-awesome-icon icon="fa-thin fa-star" /></span>
          <span v-else-if="prodotto.voto==2"></span>
          <span v-else-if="prodotto.voto==3"></span>
          <span v-else></span></li>

      
    </ul></li>
   
</div>
  
</template>

<script>
export default {
  name:'filmFiltrati',
  props:{                          
    prodotto: Object

  },
  data(){
    return{
      
        
      

    }
  }
}
</script>

<style>
        

</style>