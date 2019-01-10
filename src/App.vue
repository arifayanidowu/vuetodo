<template>
  <div id="app">
    <Header/>
    <AddTodo @add-todo="addTodo"/>
    <Todos :todos="todos" @del-todo="deleteTodo"/>
  </div>
</template>

<script>
import Todos from "@/components/Todos.vue";
import Header from "@/components/layout/Header";
import AddTodo from "@/components/AddTodo";
export default {
  name: "app",
  components: {
    Todos,
    Header,
    AddTodo
  },
  data() {
    return {
      todos: [
        {
          id: 1,
          title: "Todo One",
          completed: false
        },
        {
          id: 2,
          title: "Todo Two",
          completed: false
        },
        {
          id: 3,
          title: "Todo Three",
          completed: false
        }
      ]
    };
  },
  methods: {
    deleteTodo(id) {
      this.todos = [...this.todos.filter(todo => todo.id !== id)];
    },
    addTodo(newTodo) {
      this.todos = [...this.todos, newTodo];
    }
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
</style>
