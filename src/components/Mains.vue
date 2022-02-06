<template>
  <div class="main_back">
     
  <div class="d-flex flex-wrap justify-content-center">
    <filmFiltrati 
        v-for="(element,index) in passaMain"
        :key="index"
        :prodotto="element" 
        
        />
  </div>
          
   
 

</div>    
</template>

<script>


import filmFiltrati from './sub-components/filmFiltrati.vue';

export default {
  components: { 
    filmFiltrati ,
    
    },
  name: 'Mains',
  props: {
    passaMain: Array
    
  },
 
    
  
    methods:{
  },
  
 
 

}


</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss" scoped>
@import '../assets/style/variables.scss';

.main_back{
  background-color: rgb(49, 48, 48) ;
}
</style>

