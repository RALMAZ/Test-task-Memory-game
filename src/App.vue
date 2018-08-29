<template>
  <div id="app">
    <vs-row vs-w="12">
      <vs-col vs-type="flex" vs-justify="center" vs-align="center" vs-w="12">
        <img src="../src/assets/header.png">
      </vs-col>
    </vs-row>

    <vs-row vs-w="12">
      
      <vs-col vs-type="flex" vs-justify="center" vs-align="center" vs-w="2">    
        <vs-card actionable>
          <vs-card-body>
            <span>Lorem ipsum dolor sit amet, consectetur adipiscing elit</span>
          </vs-card-body>
        </vs-card>
      </vs-col>

    </vs-row>

  </div>
</template>

<style>
  html {
    background-color:#292e2a;
  }
  .vs-card {
    background-color:white;
  }
  #app {
    max-width:1000px;
    margin: 0 auto;
    padding: 1.5rem 1.5rem;
  }
</style>
