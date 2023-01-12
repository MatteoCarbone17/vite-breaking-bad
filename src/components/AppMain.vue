<script>
import { store } from "../store.js";
import axios from "axios";
import MainTopComponent from "./MainTopComponent.vue";

export default {
    name: "AppMain",
    data() {
        return {
            store,
            cardList: [],
            ArchList: [],
            ApiUrl: "https://db.ygoprodeck.com/api/v7/cardinfo.php?num=10&offset=0",
        };
    },
    methods: {
        getCard() {
            axios.get(this.ApiUrl, {
               
            })
                .then((response) => {
                this.cardList = response.data.data;
                console.log(this.cardList);
            });
        },
        getArchetype(value){
            axios.get(this.ApiUrl, {
                params:{
                    archetype:value,
                }
            })
            .then((response) => {
               this.ArchList = response.data.archetype;
               console.log(this.ArchList);
                console.log('funzione avviata getArchetype ')

             });

        },
    },
    created() {
        this.getCard();
        this.getArchetype();
    },
    components: {
        MainTopComponent,
        }
}
</script>

<template>
    <div>
        <MainTopComponent @selectTypeArch="getArchetype(value)"/> 
        <section class="main-section">
            <div class="wrapper-cards">
                <div class="cards" v-for="card in cardList">
                    <img :src="card.card_images[0].image_url_small" alt="">   
                </div>
            </div>
    
        </section>
    </div>
   
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
            width: calc((100% / 5) );

        }
    }
}


</style>
