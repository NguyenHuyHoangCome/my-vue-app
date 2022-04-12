<template>
  <p :class="['todoItem',todoProps.completed ? 'iscompleted' : '']">
      <input type="checkbox" :checked="todoProps.completed" @change="markItemComplete" />
      {{todoProps.title}}
      <button class="del-btn" @click="deleteItem">Delete</button>
  </p>
</template>

<script>
//import {ref} from 'vue'

export default {
    name:'TodoItemList',
    props: ['todoProps'],
    setup(props, context) {
        const markItemComplete = ()=>{
            context.emit('itemComplete',props.todoProps.id)
        }
        const deleteItem =()=>{
            context.emit('deleteItem',props.todoProps.id)
        }
        return {
            markItemComplete,
            deleteItem
        }
    }
   
}
</script>

<style>
    .iscompleted{
        text-decoration: line-through;
    }
    .todoItem{
        background: #f4f4f4;
        padding: 10px;
        margin: 0;
        border-bottom: 1px #ccc dotted;
    
    }
    .del-btn{
        background: red;
        color: white;
        border: none;
        cursor: pointer;
        float: right; 

    }
</style>