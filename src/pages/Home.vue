<template>

  <div class="home">


    <div class="album py-5 bg-body-tertiary">
      <div class="container">

        <div class="row row-cols-1 row-cols-sm-2 row-cols-md-3 g-3">
          <div class="col" v-for="(item, idx) in state.items" :key="idx">
            <Card :item="item"/>

          </div>
        </div>
      </div>
    </div>

  </div>

</template>

<script>

import Card from "@/components/Card.vue";
import axios from "axios";
import {reactive} from "vue";

export default {

  name:"Home",
  components: {Card},
  setup(){

    const state = reactive({

      items:[]
    })


    axios.get("/api/items").then(({data}) => {

      console.log(data);
      state.items = data;

    })

    return {state}

  }
}

</script>

<style scoped>

</style>