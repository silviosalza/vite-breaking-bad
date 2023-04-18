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
        const paramsRequested = {
            num: 100,
            offset: 0,
          }

          if( store.selectedArchetype ){
            paramsRequested.archetype = this.store.selectedArchetype
          }
        axios.get("https://db.ygoprodeck.com/api/v7/cardinfo.php", {
          params: paramsRequested
          
        }).then((resp)=>{
          this.store.cards = resp.data.data;
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
