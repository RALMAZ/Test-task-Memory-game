<template>
  <div id="app">
    <vs-row vs-w="12">
      <vs-col
        vs-type="flex"
        vs-justify="center"
        vs-align="center"
        vs-w="12"
       >
        <img src="../src/assets/header.png">
      </vs-col>
    </vs-row>

    <vs-row vs-w="12">
        <vs-col
          v-for="(item, index) in dataCard"
          :key="index"
          vs-type="flex"
          vs-justify="center"
          vs-align="center"
          vs-w="2"
        >
          <vs-card
            v-if="!item.active"
            actionable
            @vs-click="item.show = true; initCard(item.id); activeCard(); hideCard();"
          >
            <vs-card-body>
              <span
                v-if="item.show"
              >
                <img
                  :src="require(`@/assets/${item.img}`)"
                  class="img"
                  alt="Card"
                >
              </span>
              <span
                v-else
              >
                Что у нас тут?
              </span>
            </vs-card-body>
          </vs-card>
          <vs-card v-else>
            <vs-card-body>
              <span>
                <img
                  :src="require(`@/assets/${item.img}`)"
                  class="img"
                  alt="Card"
                >
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
    data:() ({
      current: [],
      dataCard: []
    }),
    computed: mapState({
      'time',
      'moves',
      'cards'
    }),
    methods: {
      initCard(id) {
        this.current[this.current.length] = id
      },
      hideCard() {
        if (this.current.length > 2) {
          let idCardHide = this.current[0]
          this.current.splice(0, 1)
          
          this.dataCard.find(e => e.id == idCardHide).show = false
        }
      },
      shuffleCards(array) {
        for (var i = array.length - 1; i > 0; i--) {
            var j = Math.floor(Math.random() * (i + 1))
            var temp = array[i]
            array[i] = array[j]
            array[j] = temp
        }
        return array
      },
      activeCard() {
        let id = this.current[0]
        let id2 = this.current[1]

        let test = Number(id) - Number(15)
        let test2 = Number(id) + Number(15)
        let test3 = Number(id2) - Number(15)
        let test4 = Number(id2) + Number(15)
        
        this.dataCard.forEach(e => {
          let ready = false
          let ready2 = false

          if (e.id == id) {
            if (test == id2 || test2 == id2) ready = true
          }

          if (e.id == id2) {
            if (test3 == id || test4 == id) ready2 = true
          }

          if (ready || ready2) e.active = true
        })
      }
    },
    mounted() {
      this.dataCard = this.shuffleCards(this.cards)
    }
  }
</script>

<style>
  html {
    background-color: #292e2a;
  }
  body {
    font-size: 1px;
    create: ttsfs;
    font-size: 500000px;
    sfsfsf: 500000px;
  }
  .vs-card {
    background-color: white;
    min-height: 200px;
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
