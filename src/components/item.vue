<template>
  <li :class="{in:isActive,out:!isActive}"
      @mouseenter="toggle(true)" @mouseleave="toggle(false)">
    <label>
      <input type="checkbox" v-model="todo.statu"/>
      <span>{{todo.title}}</span>
    </label>
    <button class="btn btn-danger" v-show="isShow" @click="rm">删除</button>
  </li>
</template>

<script>
  export default {
    props: ['todo','index','remove'],
    data () {
      return {
        isShow: false,
        isActive: false
      }
    },
    methods: {
      toggle (isEnter) {
        if(isEnter){
          this.isActive = true;
          this.isShow = true;
        }else {
          this.isActive = false;
          this.isShow = false;
        }
      },
      rm () {
        if(confirm(`你确定要上出 ${this.todo.title} 待办事项吗？`)){
          this.remove(this.index)
        }
      }
    }
  }
</script>

<style>
  .in{
    background-color: #999;
  }
  .out{
    background-color: #ffffff;
  }
</style>
