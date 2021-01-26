<template>
  <div id="app">
    @{{ user.userName }} - {{fullName}}
    <strong>Followers: </strong> {{followers}}
    <button @click="followUser">
      Follow
    </button>
  </div>
</template>

<script>

export default {
  name: 'App',
  data() {
    return {
      followers:0,
      user:{
        id: 1,
        userName: 'madhavsvg',
        firstName: 'Madhav',
        lastName: 'Gupta',
        email: 'madhavsvg@gmail.com',
        isAdmin: true
      }
    }
  },
  watch:{
    followers(newFollowerCount, oldFollowerCount){
      if(oldFollowerCount < newFollowerCount){
        console.log(`${this.user.userName} has gained a new follower 🥳 `);
      }
    }
  },
  computed: {
    fullName() {
      return `${this.user.firstName} ${this.user.lastName}`
    }
  },
  methods: {
    followUser(){
      this.followers++;
    }
  },
  mounted(){
    this.followUser();
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  text-align: center;
  display: flex;
  flex-direction: column;
}
</style>
