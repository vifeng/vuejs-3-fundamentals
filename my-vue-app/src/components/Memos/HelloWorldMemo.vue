<script setup>
    import { ref } from 'vue'
    // import {msg} from 'vue'
    const header = ref('Component 2 : Memo')
    const txt = ref('')
    // pay attention to ref([ -> []
    const itemsArray = ref([
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
  // pay attention to ref({ -> {}
    const itemsObject = ref({
      'item-1':{id: 1, label: "carrots"},
      'item-2':{id: 2, label: "cake"},
      'item-3':{id: 3, label: "bunny"}
    })
    const newItemPriority = ref("low")
    const IceCreamFlavors = ref([
    ])
    const saveItem = ()=>{
      itemsArray.push({newItem})
      newItem
    }

    </script>
    
    <template>
      <h1>{{ txt.toLocaleUpperCase() || header }}</h1>
      <h2>{{ txt ? txt : 'bouh' }}</h2>
      <a v-bind:href="newItem">Dynamic Link</a>
      <input 
        type="text"
        v-on:click="saveItem"
      />
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
      <li 
        v-for = "item in itemsArray" 
        :key = "item.id"
        class = "static-class"
        :class = "[
        item.purchased ? 'text-gray, strikeout' : 'underlined',
        item.highPriority ? 'priority':'',
        'test',
        {test2: item.purchased}
        ],
        [{test3: item.purchased}]"
      >{{item.label}}</li>
      <li 
      v-for="({id, label}, index) in itemsArray" :key="id">
        {{index}} - {{label}}
      </li>
      <li v-for="({id, label}, index) in itemsObject" :key="id">
        {{index}} - {{label}}</li>
    </ul>
  </div>
    </template>

    <style>
      @import './mainMemo.css'

    </style>