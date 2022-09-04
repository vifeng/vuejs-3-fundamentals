
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
    <form 
      class="add-item-form"
      @submit.prevent="items.push({id:items.length +1, label: newItem})"
    >
      <input 
        v-model.trim="newItem"
        type="text"
        placeholder="Add Item"
      >
      <label>
        <input type="checkbox" v-model="newItemHighPriority"/>
        High Priority
      </label>
      <button 
        class="btn btn-primary"
      >
        Save Item
      </button>
    </form>
    <br>
    <ul>
      <li v-for="item in items" :key="item.id">
        {{item.label}}
      </li>
    </ul>

  </template>

  <style>
  </style>