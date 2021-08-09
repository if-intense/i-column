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
      'https://i-columnblog.microcms.io/api/v1/column?limit=${limit}&offset=${(page - 1) * limit}',
      {
        
        headers: { 'X-API-KEY': '8af4ace2-1340-419c-9101-f57ca02a6ec9' }
      }
    )
    return data
  }
}
</script>
