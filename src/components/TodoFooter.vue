<template>
  <div class="todo-footer">
    <label>
      <input type="checkbox" v-model="isAllChecked" />
    </label>
    <span>
      <span>已完成{{completeSize}}</span> / 全部{{todos.length}}
    </span>
    <button class="btn btn-danger" v-show="completeSize" @click="deleteCompleteTodos">清除已完成任务</button>
  </div>
</template>

<script>
export default {
  props:{
    todos:Array,
    deleteCompleteTodos: Function,
    SelectAllTodos: Function
  },
  computed: {
    completeSize(){
      return this.todos.reduce((preTotal,todo) => preTotal + (todo.complete?1:0), 0 );
      //reduce:累加器
      //preTotal:初始值, 或者计算结束后的返回值。todo:当前元素 0:传递给函数的初始值
    },
    isAllChecked:{
      get(){
        return this.completeSize === this.todos.length && this.completeSize > 0;
      },
      set(value){
        this.SelectAllTodos(value);
      }
    }
  }
};
</script>

<style>
.todo-footer {
  width: 446px;
  margin: 10px;
  padding-left: 10px;
}
.todo-footer span {
  margin-left: 5px;
}
.todo-footer .btn-danger {
  width: 100px;
  height: 22px;
}

</style>