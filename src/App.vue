<template>
  <div id="app">
    <HeaderItem />
    <TodoItem />
  </div>
</template>

<script>
import HeaderItem from './components/headerItem.vue'
import TodoItem from './components/TodoItem.vue'
export default {
  name :'App',
  components: {HeaderItem, TodoItem},

}
</script>

<style>
#app{
  font-family: 'Franklin Gothic Medium', 'Arial Narrow', Arial, sans-serif;
}
</style>