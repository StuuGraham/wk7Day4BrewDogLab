<template>
  <div v-if="beer">
    <h3>{{beer.name}}</h3>
    <br>
    <p>{{beer.tagline}}</p>
    <p>{{beer.description}}</p>
    <p>Alcohol %: {{beer.abv}}</p>
    <br>
    <img class="beer-img" :src="beer.image_url"/>
    <h4>Ingredients: </h4>
    <ul>
        <p>Malts:</p>
        <li id="beer-ingredients" v-for="(malt, index) in beer.ingredients.malt" v-bind:key="index">
            <span>{{malt.name}} - Added at: {{malt.add}}</span>
        </li>
        <p>Hops:</p>
        <li id="beer-ingredients" v-for="(hops, index) in beer.ingredients.hops" v-bind:key="index">
            <span>{{hops.name}} - Added at: {{hops.add}}</span>
        </li>
        <p>Yeast:</p>
        <li>
            <span>{{beer.ingredients.yeast}}</span>
        </li>
        <!-- <li id="beer-ingredients" v-for="(ingredient, index) in beer.ingredients" v-bind:key="index">
            <p>Malts: {{beer.ingredients.malt}}</p>
            <p>Hops: {{beer.ingredients.hops}}</p>
            <p>Yeast: {{beer.ingredients.yeast}}</p>
        </li> -->
    </ul>
    </div>
</template>

<script>
export default {
    name: 'beer-detail',
    props: ['beer']
}
</script>

<style>
    .beer-img {
        height: 250px;
        width: 100px;
    }
</style>