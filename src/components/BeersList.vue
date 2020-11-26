<template>
    <div>
        <ul>
            <selected-beer v-for="(beer, index) in beers" :beer="beer" :key="index"></selected-beer>
        </ul>
    </div>
</template>

<script>
import {eventBus} from '../main'
import BeerSelect from './BeerSelect.vue';

export default {
    name: 'beers-list',
    props: ['beers'],
    components: {
        "selected-beer": BeerSelect
    }
}
</script>

<style>

</style>