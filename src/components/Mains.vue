<template>
  <div class="hello">
     
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
<style scoped lang="scss">
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>

