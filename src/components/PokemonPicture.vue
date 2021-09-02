<template>
    <div class="pokemon-container">
        <img  :src="imgSrc"
                class="hidden-pokemon"
                alt="pokemon">
       <img     v-if="showPokemon"
                :src="imgSrc" 
                class="fade-in"
                alt="pokemon"> 

    </div>
</template>

<script>
export default {

//Number, required
    props:{
       pokemonId: {
           type: Number,
           required: true
       },
       showPokemon: {
           type: Boolean,
           required: true,
           default: false
       }
    },
    computed: {
        imgSrc(){
            return `https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/other/dream-world/${this.pokemonId}.svg`
        }
    }

}
</script>

<style scoped>
/*Definir este estyle se define de forma global para todos para limitarlo al componente se pone scoped */
.pokemon-container {
    height: 200px;
}
img {
    height: 200px;
    position: absolute;
    left: 0;
    right: 0;
    margin: 0 auto; 
    user-select: none;
    -moz-user-select: none;
    -ms-user-select: none;
    -webkit-user-drag: none;
    -webkit-user-select: none;
}
.hidden-pokemon {
    filter: brightness(0);
}

</style>