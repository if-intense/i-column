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
    const page = params.p || '1'
    const limit = 10
    const { data } = await axios.get(      
      // add ?limit-${limit}&offset=${(page - 1)* limit}
      'https://i-columnblog.microcms.io/api/v1/column?limit=${limit}&offset=${(page - 1) * limit}',
      {
        
        headers: { 'X-API-KEY': '8af4ace2-1340-419c-9101-f57ca02a6ec9' }
      }

      `https://i-column.microcms.io/api/v1/posts?limit=${limit}&offset=${(page - 1) * limit}`,
      { headers: { 'X-API-KEY': 'c1531420-9002-48fe-a986-5671f608cd2c' } }
    )
    return data
  }
}
</script>
