<template>
  <div id="app">
    
    <Headers @filtraAncora="aggiornaDataAPI"/>
    <Mains :passaMain="arrayFilmsSerieAdattate" titolo="lista tutto" />
    <Mains :passaMain="arrayFilmAdattata" titolo="lista film"/>
    <Mains :passaMain="arraySerieAdattata" titolo="lista serie"/>
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
      filmLista:[],
      serieLista:[]
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
            voto: this.getStelle(elem.vote_average),
            immagine :elem.poster_path,
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
            voto: this.getStelle(elem.vote_average),
            immagine:elem.poster_path
          };
          arrayFilm.push(objApp);
        });
        return arrayFilm;
      },
      arrayFilmsSerieAdattate() {
          return [...this.arrayFilmAdattata, ...this.arraySerieAdattata];
      }
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
  
    
      passaFiltroAncora(inputFiltro){
      this.input= inputFiltro;

      },
      getStelle(num){
         Math.round((num)/2).toFixed(0)
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
