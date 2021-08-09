<template>
   <ul>
    <li v-for="content in contents" :key="content.id">
      <nuxt-link :to="`/${content.id}`">
        {{ content.title }}
      </nuxt-link>
    </li>
  </ul>
</template>

<script>
import axios from 'axios'
export default {
  async asyncData(params) {

    // adding for pagination
    const page = params.p|| '1'
    const limit = 10

    const { data } = await axios.get(
      
      // add ?limit-${limit}&offset=${(page - 1)* limit}
      'https://icolumn.microcms.io/api/v1/posts?limit=${limit}&offset=${(page - 1) * limit}',
      {
        
        headers: { 'X-API-KEY': 'c1531420-9002-48fe-a986-5671f608cd2c' }
      }
    )
    return data
  }
}
</script>
