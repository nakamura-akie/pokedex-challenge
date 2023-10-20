<template>
  <div class="container mt-4 text-body-secondary">
    <div class="card" style="margin-bottom: 100px">
      <h1 class="text-center">Goparity Pokedex</h1>
      <div class="card-body">
        <h2>Challenge</h2>
        <p>Using Vue.js and Axios, the challenge was to retrieve a random Pokémon from the PokéAPI (https://pokeapi.co/) and show some basic information about it.
Every time the page loads a new random Pokémon is loaded. Also, there is a button to change the Pokémon (without reloading the page).</p>
        <hr>
        <h2>Considerations</h2>
        <br>
        <h4>About the final solution</h4>
        <p>
          For the final solution for this challenge, I choose to mantain the funcionalities to the minimum 
          required, since I was handling with new tools and I had little experience developing for Front End. 
          Yet I opted for an About page to demonstrate some use and knowledge about router.
        </p>
        <p>
          To minimize the data and for pure nostalgia also, I prefer to manage just the 
          firsts 151 pokémons, because they are the ones I remember from my childhood.
        </p>
        <h4>About the design choices</h4>
        <p>
          I used Bootstrap to speed up the process of the stylization. 
        I choose to keep the page clean and focused on the main component. </p>
        <p> Also for nostalgia, I decide to keep the card component style similar to the Pokemon Card Game,
          but I simplify the background, for it to be cleaner.
        </p>
      </div>
    </div>
  </div>
</template>

<style>
</style>
