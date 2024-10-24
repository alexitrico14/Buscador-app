<script>
import axios from 'axios';

export default {
    data() {
        return {
            gender: 'male',
            randomUser: null,
        };
    },
    methods: {
        async buscarUsuarioPorGenero() {
            try {
                const url = `https://randomuser.me/api/?gender=${this.gender}`;
                const { data } = await axios.get(url);
                this.randomUser = data.results[0];
            } catch (error) {
                console.error("Error al buscar usuario por género", error);
                this.randomUser = null;
            }
        },
    },
};
</script>

<template>
    <div class="box">
        <h2>Buscador de usuario por género</h2>
        <select v-model="gender">
            <option value="male">Hombre</option>
            <option value="female">Mujer</option>
        </select>
        <button @click="buscarUsuarioPorGenero">Buscar</button>

        <div v-if="randomUser" class="result">
            <h2>{{ randomUser.name.first }} {{ randomUser.name.last }}</h2>
            <img :src="randomUser.picture.large" alt="Foto de perfil" class="profile-pic" />
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