<template>
  <div class="todo-container">
    <div class="todo-wrap">
      <h2>任务清单</h2>
      <add :add="add"></add>
      <list :todos="todos" :remove="remove"></list>
      <foot :todos="todos" :remove="remove" :remove-slect="removeSlect" :slect-all="slectAll"></foot>
    </div>
  </div>
</template>

<script>
import add from './addtodo.vue';
import list from './list.vue';
import foot from './footer.vue';
export default{
    data () {
        return{
            todos: []
        }
    },
  created () {
    this.todos = JSON.parse(localStorage.getItem('TODOS')||'[]');
  },
  components: {
        add,
        list,
        foot
  },
  methods: {
      add (todo) {
        this.todos.unshift(todo)
      },
      remove (index) {
        this.todos.splice(index,1);
      },
      removeSlect () {
        this.todos = this.todos.filter((todo)=>{
            return !todo.statu;
        })
      },
      slectAll (i) {
          this.todos.forEach(function (todo, index) {
            todo.statu = i;
          })
      }
  },
  watch: {
      todos: {
        deep: true,
        handler: function (val) {
          localStorage.setItem('TODOS',JSON.stringify(val));
        }
      }
  }
}
</script>

<style>

</style>
