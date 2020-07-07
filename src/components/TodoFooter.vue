<template>
  <div class="todo-footer">
    <label>
      <input type="checkbox" />
    </label>
    <span>
      <span>已完成0</span> / 全部2
    </span>
    <button class="btn btn-danger">清除已完成任务</button>
  </div>
</template>

<script>
export default {};
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