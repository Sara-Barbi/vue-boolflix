<template>
  <div id="app">
    <Headers @filtraAncora="aggiornaDataAPI"/>
    <div v-if="filmLista.length>0">
      <Mains :passaMain="arrayFilmAdattata" titolo="lista film" />  
      <Mains :passaMain="arraySerieAdattata" titolo="lista serie"/> 
      <Mains :passaMain="arrayFilmsSerieAdattate" titolo="lista tutto" />
    </div>
    
    <div v-else class="main_Color">
      <div  v-for="(elements,index) in initialList" :key="index">

        <div class="card">
    
          <img :src="`https://image.tmdb.org/t/p/w342${elements.poster_path}`" alt="">
      
          <div class="onHover  ">
            <div class="cardTextStyle">
              <li class="textCard">{{elements.title}}</li>
              <li class="secondTextCard">{{elements.original_title}}</li>     
              <img :src="require(`./assets/img/${elements.original_language}.png`)" alt="">

              <li v-if="getStelle(elements.vote_average)==0"><i class="bi bi-star"></i><i class="bi bi-star"></i><i class="bi bi-star"></i><i class="bi bi-star"></i><i class="bi bi-star"></i></li>
              <li v-else-if="getStelle(elements.vote_average)==1"><i class="bi bi-star-fill"></i><i class="bi bi-star"></i><i class="bi bi-star"></i><i class="bi bi-star"></i><i class="bi bi-star"></i></li>
              <li v-else-if="getStelle(elements.vote_average)==2"><i class="bi bi-star-fill"></i><i class="bi bi-star-fill"></i><i class="bi bi-star"></i><i class="bi bi-star"></i><i class="bi bi-star"></i></li>
              <li v-else-if="getStelle(elements.vote_average)==3"><i class="bi bi-star-fill"></i><i class="bi bi-star-fill"></i><i class="bi bi-star-fill"></i><i class="bi bi-star"></i><i class="bi bi-star"></i></li>
              <li v-else-if="getStelle(elements.vote_average)==4"><i class="bi bi-star-fill"></i><i class="bi bi-star-fill"></i><i class="bi bi-star-fill"></i><i class="bi bi-star-fill"></i><i class="bi bi-star"></i></li>
              <li v-else><i class="bi bi-star-fill"></i><i class="bi bi-star-fill"></i><i class="bi bi-star-fill"></i><i class="bi bi-star-fill"></i><i class="bi bi-star-fill"></i></li>
            </div>
          </div>
        </div>
      </div>
    </div>
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
      serieLista:[],
      initialList:[]
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
            immagine:elem.poster_path
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
                  query: "amore"
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

<style lang="scss">
  @import url("https://cdn.jsdelivr.net/npm/bootstrap-icons@1.8.0/font/bootstrap-icons.css"); 

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;

}
.main_Color{
  background-color: rgb(49, 48, 48);
  
}
</style>
