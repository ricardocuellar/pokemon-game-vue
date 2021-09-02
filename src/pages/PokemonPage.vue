<template>
    <h1>¿Quién es este pokémon?</h1>
    <!--TODO img-->
    <PokemonPicture />

    <PokemonOptions />
    <!--TODO opciones-->
    <!-- En VUE 2 se pone en un div<div></div>-->
</template>

<script>

import PokemonPicture from '@/components/PokemonPicture'
import PokemonOptions from '@/components/PokemonOptions'


export default {
    name: 'PokemonPage',
    components: {
        PokemonPicture,
        PokemonOptions
    }
    
}
</script>

