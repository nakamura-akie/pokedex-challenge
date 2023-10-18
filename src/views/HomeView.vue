<script setup>
import { onMounted, reactive, ref } from "vue";
import PokemonCard from "../components/PokemonCard.vue"
import axios from "axios";

let pokemonSelected = reactive(ref());

onMounted(()=>{
  getPokemonData()
})

function getRandomInt(min, max) {
  return Math.floor(Math.random() * (max - min + 1)) + min;
}

function getPokemonData() {
  axios.get("https://pokeapi.co/api/v2/pokemon/" + getRandomInt(1,151))
  .then(res => res.data)
  .then(res => pokemonSelected.value = res);
}

const randomSelection = () => {
  getPokemonData()
}
</script>

<template>
  <main>
    <div class="container">
      
      <div>
        <div class="card" style="width: 24rem;">
          
          <PokemonCard
          :name="pokemonSelected?.name"
          :xp="pokemonSelected?.base_experience"
          :types="pokemonSelected?.types"
          :height="pokemonSelected?.height"
          :weight="pokemonSelected?.weight"
          :img="pokemonSelected?.sprites.other.dream_world.front_default"
          />

        </div>

        <div class="d-grid gap-2 col-6 mx-auto" style="width: 18rem;">
          <button 
          type="button" 
          class="btn btn-danger"
          @click="randomSelection()"
          >
          New Pokemon
        </button>
        </div>
      </div>

    </div>
  </main>
</template>

<style scoped>
button {
  align-items: center;
  margin-top: 50px;
}

.card {
  margin: auto;
  width: 50%;
  border: 15px solid rgb(247, 206, 73);
  padding: 10px;
  margin-top: 50px;
  background: rgba(212, 187, 146, 0.532);
}
</style>