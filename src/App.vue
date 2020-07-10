<template>
  <div class="todo-container">
    <div class="todo-wrap">
      <todo-header :addTodo="addTodo"/>
      <todo-list :todos="todos" :deleteTodo="deleteTodo"/>
      <todo-footer :todos="todos" :deleteCompleteTodos="deleteCompleteTodos" :SelectAllTodos="SelectAllTodos"/>
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
      //从localstorage读取todos
      todos: JSON.parse(window.localStorage.getItem('todos_key') || '[]')
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
    },
    deleteCompleteTodos(){
      this.todos = this.todos.filter(todo => !todo.complete);
    },
    SelectAllTodos(check){
      this.todos.forEach(todo => todo.complete = check)
    }

  },
  watch: {//深度监视
  todos:{
    deep: true,//深度监视
    handler: function(value){
      //将todos最新值的JSON数据，保存到localstorage
      window.localStorage.setItem('todos_key',JSON.stringify(value))
    }
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
