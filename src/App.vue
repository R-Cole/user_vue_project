<template>
  <div id="app">
    <button @click="page_Change(1)">PAGE 1</button><button @click="page_Change(2)">PAGE 2</button>

    <div v-if="page === 1">
      <PageBase
        :caseNumber="1" 
        pageTitle="Hello, this is page 1"
        :baseNumber_1="0"
        :baseNumber_2="0"
        buttonMessage="HIGHLIGHT 0 LOGIN USERS"
        colorHighlight="red-style"/>
    </div>

    <div v-if="page === 2">
      <PageBase
        :caseNumber="2"
        pageTitle="Hello, this is page 2"
        :baseNumber_1="1"
        :baseNumber_2="0"
        buttonMessage="HIGHLIGHT MORE THAN 1 LOGIN USERS"
        colorHighlight="green-style"/>
    </div>

  </div>
</template>

<script>

import PageBase from './components/PageBase.vue'

export default {
  name: 'app',
  components: {
    PageBase
  },
  data: () => ({
     page: 1
  }),
  methods: {
     page_Change(page){
       this.page = page
     },
  } 
}
</script>

<style>
  #app {
    font-family: 'Avenir', Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    margin-top: 60px;
  }

  button {
    margin-left: 40px;
    padding: 7px 15px;
    font-size: 14px;
    cursor: pointer;
    text-align: center;
    text-decoration: none;
    outline: none;
  }

  .button-on-1 {
    color: rgb(255, 212, 71);
    background-color: rgb(245, 65, 65);
    border: none;
  }

  .button-off-1 {
    color: rgb(124, 45, 45);
    background-color: rgb(206, 204, 204);
    border: none;
  }
  
  .button-off-1:hover {
    color: rgb(255, 248, 224);
    background-color: rgb(255, 100, 100);
  }

  .button-on-2 {
    color: rgb(255, 212, 71);
    background-color: rgb(75, 143, 36);
    border: none;
  }

  .button-off-2 {
    color: rgb(9, 53, 20);
    background-color: rgb(205, 206, 204);
    border: none;
  }
  
  .button-off-2:hover {
    color: rgb(255, 212, 72);
    background-color: rgb(85, 161, 78);
  }

</style>
