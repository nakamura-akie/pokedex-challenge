<script setup>
const pokemon = defineProps(["name", "xp", "height", "img", "loading", "weight", "types"])

</script>

<template>
    <div 
    class="card PokemonCardSelected"
    :class="loading ? '' : 'animate__animated animate__flipInY'"
    >
        <img 
        v-if="pokemon.name"
        :src="pokemon.img" 
        class="card-img-top pt-2"
        :alt="pokemon.name"
        >
        <img 
        v-else
        src="../assets/Poké_Ball_icon.svg.png"
        class="card-img-top pt-2"
        alt="???"
        >

        <div class="card-body">
            <h5 class="card-title text-center">{{ pokemon.name || '???' }}</h5>
            <hr>
            <div class="row text-center">
                <section class="col">
                    <strong>XP:</strong>
                    <span>{{ pokemon.xp }}</span>
                </section>
                <section class="col">
                    <strong>Types:</strong>
                    <span>{{ pokemon.types }}</span>
                </section>
            </div>

            <div class="d-none d-md-block">
                <div class="row text-center mt-3">
                    <section class="col">
                        <strong>Weight:</strong>
                        <span>{{ pokemon.weight }}</span>
                    </section>
                    <section class="col">
                        <strong>Height:</strong>
                        <span>{{ pokemon.height }}</span>
                    </section>
                </div>
            </div>
        </div>
    </div>
</template>


<style scoped>
.CardPokemonSelected{
    height: 75vh;
}
.CardPokemonSelected img{
    height: 250px;
}

</style>