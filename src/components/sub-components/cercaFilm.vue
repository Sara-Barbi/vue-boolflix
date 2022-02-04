<template>
    <div>
       <input 
          type="text"
          placeholder="search your film!"
          v-model="inputCerca"
        
          >

        <button @click="$emit('filtra',inputCerca)" >Cerca</button>
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

<style>

</style>