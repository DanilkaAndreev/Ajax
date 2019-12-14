<template>
  <div id="app">
    <!-- <img alt="Vue logo" src="./assets/logo.png">
    <HelloWorld msg="Welcome to Your Vue.js App"/> -->
    
    <UserCard v-if="user" :user="user"></UserCard>
    {{user}}
  
    
  </div>
</template>

<script>
import UserCard from'./components/UserCard.vue'

export default {
  name: 'app',
  components: {

    UserCard
  },
  data(){
    return {
      user: null
    }
  },
  mounted() {
    this.axios.get('https://randomuser.me/api').then((response)=>{
      console.log('response', response.data)
      this.user = response.data.results[0]
    }).catch(err=>{
      console.log('errr', err)
    })
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
</style>
