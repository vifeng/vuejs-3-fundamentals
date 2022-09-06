<script setup>
    import {ref, reactive} from 'vue'

    // see https://vuejs.org/guide/extras/reactivity-in-depth.html#computed-debugging

    // don't work with primitives reactive({0}), reactive({true}), reactive({'hello'})
    // but can live in sth big such as count here
    const state = reactive({count: 0})
    // work without def
    const increment = ()=>{
        state.count ++
    }
    
    const msg = ref('hello Wolrd!')
</script>


<template>
    <h1> {{state.count}}</h1>
    <button 
        @click="increment">
        Increment count
    </button>
</template>