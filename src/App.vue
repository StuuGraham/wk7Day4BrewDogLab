<template>
  <div id="app">
    <h1>Brewdog Beers</h1>
    <div class="main-container">
      <beers-list :beers="beers"></beers-list>
      <beer-detail :beer="selectedBeer"></beer-detail>
    </div>

    <button v-if="!favouriteBeers.includes(selectedBeer)" v-on:click="addToFavourites">Add Beer</button>
    <favourite-beers :favouriteBeers="favouriteBeers"></favourite-beers>

  </div>
</template>

<script>
import BeersList from './components/BeersList.vue';
import BeerSelect from './components/BeerSelect.vue';
import BeerDetail from './components/BeerDetail.vue';
import BeerFaves from './components/BeerFaves.vue';
import {eventBus} from './main';

export default {
  name: 'App',
  data(){
    return {
      beers: [],
      selectedBeer: null,
      favouriteBeers: []
    };
  },

  mounted(){
    fetch('https://api.punkapi.com/v2/beers')
    .then(res => res.json())
    .then(beers => this.beers = beers);

    eventBus.$on('beer-selected', (beer) => {
      this.selectedBeer = beer;
    })
  },

  methods: {
    addToFavourites: function() {
      if(this.favouriteBeers.indexOf(this.selectedBeer) === -1) {
        this.favouriteBeers.push(this.selectedBeer);
      }
    }
  },

  components: {
    'beers-list': BeersList,
    'beer-detail': BeerDetail,
    'favourite-beers': BeerFaves
    
  },
}
</script>

<style>

</style>
