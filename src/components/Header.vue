<template>
    <header class="flex flex-col w-full container">
      <Title msg="🥤A Todo App 🍔"/>
      <NewTodo/>
    </header>
</template>

<script setup>
  import NewTodo from './NewTodo.vue'
  import Title from './Title.vue'
</script>