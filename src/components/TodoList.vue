<template>
  <ul class="todo-main">
    <todo-item v-for="(todo,index) in todos" :key="index" :todo="todo" :index="index" :deleteTodo="deleteTodo"/>
  </ul>
</template>

<script>
  import TodoItem from './TodoItem.vue';
  export default {
    props:{
      todos:Array,
      deleteTodo: Function
    },
    components:{
      TodoItem
    }
  };
</script>

<style>
.todo-main {
  width: 460px;
  margin: 10px;
  border: 1.5px solid gainsboro;
  border-radius: 5px;
}

</style>