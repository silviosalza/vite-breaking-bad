<script >
import AppHeader from './components/AppHeader.vue';
import CardList from './components/CardList.vue';
import axios from "axios";
import {store} from "./store";
export default{
  components: {
    AppHeader,
    CardList
  },
  data(){
    return{
      store
    }

  },
  mounted(){
        axios
        .get("https://db.ygoprodeck.com/api/v7/cardinfo.php?num=20&offset=0")
        .then((resp) => {
          console.log(resp);
        // const myData = resp.data.data;
        // console.log(myData);
        this.store.cards = resp.data.data;
    })
    }
}

</script>

<template>
<AppHeader title="Yu-Gi-Oh API"/>
<CardList/>

  
</template>

<style lang="scss" >
@use "./styles/general.scss";

</style>
