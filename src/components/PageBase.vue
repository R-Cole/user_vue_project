
<template>
  <div class="container">
        <h1>{{ pageTitle }}</h1>
        <button
          v-if="caseNumber === 1"
          :class="{'button-off-1': !detectMode, 'button-on-1': detectMode}"
          @click="setDetector()">
          {{ buttonMessage }}
        </button>
        <button
          v-if="caseNumber === 2"
          :class="{'button-off-2': !detectMode, 'button-on-2': detectMode}"
          @click="setDetector()">
          {{ buttonMessage }}
        </button>
        <br/>
        <br/>

        <!-- 1 -->
        <div  v-if="caseNumber === 1">
          <table align="center">
          <thead>
            <tr>
              <th>ID</th>
              <th>Name</th>
              <th>Last Login Date</th>
              <th>Login Count</th>
              <th>Project Count</th>
            </tr>
          </thead>
          <tbody>
          <tr :key="user.id"
            v-for="user in theUsers"
            :class="{
                'red-style' : user.login_count === baseNumber_1,
                'white-style': user.login_count > baseNumber_2,
                'white-style': !detectMode}"
            >
            <td>{{ user.id }}</td>
            <td>{{ user.username }}</td>
            <td>{{ formatDate(user.last_login) }}</td>
            <td>{{ user.login_count }}</td>
            <td>{{ user.project_count }}</td>
          </tr>
          </tbody>
          </table>
        </div>

        <!-- 2 -->
        <div  v-if="caseNumber === 2">
          <table align="center">
          <thead>
            <tr>
              <th>ID</th>
              <th>Name</th>
              <th>Last Login Date</th>
              <th>Login Count</th>
              <th>Project Count</th>
            </tr>
          </thead>
          <tbody>
          <tr :key="user.id"
            v-for="user in theUsers"
            :class="{
                'green-style' : user.login_count >= baseNumber_1,
                'white-style': user.login_count === baseNumber_2,
                'white-style': !detectMode}"
            >
            <td>{{ user.id }}</td>
            <td>{{ user.username }}</td>
            <td>{{ formatDate(user.last_login) }}</td>
            <td>{{ user.login_count }}</td>
            <td>{{ user.project_count }}</td>
          </tr>
          </tbody>
          </table>
        </div>
        
  </div>
</template>
<script>

import users from '../assets/users.json'
import moment from 'moment' 
 
export default {
  name: 'PageOne',
  data: () => ({
    theUsers: users,
    detectMode: false 
  }),
  props: {
    caseNumber: Number,
    pageTitle: String,
    baseNumber_1: Number,
    baseNumber_2: Number,
    buttonMessage: String,
    colorHighlight: String
  },
  methods: {
    setDetector: function(){
       
      if(this.detectMode){
        this.detectMode = false
      }
      else{
        this.detectMode = true
      }
    },
    formatDate: function(date){
       return moment(date).format('MMMM Do YYYY, h:mm:ss a')
    } 
  } 
}
</script>
<style scoped>

  .container {
    text-align: center;
  }
   
  h1 {
    margin-left: 50px; 
    text-align: center;
    color: rgb(73, 73, 97);
  } 
 
  button {
    padding: 7px 15px;
    font-size: 14px;
    cursor: pointer;
    text-align: center;
    text-decoration: none;
    outline: none;
  }

  .button-on {
    color: rgb(255, 212, 71);
    background-color: rgb(245, 65, 65);
    border: none;
  }

  .button-off {
    color: rgb(124, 45, 45);
    background-color: rgb(206, 204, 204);
    border: none;
  }
  
  .button-off:hover {
    color: rgb(255, 248, 224);
    background-color: rgb(255, 100, 100);
  }
 
  .red-style {
    color: yellow;
    background:red;
  }

  .green-style {
    color: yellow;
    background:rgb(41, 109, 55);
  }

  .white-style {
    color: rgb(73, 73, 97);
    background: white;
  }

  table
  { 
    text-align: center;
    border-collapse: collapse;
    border-spacing: 0px;
  }
  table, th, td
  {
    padding: 15px;
    border: 1px solid rgb(163, 156, 156);
  }

</style>