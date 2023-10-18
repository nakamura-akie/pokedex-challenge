<script setup>
const pokemon = defineProps(["name" , "urlBaseSvg"])
</script>


<template>
    <div class="col-4 col-md-6 col-xl-3">
        <div class="card p-2 mb-3 cardListPokemon">
            <p class="text-center">{{ pokemon.name }}</p>
            <img 
            :src="urlBaseSvg" class="card-img-top" 
            alt="..."
            height="80"
            />
        </div>
    </div>
</template>


<style scoped>
.cardListPokemon{
    background: #ffcf33b3;
    cursor: pointer;
}

.cardListPokemon:hover {
    background: #ffcf33;
    cursor: pointer;
}

.cardListPokemon img:hover {
    padding: .1rem;
}
</style>