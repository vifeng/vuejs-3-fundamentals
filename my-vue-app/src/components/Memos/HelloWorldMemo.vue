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
    </script>
    
    <template>
      <h1>{{ txt.toLocaleUpperCase() || header }}</h1>
      <h2>{{ txt ? txt : 'bouh' }}</h2>
      <input v-model="header"/>
      <ul>
      <li v-for="({id, label}, index) in itemsArray" :key="id">
        {{index}} - {{label}}</li>
      <li v-for="({id, label}, index) in itemsObject" :key="id">
        {{index}} - {{label}}</li>
    </ul>
    </template>