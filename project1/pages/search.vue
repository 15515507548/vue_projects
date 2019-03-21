<template>
  <section class="container">
   search
   <ul>
      <li v-for="(item,idx) in $store.state.navbar.app" :key="idx">{{item}}</li>
   </ul>
  </section>
</template>

<script>
import axios from 'axios'
export default {
  layout: 'search',
  data() {
    return {
      list: []
    }
  },
  async asyncData() {
    let {status, data: {list}} = await axios.get('http://localhost:3000/city/list')
    if (status === 200) {
      return {
        list: list
      }
    }
  }
}
</script>


<style scoped>
.title {
  margin: 50px 0;
}
</style>
