<template>
<div class='user'>
  <h1>Usuarios</h1>
  <ul v-for='user in users' v-bind:key="user.id">
          <li>
          {{ user.name  }}-{{ user.email  }}
          <button v-on:click='remove(user)'>x</button>
          </li>
  </ul>
  <form v-on:submit.prevent='addUser'>
    <input type="text" v-model='newUser.name' placeholder='nombre'>
    <input type="email" v-model='newUser.email' placeholder='email'>
    <input type="submit" value='Crear'>
  </form>
</div>
</template>

<script>

export default{
  data() {
    return{
      users:[],
      newUser: {},
    }
  },
  methods: {
    addUser(){
      this.users.push(this.newUser);
      this.newUser = {};
    },
    remove(user){
      this.users.splice(this.users.indexOf(user),1);
    }
  },
  created(){
    this.$http.get('https://jsonplaceholder.typicode.com/users')
      .then(res=> this.users = res.body);
  }
}

</script>

<style>
.user {
  background: black;
  color: white;
}
</style>
