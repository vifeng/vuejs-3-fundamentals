<script setup>
    import { ref } from 'vue'
    // import {msg} from 'vue'
    const header = ref('Component 2 : Memo')
    const txt = ref('')
    </script>
    
    <template>
      <h1>{{ txt.toLocaleUpperCase() || header }}</h1>
      <h2>{{ txt ? txt : 'bouh' }}</h2>
     <h3 >{{msg}} xxo</h3>
     <input v-model="header"/>
    </template>