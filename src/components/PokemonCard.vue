<script setup>
const pokemon = defineProps(["name", "xp", "types", "height", "weight", "img"])

</script>

<template>
    <div class="PokemonCard">

        <div class="card-body">
            <h4 class="card-title">{{ pokemon.name }}</h4>
            <img v-if="pokemon.name" :src="pokemon.img" class="card-img-top pt-2" :alt="pokemon.name">
            <hr>
            
            <div class="row text-center">
                <section class="col">
                    <strong>XP: </strong>
                    <span>{{ pokemon.xp }}</span>
                </section>
                <section class="col">
                    <strong>Types:</strong>
                    <ul id="example-1">
                        <li v-for="type in types">
                            {{ type.type.name }}
                        </li>
                    </ul>
                </section>

                <div class="d-none d-md-block">
                    <div class="row text-center mt-3">

                        <section class="col">
                            <strong>Height: </strong>
                            <span>{{ pokemon.height }}</span>
                        </section>

                        <section class="col">
                            <strong>Weight: </strong>
                            <span>{{ pokemon.weight }}</span>
                        </section>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>


<style scoped>
.PokemonCard {
    height: 45vh;
}

.PokemonCard img {
    padding-top: 20px;
    height: 250px;
}
</style>