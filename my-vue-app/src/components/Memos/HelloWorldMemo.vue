<script setup>
    import { ref } from 'vue'
    // import {msg} from 'vue'
    const header = ref('Component 2 : Memo')
    const txt = ref('')
    const itemsArray = ref([
    {id: 1, label: "carrots"},
    {id: 2, label: "cake"},
    {id: 3, label: "bunny"}
  ])
    const itemsObject = ref({
      'item-1':{id: 1, label: "carrots"},
      'item-2':{id: 2, label: "cake"},
      'item-3':{id: 3, label: "bunny"}
    })
    const newItemPriority = ref("low")
    const IceCreamFlavors = ref([
    ])

    </script>
    
    <template>
      <h1>{{ txt.toLocaleUpperCase() || header }}</h1>
      <h2>{{ txt ? txt : 'bouh' }}</h2>
      <div class="memo">
      IceCreamFlavors:
      <label>
        <input type="checkbox" v-model="IceCreamFlavors" value="chocolate"/>Choco
      </label>
      <label>
        <input type="checkbox" v-model="IceCreamFlavors" value="coffee"/>Coffee
      </label>
      <label>
        <input type="checkbox" v-model="IceCreamFlavors" value="pear"/>Pear
      </label>
      <br>
      Priority:
    <label>
      <input v-model="newItemPriority" type="radio" value="low"/>Low Priority
      <input v-model="newItemPriority" type="radio" value="high"/>High Priority
    </label>
    <label>
      <select v-model="newItemPriority">
        <option value="low">Low</option>
        <option value="high">High</option>
      </select>
    </label>
<br>
    {{newItemPriority}}
      <ul>
      <li v-for="({id, label}, index) in itemsArray" :key="id">
        {{index}} - {{label}}</li>
      <li v-for="({id, label}, index) in itemsObject" :key="id">
        {{index}} - {{label}}</li>
    </ul>
  </div>
    </template>

    <style>
      @import './mainMemo.css'

    </style>