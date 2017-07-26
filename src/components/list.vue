<template>
  <ul class="todo-main" >
    <item v-for="(todo,index) in todos" :key="index" :todo="todo" :index="index" :remove="remove"></item>
  </ul>
</template>

<script>
  import item from './item.vue';

  export default {
    props:['todos','remove'],

    components: {
      item
    }
}

</script>

<style>

</style>
