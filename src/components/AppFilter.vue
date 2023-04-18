<script>
import { store } from '../store';
export default{
    name: "AppFilter",
    emits: ["filter"],
    data(){
        return{
            store,
            archetypesOptions:["Alien" , "Ally of Justice", "Ancient Gear"]
        }
    }
    
}

</script>

<template>
    <div class="filter-section">
        <div class="container d-flex justify-content-center ">
            <select class="form-select w-25 mx-2" name="archetype" id="archetype" v-model="store.selectedArchetype">
                <option value="">All</option>
                <option :value= "archetype" v-for="archetype in archetypesOptions">{{ archetype }}</option>
            </select>
            <button @click= "$emit('filter')" class="btn btn-success">Filtra</button>
        </div>
        <h4 class="text-center">Carte trovate: {{ store.cards.length }} </h4>
    </div>
    
</template>

<style scoped lang="scss">
.filter-section{
    height: 50px;
    background-color: rgb(41, 41, 59);
    h4{
        color: white;
    }

}


</style>