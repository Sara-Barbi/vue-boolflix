<template>
  <div class="hello">
    <div class="container">
      <div class="row">
        <div class="col-12 d-flex justify-content-around align-items-center">
          <h2 class="logo">BOOLFLIX</h2>
          <cercaFilm 
            @filtra="passaFiltro"/>

        </div>
      </div>
    </div>
  </div>
</template>

<script>

import cercaFilm from './sub-components/cercaFilm.vue'

export default {
  name: 'Headers',
  components:{
    cercaFilm
  },
  
  
  props: {
    
  },
  methods:{
    passaFiltro(argument){
      this.$emit('filtraAncora', argument)
    }
  }

}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
.hello{
  max-height: 60px ;
  background-color: black ;
  z-index: 1;
}
.logo{
  color: rgb(164, 12, 12);
  font-family: 'Times New Roman', Times, serif;
  font-weight: 900;
}
</style>
