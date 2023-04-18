<script >
import AppHeader from './components/AppHeader.vue';
import CardList from './components/CardList.vue';
import axios from "axios";
import {store} from "./store";
import AppFilter from './components/AppFilter.vue';
export default{
  components: {
    AppHeader,
    CardList,
    AppFilter
  },
  data(){
    return{
      store
    }

  },
  mounted(){
        axios
        .get("https://db.ygoprodeck.com/api/v7/cardinfo.php" ,{
          params: {
            num: 100,
            offset: 0
          }
        })
        .then((resp) => {
        this.store.cards = resp.data.data;
    })
    },
    methods: {
      handlefilter(){
        axios.get("https://db.ygoprodeck.com/api/v7/cardinfo.php", {
          params: {
            num: 100,
            offset: 0,
            archetype: this.store.selectedtype
          }
        }).then((resp)=>{
          this.store.cards = resp.data.results;
        })
      }
    }
}

</script>

<template>
<AppHeader title="Yu-Gi-Oh API"/>
<AppFilter @filter="handlefilter"/>
<CardList/>

  
</template>

<style lang="scss" >
@use "./styles/general.scss";

</style>
