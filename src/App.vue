<template>
  <div id="app">
    <Initialize />
    <ConversationContainer 
      v-for="id in convoIds"
      :conversation="conversations[id]"
      :id="id"
      :key="id"
    />
    From the Vue article here : https://vuejsdevelopers.com/2017/10/16/vue-js-firestore/?jsdojo_id=revue_vvf&utm_campaign=Revue%20newsletter&utm_medium=Newsletter&utm_source=Vue.js%20Developers
  </div>
</template>

<script>
import Initialize from './Initialize.vue'
import ConversationContainer from './ConversationContainer.vue'

import { mapState } from 'vuex'

export default {
  name: 'app',
  created () {
    console.log('-- firebase log --')
    console.log(this.$store.state.db)
  },
  components: {
    Initialize,
    ConversationContainer
  },
  computed: {
    ...mapState({
      conversations: state => state.conversations.all,
      convoIds: state => state.conversations.allIds
    })
  },
  data () {
    return {
      msg: 'Welcome to Your Vue.js App'
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

h1, h2 {
  font-weight: normal;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #42b983;
}
</style>
