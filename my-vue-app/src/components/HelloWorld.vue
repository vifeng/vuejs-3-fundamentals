
<script setup>
  import { ref } from 'vue'
  
  const header = ref('Shopping List App')
  const items = ref([
    {id: 1, label: "carrots"},
    {id: 2, label: "cake"},
    {id: 3, label: "bunny"}
  ])
  const newItem = ref("")
  const newItemHighPriority = ref(false)
  </script>
  
  <template>
    <h1>{{ header }}</h1>
    <input v-model="newItem" placeholder="Add Item"/>
    <label>
      <input v-model="newItemHighPriority" type="checkbox"/>
      High Priority
    </label>
    <br>
    {{newItemHighPriority}}
    <ul>
      <li v-for="item in items" :key="item.id">
        {{item.label}}
      </li>
    </ul>

  </template>

  <style>
  </style>