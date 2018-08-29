<template>
  <div id="app">
    <vs-row vs-w="12">
      <vs-col vs-type="flex" vs-justify="center" vs-align="center" vs-w="12">
        <img src="../src/assets/header.png">
      </vs-col>
      <vs-col vs-type="flex" vs-justify="center" vs-align="center" vs-w="12">
      </vs-col>
    </vs-row>

    <vs-row vs-w="12">

      <vs-col
        v-for="(item, index) in cards" :key="index"
        vs-type="flex"
        vs-justify="center"
        vs-align="center"
        vs-w="2"
      >
        <vs-card
          actionable
          @vs-click="item.show = true"
        >
          <vs-card-body>
            <span
              v-if="!item.show"
            >
              <img
                :src="require(`@/assets/${item.img}`)"
                class="img"
                alt="Card"
              >
            </span>
            <span v-else>
              Что у нас тут?
            </span>
          </vs-card-body>
        </vs-card>
      </vs-col>

    </vs-row>

  </div>
</template>

<script>
  import { mapState } from 'vuex'

  export default {
    name: 'App',
    data() {
      return {
        current: [],
        initCards: []
      }
    },
    computed: mapState({
      time: state => state.time,
      moves: state => state.moves,
      cards: state => state.cards
    }),
    mounted() {
      this.initCards = this.cards;
      for (let index = 0; index < this.initCards.length; index++) {
        const element = this.initCards[index];
        element.show = false;
      }
    }
  }
</script>

<style>
  html {
    background-color:#292e2a;
  }
  .vs-card {
    background-color:white;
  }
  .img {
    width: 100%;
  }
  #app {
    max-width: 1000px;
    margin: 0 auto;
    padding: 1.5rem 1.5rem;
  }
</style>
