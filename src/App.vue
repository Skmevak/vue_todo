<template>
  <div class="todo-container">
    <div class="todo-wrap">
      <todo-header :addTodo="addTodo"/>
      <todo-list :todos="todos" :deleteTodo="deleteTodo"/>
      <todo-footer/>
    </div>
  </div>
</template>

<script>
import TodoHeader from "./components/TodoHeader.vue";
import TodoList from "./components/TodoList.vue";
import TodoFooter from "./components/TodoFooter.vue";

export default {
  name: "App",
  data(){
    return{
      todos:[
        {title: '吃饭',complete: false},
        {title: 'sleep',complete: true},
        {title: 'coding',complete: false}
      ]
    }
  },
  components: {
    TodoHeader,
    TodoList,
    TodoFooter
  },
  methods: {
    addTodo(todo){
      this.todos.unshift(todo);
    },
    deleteTodo(index){
      this.todos.splice(index,1);
    }
  }
};
</script>

<style>
.todo-container {
  width: 600px;
  height: 100%;
  margin: auto;
  border: 1.5px solid gainsboro;
  border-radius: 10px;
}
.todo-wrap {
  width: 500px;
  height: 100%;
  margin: 20px auto;
  border: 1.5px solid gainsboro;
  border-radius: 10px;
}
</style>
