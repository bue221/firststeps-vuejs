<template>
<div>
  <div v-if='show'>
      <p>No puedo mostrar el mensaje</p>
  </div>
  <div v-else>
    <p>Ya puedo mostrar el mensaje</p>
  </div>
  <hr>
  <div v-for='task in task'>
    {{ task.title  }}
  </div>
  <input type="text" v-model='user.firstName'>
  <button type='button' name='button' v-on:click='saludar(user.firstName)'>
    Saluda
  </button>
</div>
</template>

<script>
export default {
 data() {
  return {
    title: 'Componente Test',
    user: {
      firstName: 'joe',
      lastName: 'Makey'
    },
    html: '<h1>Buena</h1>',
    show: true,
    task: [
    {title: 'comer'},
    {title: 'mate'},
    {title: 'Algebra'}
    ]
  }
 },
 methods: {
  saludar(show) {
    alert('hello '+ show);
  }
 }
}
</script>

<style media='screen'>
</style>
