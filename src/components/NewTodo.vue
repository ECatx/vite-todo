<template>
    <input class="text-3xl py-2 px-4 rounded-lg w-full mt-8" type="text" :placeholder="placeholder" v-model="newTodo" @change="addTodo"/>
</template>

<script setup>
import {defineProps} from 'vue'
import {newTodo,addTodo} from '../helpers/stuff.js'

defineProps({
    placeholder: {
        type: String,
        default: 'Type a new Todo',
    },
})
</script>