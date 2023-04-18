<script>
import { store } from '../store';
export default{
    name:"CardList",   
    data(){
        return {
            store
        }
    }
}
</script>

<template>
    <section class="card-sect">
        <div class="container">
            <ul class="d-flex flex-wrap justify-content-center">
                <li class="col-2 m-1 " v-for="(card, index) in store.cards" :key="index">

                        <img :src= card.card_images[0].image_url  alt="">

                    <div class="card-name text-center">
                        {{ card.name }}
                    </div>

                    <div class="type text-center">
                        {{ card.archetype }}
                    </div>

                </li>
            </ul>
        </div>
    </section>
</template>

<style scoped lang="scss">
@use '../styles/partials/variables' as *;
.card-sect{
    background-color: $bg-color ;   
}
.container{
    background-color: rgb(41, 41, 59);
    padding-top: 1rem;
}
li{
    list-style: none;
    background-color: $bg-color ;   
}
img{
    width: 100%;
}
.card-name{
    color: white;
    font-weight:900
}
.type{
    color: black;
    font-weight:900
}

</style>