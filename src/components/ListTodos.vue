<template>
         <section class="space-y-4" v-if="todos.length>0">
        <h3 class="text-3xl font-bold" :class="color === 'green' ? 'text-green-500' : 'text-red-500'"> {{title}}: {{todos.length}}</h3>
        <ul class="space-y-4">
          <li v-for="todo in todos" :key="todo.id" class=" bg-white rounded-xl text-2xl py-2 px-4 font-medium text-center hover:text-white cursor-pointer transition-colors" :class="color==='green' ? 'text-green-500 hover:bg-green-500' : 'text-red-500 hover:bg-red-500' " @click="changeStatus(todo.id)">
            {{todo.text}}</li>
        </ul>
      </section>   
</template>

<script setup>
import {changeStatus} from '../helpers/stuff.js'
import {defineProps} from 'vue' 

defineProps({
    color:{
        type: String,
        default: 'green'
    },
    title: {
        type: String,
        default: 'Todo List'
    },
    todos: {
       type: Array,
       default: [],

    }
})
</script>