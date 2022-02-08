<template>
  <div id="app">
    <Headers 
    @filtraAncora="aggiornaDataAPI"
    class="position-fixed top-0 w-100"/>
    <div v-if="filmLista.length>0" class="marginTopMain">
      <Mains :passaMain="arrayFilmAdattata" titolo="lista film" />  
      <Mains :passaMain="arraySerieAdattata" titolo="lista serie"/> 
      <Mains :passaMain="arrayFilmsSerieAdattate" titolo="lista tutto" />
    </div>
    
    <div v-else class="main_Color d-flex flex-wrap">
      {{filmIniziali()}}

    <initial-list v-for="(cards, index) in initialList"  
         :key="index"
         :carte = cards />
    </div>
      
</div>
     
    

</template>

<script>
import axios from 'axios'
import Headers from './components/Headers.vue'
import Mains from './components/Mains.vue'
import InitialList from './components/sub-components/InitialList.vue'


export default {
  name: 'App',
  components: {
    Headers,
    Mains,
    InitialList
   
  },
  data(){
    return{
      input:"",
      filmLista:[],
      serieLista:[],
      initialList:[],
      
    }
  },
  
  computed:{
      arrayFilmAdattata(){
        const arrayFilm = [];
        this.filmLista.forEach((elem) => {
          const objApp = {
            titolo: elem.title,
            titolo_originale: elem.original_title,
            lingua: elem.original_language,
            voto: elem.vote_average,
            immagine :elem.poster_path,
            info: elem.overview,
          };
          arrayFilm.push(objApp);
        });
        return arrayFilm;
      },
      arraySerieAdattata(){
        const arrayFilm = [];
        this.serieLista.forEach((elem) => {
          const objApp = {
            titolo: elem.name,
            titolo_originale: elem.original_name,
            lingua: elem.original_language,
            voto: elem.vote_average,
            immagine:elem.poster_path,
            info: elem.overview,
          };
          arrayFilm.push(objApp);
        });
        return arrayFilm;
      },
      arrayFilmsSerieAdattate() {
          return [...this.arrayFilmAdattata, ...this.arraySerieAdattata];
      },
  
   },
    methods:{
      aggiornaDataAPI(inputFiltroAncora){
        this.input = inputFiltroAncora;
        this.cercaFilm();
        this.cercaSerie();
        
      },


      
      cercaFilm: function(){
        axios
        .get('https://api.themoviedb.org/3/search/movie', {
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
      cercaSerie: function(){
            axios
                .get('https://api.themoviedb.org/3/search/tv?', 
                {
                    params: {
                        api_key: '5ca4950d17856f632c0bf4407810d397',
                        query: this.input
                    }
                })
                .then( (response) => {
                    this.serieLista = response.data.results
                    
                })
                .catch(function (error) {
                    console.log(error);
                });
        },
      filmIniziali: function(){
      axios
          .get('https://api.themoviedb.org/3/search/movie', 
          {
              params: {
                  api_key: '5ca4950d17856f632c0bf4407810d397',
                  query:'avv'
                  
              }
          })
          .then( (response) => {
              this.initialList = response.data.results
              
              
          })
          .catch(function (error) {
              console.log(error);
          });
  },
  
    
      passaFiltroAncora(inputFiltro){
      this.input= inputFiltro;

      },
     
    }
  
}
</script>

<style lang='scss'>
  @import url("https://cdn.jsdelivr.net/npm/bootstrap-icons@1.8.0/font/bootstrap-icons.css"); 

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;

}
.marginTopMain{
  margin-top: 46px;
  
}
.main_Color{
  background-color: rgb(49, 48, 48);
  
  margin-bottom: 0;
  color: white;
  padding-top: 65px;
  
}
</style>
