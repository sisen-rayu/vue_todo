<template>
  <div class="hello">
    <!-- <h1>{{ msg }}</h1> -->
    <h2>Todo app</h2>
      <button style="submit" @click="deleteAll(todo)">DeleteALL</button>
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

    <button style="submit" @click="read">Read</button>
    <div v-for="todo in todos" :key="todo.name">
      <li>Name:{{ todo.name }}</li>
      <li>Description:{{ todo.description }}</li>
      <li>Deadline:{{ todo.deadline }}</li>
      <button style="submit" @click="deleteTodo(todo)">Delete</button>
      <hr>
    </div>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data: () => ({
    todos: [
      // { name: "walking", description: "walking", deadline:"0401"},
      // { name: "walking", description: "walking", deadline:"0401"}
    ],
    todo: {
      name: "",
      description: "",
      deadline: ""
    },
    name: "todos"
  }),
  methods: {
    read() {
      const data = sessionStorage.getItem(this.name)
      if (data) {
        this.todos = JSON.parse(data)
      }
    },
    create() {
      // this.name = sessionStorage.getItem("name")
      this.todos.push(this.todo)
      sessionStorage.setItem(this.name, JSON.stringify(this.todos))
      this.todo = {
        name: "",
        description: "",
        deadline: ""
      }
    },
    deleteTodo(todo) {
      this.todos = this.todos.filter((item) => item.name !== todo.name)
      sessionStorage.setItem(this.name, JSON.stringify(this.todos))
    },
    deleteAll() {
      // sessionstorageの中身を空にするメソッド
      sessionStorage.clear()
      this.todos = []
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
