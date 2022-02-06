<template>
    <div>
       <input 
          type="text"
          placeholder="search your film!"
          v-model="inputCerca"
          class="stileRicerca"
        
          >

        <button class="buttonCerca" @click="$emit('filtra',inputCerca)" >Cerca</button>
    </div>
</template>

<script>



export default {
   name: "cercaFilm",
   props:{

   },
   data(){
       return{
           inputCerca:""
       }
   }

}
</script>

<style scoped lang="scss">

.stileRicerca{
    background-color: rgb(59, 59, 59);
    border-radius: 20px;
    color: white;
}
.buttonCerca{
    border-radius: 20px ;
    background-color: rgb(34, 32, 32);
    color: antiquewhite;
}

</style>