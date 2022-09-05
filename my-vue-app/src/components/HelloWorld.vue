
<script setup>
  import { ref } from 'vue'
  
  const header = ref('Shopping List App')
  const editing = ref(false)
  const items = ref([
    // {id: 1, label: "carrots"},
    // {id: 2, label: "cake"},
    // {id: 3, label: "bunny"}
  ])
  const newItem = ref("")
  const newItemHighPriority = ref(false)

  const saveItem = ()=>{
    items.value.push({id:items.value.length +1, label: newItem.value})
    newItem.value=""
  }
  const doEdit = (e)=>{
    editing.value = e
    newItem.value = ""
  }
  </script>
  
  <template>
    <div class="header">
      <h1>{{ header }}</h1>
      <button 
        v-if="editing"
        @click="doEdit(false)"
        class="btn"
        >
        Cancel
      </button>
      <button 
      v-else 
      @click="doEdit(true)"
      class="btn btn-primary">
      Add Item
      </button>
    </div>

    
    <form 
      class="add-item-form"
      v-if ="editing"
      @submit.prevent="saveItem"
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
        :disabled="newItem.length < 3"
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