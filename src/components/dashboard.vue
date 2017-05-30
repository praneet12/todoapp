<template>
  <div class="dash">
    <div> Header Section </div>
    <div> Aside Section</div>
    <input v-model="newTodo" />
    <button v-on:click="addTodo">Add</button>
    <Content
        v-bind:todos="todos"
        v-bind:deletetodo="deletetodo"
        v-bind:complete="complete"
    />
  </div>
</template>

<script>

import Content from './Content'

export default {
  methods: {
      addTodo: function() { if (this.newTodo) this.todos.splice(0,0,{ id: this.todos.length + 1 , text: this.newTodo,completed: false }); console.log(this.todos); this.newTodo = undefined },
      deletetodo: function(id) {console.log(id); this.index = this.todos.findIndex(x => x.id === id); this.todos.splice(this.index, 1) },
      complete: function (todo) { todo.completed = true }
  },
  data () {
    return {
      msg: 'Welcome to Your Vue.js App',
      newTodo : undefined,
      todos: []
    }
  },
  components: {
    Content
  }
}
</script>




<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #42b983;
}
</style>
