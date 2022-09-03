
<script setup>
  import { ref } from 'vue'
  
  const header = ref('Shopping List App')
  </script>
  
  <template>
    <h1>{{ header }}</h1>
    <input v-model="header"/>
  </template>

  <style>
  </style>