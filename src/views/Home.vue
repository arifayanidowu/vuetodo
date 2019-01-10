<template>
  <div id="app">
    <Header/>
    <AddTodo @add-todo="addTodo"/>
    <div v-if="loading === true">
      <img src="../assets/loading.gif" alt="Loading">
    </div>
    <p class="align-center" v-if="todos.length === 0 && loading === false">You Have No Todos</p>
    <Todos :todos="todos" @del-todo="deleteTodo"/>
  </div>
</template>

<script>
/* eslint-disable */
import axios from "axios";
import Todos from "@/components/Todos.vue";
import Header from "@/components/layout/Header";
import AddTodo from "@/components/AddTodo";
export default {
  name: "Home",
  components: {
    Todos,
    Header,
    AddTodo
  },
  data() {
    return {
      todos: [],
      loading: false
    };
  },
  methods: {
    deleteTodo(id) {
      axios
        .delete(`http://jsonplaceholder.typicode.com/todos/${id}`)
        .then(
          ({ data }) =>
            (this.todos = [...this.todos.filter(todo => todo.id !== id)])
        )
        .catch(err => console.log(err));
    },
    addTodo(newTodo) {
      const { title, completed } = newTodo;
      axios
        .post("http://jsonplaceholder.typicode.com/todos", {
          title,
          completed
        })
        .then(({ data }) => (this.todos = [...this.todos, data]))
        .catch(err => {
          console.log(err);
        });
    }
  },
  created() {
    this.loading = !this.loading;
    axios
      .get("http://jsonplaceholder.typicode.com/todos?_limit=5")
      .then(({ data }) => {
        this.todos = data;
        this.loading = false;
      })
      .catch(err => err);
  }
};
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  font-family: "Dosis", sans-serif;
  line-height: 1.4;
}
.text-center {
  text-align: center;
}

.btn {
  display: inline-block;
  border: none;
  background: #555;
  color: #fff;
  padding: 7px 20px;
  cursor: pointer;
}
.btn:hover {
  background: #666;
}

img {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  margin: 0 auto;
}

.align-center {
  text-align: center;
  margin: 0 auto;
  position: absolute;
  top: 25%;
  left: 50%;
  transform: translate(-50%, -50%);
}
</style>
