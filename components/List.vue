<template>
  <div>
    <ul>
      <li v-for="item in items" :key="item.id">
        {{ item.description }}
      </li>
    </ul>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  name: 'List',
  props: ['name', 'url'],
  data() {
    return {
      items: []
    }
  },
  async created() {
    try {
      const res = await axios.get(this.url)
      this.items = res.data
    } catch (error) {
      console.log(error)
    }
  }
}
</script>
  