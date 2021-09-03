<template>

    <h1 v-if="!pokemon">Espere por favor ...</h1>
    <div v-else>
        <h1>¿Quién es este pokémon?</h1>
        <!--TODO img-->
        <!--We can use  CamelCase or Kebab-Case for components tags and attributes both are correct-->
        <PokemonPicture 
            :pokemon-id="pokemon.id" 
            :show-pokemon="showPokemon" />

        <PokemonOptions 
            :pokemons="pokemonArr"
            @selection-pokemon="checkAnswer"
            />
        <!--TODO opciones-->
        <!-- En VUE 2 se pone en un div<div></div>-->
        <!-- Remember: Bracket only when we want send arguments if not only reference >-->

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
        },
        checkAnswer(pokemonId){
            this.showPokemon = true
        }
    },
    mounted(){
        this.mixPokemonArray()
    }

    //Handler and target is reactive property or object
    
}
</script>

