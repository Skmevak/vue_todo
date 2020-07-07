<template>
  <div class="todo-header">
    <input type="text" placeholder="请输入你的任务名称，按回车键确认" v-model="title" @keyup.enter="addItem" />
  </div>
</template>

<script>
export default {
  props: {
    addTodo: Function
  },
  data(){
    return {
      title: ''
    }
  },
  methods:{
    addItem(){
      const title = this.title.trim();
      if(!title){
        alert('必须输入');
      }
      //根据输入生成一个todo对象
      const todo = {
        title,
        complete: false
      }
      //添加到todos
      this.addTodo(todo);
      //清楚输入
      this.title = '';
    }
  }
};
</script>

<style>
.todo-header {
  width: 480px;
  margin: 10px;
}
.todo-header input {
  width: 450px;
  height: 12px;
  padding: 5px;
  line-height: 22px;
  border: 1.5px solid gainsboro;
  border-radius: 5px;
}
</style>