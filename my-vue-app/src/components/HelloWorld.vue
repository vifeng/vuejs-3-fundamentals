
<script setup>
  import { ref } from 'vue'
  
  const header = ref('Shopping List App')
  const items = ref([
    {id: 1, label: "carrots"},
    {id: 2, label: "cake"},
    {id: 3, label: "bunny"}
  ])
  </script>
  
  <template>
    <h1>{{ header }}</h1>
    <input v-model="header"/>
    <ul>
      <li v-for="item in items" :key="item.id">
        {{item.label}}
      </li>
    </ul>

  </template>

  <style>
  </style>