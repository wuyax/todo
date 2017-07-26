<template>
  <div class="todo-header">
    <input type="text" placeholder="请输入你的任务名称，按回车键确认" v-model="todo" @keyup.enter="addTodo"/>
  </div>
</template>

<script>
  export default {
    props: ['add'],
      data () {
        return {
          todo: ''
        }
      },
      methods: {
          addTodo () {
              let {todo} = this;
              if(!todo.trim()){
                  return;
              };
              let addTodo = {statu:false,title:todo.trim()};
              this.add(addTodo);
              this.todo = '';
          }
      }
  }
</script>

<style>

</style>
