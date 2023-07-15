<template>
    <div class="shelve">
        <Book v-for="(book, index) in shelves" v-bind:key="index" v-bind:bookinfo="book"/>
    </div>
</template>

<script>
import Book from "./BookInfo.vue"

export default {    
    props:['shelves'],
    components:{
        Book
    }
}
</script>

<style>
.shelve {
    display: flex;
    flex-wrap: wrap;
}
</style>