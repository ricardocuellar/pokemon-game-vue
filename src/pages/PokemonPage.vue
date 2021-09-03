<template>

    <h1 v-if="!pokemon">Espere por favor ...</h1>
    <div v-else>
        <h1>¿Quién es este pokémon?</h1>
        <!--TODO img-->
        <PokemonPicture :pokemonId="pokemon.id" :showPokemon="showPokemon" />

        <PokemonOptions :pokemons="pokemonArr"/>
        <!--TODO opciones-->
        <!-- En VUE 2 se pone en un div<div></div>-->

    </div>

    
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
            pokemonArr: [],
            pokemon: null,
            showPokemon: false,
        }
    },
    methods: {
        async mixPokemonArray() {
            this.pokemonArr = await getPokemonOptions()
            const rndInt = Math.floor(Math.random() * 4)
            this.pokemon = this.pokemonArr[ rndInt ]
        }
    },
    mounted(){
        this.mixPokemonArray()
    }

    //Handler and target is reactive property or object
    
}
</script>

