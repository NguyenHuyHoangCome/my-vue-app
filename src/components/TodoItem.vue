<template>
  <AddTodo @add-todo="addTodoitem" />
  <TodoItemList
    v-for="todo in todos"
    :key="todo.id"
    :todoProps="todo"
    @itemComplete="markItemComplete"
    @deleteItem="deleteTodo"
  />
</template>

<script>
import { ref } from 'vue'
import TodoItemList from './todolist.vue'
import AddTodo from './addTodo.vue'

import axios from 'axios'

export default {
  name: 'TodoItem',
  components: { TodoItemList, AddTodo },
  setup() {
    const todos = ref([])
    const getAllTodos = async () => {
      try {
        const res = await axios.get(
          'https://jsonplaceholder.typicode.com/todos?_limit=5'
        )

        console.log(res.data)
        //todos.value = res.data
      } catch (error) {
        console.log(error)
      }
    }
    getAllTodos()
    const markItemComplete = id => {
      //console.log(id)
      todos.value = todos.value.map(todo => {
        if (todo.id === id) {
          todo.completed = !todo.completed
        }
        return todo
      })
    }
    const deleteTodo = id => {
      todos.value = todos.value.filter(todo => todo.id !== id)
    }

    const addTodoitem = newTodo => {
      console.log(newTodo.id)
      todos.value.push(newTodo)
    }
    return {
      todos,
      markItemComplete,
      deleteTodo,
      addTodoitem
    }
  }
}
</script>

<style>
</style>