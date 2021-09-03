<template>
    <h1>¿Quién es este pokémon?</h1>
    <!--TODO img-->
    <PokemonPicture :pokemonId="150" :showPokemon="false" />

    <PokemonOptions :pokemons="pokemonArr"/>
    <!--TODO opciones-->
    <!-- En VUE 2 se pone en un div<div></div>-->
</template>

<script>

import PokemonPicture from '@/components/PokemonPicture'
import PokemonOptions from '@/components/PokemonOptions'

import getPokemonOptions from '@/helpers/getPokemonOptions'

//console.log(getPokemonOptions())

export default {
    name: 'PokemonPage',
    components: {
        PokemonPicture,
        PokemonOptions
    },
    data(){
        return {
            pokemonArr: []
        }
    },
    methods: {
        async mixPokemonArray() {
            this.pokemonArr = await getPokemonOptions()
        }
    },
    mounted(){
        this.mixPokemonArray()
    }

    //Handler and target is reactive property or object
    
}
</script>

