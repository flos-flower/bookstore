<template>
    <div class="rev_area">
        <label for="txt_area">Отзыв:</label>
        <br>
        <textarea id="txt_area" v-model="book_rev.rev" class="a_name"></textarea>
        <br>
        <input type="text" placeholder="Ваше имя" v-model="book_rev.rev_owner" class="a_name">
        <input type="text" placeholder="Название произведения" v-model="book_rev.rev_name" class="a_name">
        <button @click="add" class="btn">Опубликовать</button>
        <div class="oth_rev">   
            <p><span>Другие отзывы:</span><span class="rev_sort">Видеть отзывы только на: <input type="text" v-model="sort_name"><button class="btn_sort" @click="to_sort">Отсортировать</button><button class="btn_sort" @click="revert">Сбросить</button></span></p>
            <div v-for="(book, index) in books_sort" :key="index" class="rev_div">{{book.name}}:
                <div v-for="(review, new_index) in book.reviews" :key="new_index">
                    {{review.name}}: <br>{{review.review}}
                </div>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    props:['books','books_sort'],
    data(){
        return{
            book_rev:{
                rev:"",
                rev_name:"",
                rev_owner:""
            },
            sort_name:""   
        }
    },
    methods:{
        add(){
            this.$emit('add-rev',this.book_rev);
            this.book_rev.rev="";
            this.book_rev.rev_name="";
            this.book_rev.rev_owner="";
        },
        to_sort(){
            this.$emit('sort-rev',this.sort_name);
            this.sort_name = "";
        },
        revert(){
            this.$emit('sort-revert')
        }
    }
}
</script>
<style>
#txt_area{
    overflow: auto;
    outline: none;
    resize: none;
    height: 6rem;
    width:70%;
    margin-top:0.4rem;
}

.rev_area{
    margin-left: 3rem;
}

.rev_area input {
    margin-right: 0.5rem;
}

.oth_rev{
    margin-top: 1rem;
}

.a_name {
    height: 1.2rem;
    border:0.05rem solid #404040;
    border-radius:0.15rem;
}

.rev_div{
    margin-top:0.7rem;
    border:0.05rem solid #404040;
    border-radius: 0.15rem;
    padding:0.2rem;
}

.rev_sort{
    float:right;
}

.btn_sort{
    font-family: 'Open Sans', sans-serif;
    border-radius: 2px;
    background-color: #404040;
    color: white;
    border-width: 0;
    cursor: pointer;
    margin-left:0.2rem;
}
</style>