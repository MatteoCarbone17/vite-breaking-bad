<script>
import { store } from "../store.js";
import axios from "axios";
// import MainTopComponent from "./MainTopComponent.vue";

export default {
    name: "AppMain",
    data() {
        return {
            store,
            cardList: [],
        };
    },
    methods: {
        getCard() {
            axios.get("https://db.ygoprodeck.com/api/v7/cardinfo.php?num=10&offset=0", {})
                .then((response) => {
                /* console.log(response.data.data) */
                this.cardList = response.data.data;
                console.log(this.cardList);
            });
        }
    },
    created() {
        this.getCard();
    },
    components: {
        //  MainTopComponent,
         }
}
</script>

<template>
    <!-- <MainTopComponent/> -->
    
    <section class="main-section">
        <div class="wrapper-cards">
            <div class="cards" v-for="card in cardList">
                <img :src="card.card_images[0].image_url_small" alt="">
              
             
            </div>

        </div>

    </section>
   
</template>

<style scoped lang="scss">
section.main-section{
    background-color: rgb(212, 143, 56);
    padding: 5rem;
   

    div.wrapper-cards{
        background-color: white;
        
        margin: 0 auto;
        display: flex;
        flex-wrap: wrap;
       

        div.cards{
            width: calc((100% / 5)  );

        }
    }
}


</style>
