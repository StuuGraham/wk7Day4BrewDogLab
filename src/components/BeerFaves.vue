<template>
    <div id="favourite_beers">
        <h2>Favourite Beers</h2>
        <ul id="fave-beer-list">
            <li v-for="(beer, index) in favouriteBeers" v-bind:key="index">
                <span id="beer-name">Beer Name: {{beer.name}}</span>
                <br>
                <span id="beer-%"> Alc %: {{beer.abv}}</span>
                <br>
                <h4>Goes well with:</h4>
                <ul>
                    <li id="food-pair" v-for="(food, index) in beer.food_pairing" v-bind:key="index">
                        <span>{{food}}</span>
                    </li>
                </ul>        
                <br>
                <img id="beer-img" :src="beer.image_url"/>
                <br>
                <button v-on:click="deleteFave(index)">Remove From Favourites</button>
            </li>
        </ul>
    </div>
</template>

<script>
export default {
    name: 'favourite-beers',
    props: ['favouriteBeers'],

    methods: {
        deleteFave: function(index) {
            this.favouriteBeers.splice(index, 1)
        }

    }

}



</script>

<style>
#fave-beer-list {
    display: flex;
    flex-wrap: wrap;
}

 #beer-img {
     height: 250px;
     width: 100px;
 }
</style>