<template>
  <div class="todo-footer">
    <label>
      <input type="checkbox" v-model="isSlectAll"/>
    </label>
    <span>
          <span>已完成{{slect.length}}</span> / 全部{{todos.length}}
        </span>
    <button class="btn btn-danger" v-show="slect.length" @click="rmAll">清除已完成任务</button>
  </div>
</template>

<script>
  export default {
    props: {
      todos:Array,
      remove:Function,
      removeSlect:Function,
      slectAll:Function
    },
    data () {
      return {
        isAll: false,
        hasSelect: false,
        //slectTodo: []
      }
    },
    methods: {
        rmAll () {
          this.removeSlect();
        }
    },
    computed: {

      slect: {
        get: function () {
          let slectTodo = [];
           return slectTodo = this.todos.filter((todo)=> todo.statu);
        }
      },
      isSlectAll: {
        get: function () {
            return this.slect.length===this.todos.length && this.todos.length>0
        },
        set: function (value) {
            this.slectAll(value);
        }
      }
    }
  }
</script>

<style>

</style>
