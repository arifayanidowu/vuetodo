<template>
  <div class="todo-item" :class="{'is-complete':todo.completed}">
    <p>
      <input type="checkbox" @change="markComplete">
      {{ todo.title }}
      <button @click="$emit('del-todo', todo.id)" class="del">&times;</button>
    </p>
  </div>
</template>

<script>
export default {
  name: "TodoItem",
  props: {
    todo: Object
  },
  methods: {
    markComplete: function() {
      this.todo.completed = !this.todo.completed;
    }
  }
};
</script>

<style scoped>
.todo-item {
  padding: 10px;
  background: #f4f4f4;
  border-bottom: 1px dotted #ccc;
}
.is-complete {
  text-decoration: line-through;
}
.del {
  background: #ff0000;
  color: #fff;
  padding: 5px 9px;
  border: none;
  border-radius: 50%;
  cursor: pointer;
  float: right;
}
</style>
