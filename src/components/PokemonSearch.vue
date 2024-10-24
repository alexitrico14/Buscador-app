<script>
import axios from 'axios';

export default {
    data() {
        return {
            pokemonName: '',
            pokemon: null,
        };
    },
    methods: {
        async buscarPokemon() {
            try {
                const url = `https://pokeapi.co/api/v2/pokemon/${this.pokemonName.toLowerCase()}`;
                const { data } = await axios.get(url);
                this.pokemon = data;
            } catch (error) {
                console.error("Error al buscar Pokémon", error);
                this.pokemon = null;
            }
        },
    },
};
</script>

<template>
    <div class="box">
        <h2>Buscador de Pokémon</h2>
        <input v-model="pokemonName" placeholder="Ingresa el nombre o ID del Pokémon" />
        <button @click="buscarPokemon">Buscar</button>

        <div v-if="pokemon" class="result">
            <h2>{{ pokemon.name }} (ID: {{ pokemon.id }})</h2>
            <img :src="pokemon.sprites.front_default" alt="Imagen del Pokémon" class="pokemon-pic" />
        </div>
    </div>
</template>

<style scoped>
/* Box*/
.box {
    background-color: #f9f9f9;
    border: 2px solid #ccc;
    padding: 20px;
    margin: 20px;
    border-radius: 10px;
    text-align: center;
    width: 300px;
    box-shadow: 0px 4px 6px rgba(0, 0, 0, 0.1);
}

/* Input y button */
input,
select {
    margin-top: 10px;
    padding: 8px;
    border: 1px solid #ddd;
    border-radius: 5px;
    width: 80%;
}

button {
    margin-top: 15px;
    padding: 10px 20px;
    border: none;
    background-color: #5cb85c;
    color: white;
    font-size: 14px;
    border-radius: 5px;
    cursor: pointer;
}

button:hover {
    background-color: #4cae4c;
}

/* result */
.result {
    margin-top: 20px;
}

.profile-pic,
.pokemon-pic {
    margin-top: 10px;
    width: 100px;
    height: 100px;
    border-radius: 50%;
    border: 2px solid #ddd;
    object-fit: cover;
}
</style>