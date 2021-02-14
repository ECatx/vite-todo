<template>
      <h1 class="text-4xl font-light text-white text-center"> {{ msg }}</h1>
</template>

<script setup>
import {defineProps} from 'vue'
  
defineProps({
    msg:{
        type: String,
        default: 'No Title',
    },
})
</script>

