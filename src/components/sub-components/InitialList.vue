<template>
        <div @mouseover="active=true" @mouseleave="active=false" class="card m-3" >
  
          <img  :src="`https://image.tmdb.org/t/p/w342${carte.poster_path}`" alt="">
        
          <div class="onHover" v-if="active">
            <div class="cardTextStyle">
              <li class="textCard">{{carte.title}}</li>
              <li class="secondTextCard">{{carte.original_title}}</li> 
              <li class="info">{{carte.overview}}</li>     

              <img :src="require(`../../assets/img/${carte.original_language}.png`)" alt="">
            </div>
        </div>
      </div>
</template>

<script>
export default {
  name:'InitialList',
data(){
    return{
       active : false
    }
  },
  props:{
      carte:Object
  }
}
</script>

<style>

</style>