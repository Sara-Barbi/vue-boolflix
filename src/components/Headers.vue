<template>
  <div class="hello">

    <cercaFilm 
      @filtra="passaFiltro"/>

  </div>
</template>

<script>

import cercaFilm from './sub-components/cercaFilm.vue'

export default {
  name: 'Headers',
  components:{
    cercaFilm
  },
  data(){
    return{
      filtroInput:""
    }
  },
  
  props: {
    
  },
  methods:{
    passaFiltro(argument){
      this.filtroInput= argument
      this.$emit('filtraAncora', argument)
    }
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
