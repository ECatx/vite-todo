<template>
  <div class="min-h-screen flex flex-col justify-center items-center">
    <header class="flex flex-col w-full container">
      <h1 class="text-4xl font-light text-white text-center">A Todo App 🍔</h1>
      <input class="text-3xl py-2 px-4 rounded-lg w-full mt-8" type="text" placeholder="New Todo" v-model="newTodo" @change="addTodo"/>
    </header>

    <main class="container w-full mt-7 space-y-8">
      <section class="space-y-4" v-if="pendingTodos.length>0">
        <h3 class="text-green-500 text-3xl font-bold">Pending Items: {{pendingTodos.length}}</h3>
        <ul class="space-y-4">
          <li v-for="todo in pendingTodos" :key="todo.id" class=" bg-white rounded-xl text-2xl py-2 px-4 font-medium text-green-500 text-center hover:text-white hover:bg-green-500 cursor-pointer transition-colors" @click="changeStatus(todo.id)">
            {{todo.text}}</li>
        </ul>
      </section>
      <section class="space-y-4" v-if="completedTodos.length>0">
        <h3 class="text-red-500 font-bold text-3xl">Completed Items: {{completedTodos.length}}</h3>
        <ul class="space-y-4">
          <li v-for="todo in completedTodos" :key="todo.id" class="bg-white rounded-xl text-2xl py-2 px-4 font-medium text-red-500 text-center hover:text-white hover:bg-red-500 cursor-pointer transition-colors" @click="changeStatus(todo.id)">
            {{todo.text}}
            </li>
        </ul>
      </section>

    </main>
  </div> 
</template>

<script setup>
  import {ref,computed} from 'vue'

  const newTodo = ref('')

  const todos = ref([

  ])

  const pendingTodos = computed(()=>{
    return todos.value.filter(todo=>todo.status==='pending')
  })
  const completedTodos = computed(()=>{
    return todos.value.filter(todo=>todo.status==='done')
  })
const changeStatus = id => {
  todos.value.map(todo =>{
    if(todo.id === id){
      todo.status = todo.status === 'pending' ? 'done' : 'pending'
    }
  })
}

const addTodo = () => {
  if(newTodo.value.length>0){
    todos.value.push({
      id: todos.value.length,
      text: newTodo.value,
      status: 'pending'
    })
    newTodo.value = ''
  }
}
</script>

