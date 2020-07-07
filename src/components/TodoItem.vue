<template>
  <li @mouseenter="handleEnter(true)" @mouseleave="handleEnter(false)" :style="{background: bgColor}">
    <label>
      <input type="checkbox" v-model="todo.complete"/>
      <span>{{todo.title}}</span>
    </label>
    <button class="btn btn-danger" v-show="isShow" @click="deleteItem">删除</button>
  </li>
</template>

<script>
  export default {
    props: {
      todo: Object,
      index: Number,
      deleteTodo: Function
    },

    data(){
      return{
        bgColor: 'white',
        isShow: false
      }
    },
    methods:{
      handleEnter(isEnter){
        if (isEnter) {
          this.bgColor = '#aaa';
          this.isShow = true;
        }else{
          this.bgColor = 'white';
          this.isShow = false;
        }
      },
      deleteItem(){
        const {todo,index,deleteTodo} = this;
        if (window.confirm(`确认删除${todo.title}吗?`)) {
          deleteTodo(index);
        }
      }
    }
  }
</script>

<style>
.todo-main li {
  width: 450px;
  height: 30px;
  padding-left: 10px;
  line-height: 30px;
  border-bottom: 1px solid gainsboro;
}
.todo-main li:last-child {
  border-bottom: none;
}
.todo-main li span {
  margin-left: 5px;
}
.todo-main .btn-danger {
  width: 60px;
  height: 20px;
  margin: 5px;
}
</style>