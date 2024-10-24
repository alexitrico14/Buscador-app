<script>
import GitHubUser from './components/GitHubUser.vue';
import PokemonSearch from './components/PokemonSearch.vue';
import RandomUser from './components/RandomUser.vue';

export default {
  components: {
    GitHubUser,
    PokemonSearch,
    RandomUser,
  },
};
</script>

<template>
  <div class="container">
    <GitHubUser />
    <PokemonSearch />
    <RandomUser />
  </div>
</template>


<style scoped>
.container {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  margin-top: 50px;
}
 
</style>
