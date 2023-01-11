<script>
import { store } from "../store.js";
import axios from "axios";

export default {
    name: 'AppMain',
    data() {
        return {
            store,
            cardList: [],
        }
    },

    methods: {
       getCard(){
        axios.get( 'https://db.ygoprodeck.com/api/v7/cardinfo.php?num=10&offset=0', {
        })
            .then((response) => {
                this.cardList = response.data.name; 
                console.log(this.cardList);
            })
            
       }
    },

    created() {
        this.getCard();
    },
}
</script>

<template>
    <section class="d-flex justify-content-center">
        <div class="text-bg-danger"  v-for="card in cardList" >
            {{ card }}
        </div>

    </section>

</template>

<style scoped>

</style>
