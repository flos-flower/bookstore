<template>
    <div class="book">
        <img v-bind:src="require(`@/assets/${bookinfo.pic}`)">
        <p>{{bookinfo.name}}</p>
        <p>{{bookinfo.genre}}</p>
        <p><span class="rating">{{bookinfo.rating}}</span></p>
        <p class ="cost">{{bookinfo.cost}}</p>
        <p v-if='bookinfo.availability'>Есть в наличии</p>
        <p v-else>Нет в наличии</p>
        <p class="about"><span class='gray-color-text'>Аннотация</span><br>{{bookinfo.about}}</p> 
    </div>
</template>
    
<script>
export default {
    props:['bookinfo']
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Lato:wght@300&family=Nunito:wght@200&family=Open+Sans:wght@300;400&display=swap');

.gray-color-text {
    color: rgba(188, 183, 183, 0.8);
}
.book:hover {
    box-shadow: 0px 0px 6px 1px rgb(187, 187, 187);
}
.book {
    white-space: nowrap;
    border-radius: 0.17rem;
    margin: 2rem;
    width:11rem;
    height:auto;
    padding:1rem;
    cursor: pointer;
}
img {
    width: 9rem;
    height: 14rem;
    margin: 0 1rem 0.5rem 1rem;
}
p {
    margin: 0.1rem 0;
}
.rating::after {
    content:"⭐";
}

.cost::after {
    content:" ₽";
}

.about {
    overflow: hidden;
    text-overflow: ellipsis;
}

.about:hover {
    overflow: visible;
    text-overflow: inherit;
    background: #fff;
    position: absolute;
    left:auto;
    top:auto;
    width: 500px;
    max-width: 20rem;
    border: 1px solid #eaebec;
    padding: 0 .5rem;
    box-shadow: 0 2px 4px 0 rgba(0,0,0,.28);
    white-space: normal;
    word-wrap: break-word;
    display:block;
    color:black;
    margin-top:-1.25rem;
}

.rate_btn {
   border-width: 0;
   background-color: rgb(255, 255, 255);
   cursor: pointer;
   font-family: 'Open Sans', sans-serif;
   border-radius: 0.1rem;
}

.rate_btn:hover {
    background-color: rgb(239, 239, 239);
}
</style>