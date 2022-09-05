
<script setup>
  import { ref } from 'vue'
  
  const header = ref('Shopping List App')
  const editing = ref(false)
  const items = ref([
    {
    id: 1, 
    label: "carrots", 
    purchased: true, 
    highPriority: false},
    {
    id: 2, 
    label: "cake", 
    purchased:true, 
    highPriority: false},
    {
    id: 3, 
    label: "bunny", 
    purchased:false, 
    highPriority: true}
  ])
  const newItem = ref("")
  const newItemHighPriority = ref(false)

// methods

  const saveItem = ()=>{
    items.value.push(
      {
        id: items.value.length + 1,
        label: newItem.value,
        highPriority: newItemHighPriority.value
      })
    newItem.value = ""
    newItemHighPriority.value = ""
  }
  const doEdit = (e)=>{
    editing.value = e
    newItem.value = ""
    newItemHighPriority.value = ""
  }
  const togglePurchased = (item)=>{
    item.purchased = !item.purchased
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
      <li 
      v-for = "item in items" 
      @click="togglePurchased(item)"
      :key = "item.id"
      class = "static-class"
      :class = "[
      item.purchased ? 'text-gray, strikeout' : 'underlined',
      item.highPriority ? 'priority':'',
      ]"
      >
      {{item.label}}
      </li>
    </ul>
  </template>

  <style>
  </style>