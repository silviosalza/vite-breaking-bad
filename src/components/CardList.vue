<script>
import axios from "axios";
export default{
    name:"CardList",
    mounted(){
        axios
        .get("https://db.ygoprodeck.com/api/v7/cardinfo.php?num=20&offset=0")
        .then((resp) => {
        const myData = resp.data.data;
        console.log(myData);
    })
    }
    
}
</script>

<template>
    <section class="card-sect">
        <div class="container">
            <h2>Carte</h2>
        </div>
    </section>
</template>

<style scoped lang="scss">

.card-sect{
    background-color: #D48F38 ;
    height: calc(100vh - 100px);
}

</style>