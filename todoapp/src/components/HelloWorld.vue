<template>
  <div class="hello">
    <!-- <h1>{{ msg }}</h1> -->
    <h2>Todo app</h2>
    <h3>Enter todo</h3>
    <p>Name:</p>
    <input v-model="todo.name">
    <p>Description:</p>
    <input v-model="todo.description">
    <p>Deadline:</p>
    <input v-model="todo.deadline">
    <br>
    <button style="submit" @click="create">Create</button>
    <hr>

    <div v-for="todo in todos" :key="todo.name">
      <li>Name:{{ todo.name }}</li>
      <li>Description:{{ todo.description }}</li>
      <li>Deadline:{{ todo.deadline }}</li>
      <hr>
    </div>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data: () => ({
    todos: [
      { name: "walking", description: "walking", deadline:"0401"},
      { name: "walking", description: "walking", deadline:"0401"}
    ],
    todo: {
      name: "",
      description: "",
      deadline: ""
    }
  }),
  methods: {
    create() {
      this.todos.push(this.todo)
      this.todo = {
        name: "",
        description: "",
        deadline: ""
      }
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
