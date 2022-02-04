<template>
  <div id="app">
    
    <Headers @filtraAncora="passaFiltroAncora"/>
    <Mains :passaMain="filmLista"/>
    <Footers />

  </div>

</template>

<script>
import axios from 'axios'
import Headers from './components/Headers.vue'
import Mains from './components/Mains.vue'
import Footers from './components/Footers.vue'

export default {
  name: 'App',
  components: {
    Headers,
    Mains,
    Footers
  },
  data(){
    return{
      input:"",
      filmLista:[]
    }
  },
  
  computed:{
    
   },
    methods:{
      cerca: function(){
        axios
        .get(this.apiURL, {
        params: {
          api_key: '5ca4950d17856f632c0bf4407810d397',
          query: this.input,
        }
        })
        .then((response)=> {
          this.filmLista = response.data.results;
          console.log(this.filmLista)


        })
        .catch((error) =>{
          console.log(error);
        })
      },
  
    
      passaFiltroAncora(inputFiltro){
      this.input= inputFiltro;

      }
    }
  
}
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
