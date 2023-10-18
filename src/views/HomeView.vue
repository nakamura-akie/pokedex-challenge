<script setup>
import axios from 'axios'
import { onMounted, reactive, ref, computed } from 'vue'
import PokemonsList from "../components/PokemonsList.vue"
import PokemonCardSelected from "../components/PokemonCardSelected.vue"

let urlBaseSvg = ref("https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/other/dream-world/")
let pokemons = reactive(ref());
let searchPokemonField = ref("")
let pokemonSelected = reactive(ref());
let loading = ref(false)

onMounted(() => {
  axios.get('https://pokeapi.co/api/v2/pokemon?limit=151&offset=0')
    .then(response => response.data)
    .then(response => pokemons = response.results);
})

const pokemonsFiltered = computed(()=>{
  if(pokemons.value && searchPokemonField.value){
    return pokemons.value.filter(pokemon=>
      pokemon.name.toLowerCase().includes(searchPokemonField.value.toLowerCase())
    )
  }
  return pokemons.value;
})

const selectPokemon = async (pokemon) => {
  loading.value = true;
  await axios.get(pokemon.url)
  .then(response => response.data)
  .then(response => pokemonSelected.value = response)
  .catch(err => alert(err))
  .finally(()=> loading.value = false)

  console.log(pokemonSelected.value)
  
}

</script>

<template>
  <main>
    <div class="container text-body-secondary">
      
      <div class="row mt-4">
        <div class="col-sm-12 col-md-6">
          
          <PokemonCardSelected
          :name="pokemonSelected?.name"
          :xp="pokemonSelected?.base_experience"
          :weight="pokemonSelected?.weight"
          :height="pokemonSelected?.height"
          :types="pokemonSelected?.types"
          :img="pokemonSelected?.sprites.other.dream_world.front_default"
          :loading="loading"
          />

        </div>
  
        <div class="col-sm-12 col-md-6">
          <div class="card card-list">
            <div class="card-body row">
              
              <div class="mb-3">
                <label 
                hidden 
                for="searchPokemonField" 
                class="form-label">
                Search Pokemon
                </label>

                <input 
                v-model="searchPokemonField"
                type="text" 
                class="form-control" 
                id="searchPokemonField" 
                placeholder="Search Pokemon">
              </div>

              <PokemonsList
              v-for="pokemon in pokemonsFiltered"
              :key="pokemon.name"
              :name="pokemon.name"
              :urlBaseSvg="urlBaseSvg + pokemon.url.split('/')[6] + '.svg'"
              @click="selectPokemon(pokemon)"
              />
            </div>
          </div>
        </div>
      </div>

    </div>
  </main>
</template>

<style scoped>
.card-list{
  max-height: 75vh;
  overflow-y: scroll;
  overflow-x: hidden;
}
</style>