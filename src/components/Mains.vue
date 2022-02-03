<template>
  <div class="hello">

    <input 
    type="text"
    placeholder="search your film!"
    v-model="inputCerca">

    <button @click="cerca">Cerca</button>
    <ul 
        v-for="(element,index) in filmLista"
        :key="index">
          <li>{{element.title}}</li>
          <li>{{element.original_title}}</li>
          <img :src="`../assets/img/flags/${element.original_language}.png `" alt="">
          <li>{{element.vote_average}}</li>
    </ul>
   
 

</div>    
</template>

<script>
import axios from 'axios';

export default {
  name: 'Mains',
  props: {

    
  },
 data(){
   return{
     apiURL: "https://api.themoviedb.org/3/search/movie",
     inputCerca:'',
     filmLista:[],
   
     
   }
 },
  methods:{
    cerca: function(){
      axios
      .get(this.apiURL, {
      params: {
        api_key: '5ca4950d17856f632c0bf4407810d397',
        query: this.inputCerca,
      }
      })
      .then((response)=> {
        this.filmLista = response.data.results;


      })
      .catch((error) =>{
        console.log(error);
      })
    },
  
  }
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

<!--        axios
          .get('https://api.themoviedb.org/3/search/tv', {
          params: {
            api_key: 'c118f218a2e8045c8dc9d93ebeb85c9b',
            language: 'it-IT',
            query: this.ricercaUtente,
          }
          })
          .then( (response) => {
            this.serieLista = response.data.results;
            this.nuovoArr = this.filmLista.concat(this.serieLista);
            console.log(this.serieLista)
          
    
       });
-->