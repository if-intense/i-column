<template>
  <main class="main">
    <h1 class="title">{{ title }}</h1>
    <p class="publishedAt">{{ publishedAt }}</p>
    <p class="category">{{category && category.name}}</p>
    <div class="post" v-html="body"></div>
  </main>
</template>

<script>
import axios from 'axios'

export default {
  async asyncData({ params }) {
    const { data } = await axios.get(
      `https://icolumn.microcms.io/api/v1/posts/${params.slug}`,
      {
        headers: { 'X-API-KEY': 'c1531420-9002-48fe-a986-5671f608cd2c' }
      }
    )
    return data
  }
}
</script>

<style lang="css" scoped>
.main {
  width: 100%;
  margin: 0 auto;
}

.title {
  margin-bottom: 20px;
}

.publishedAt {
  margin-bottom: 40px;
}

.post > h1 {
	 font-size: 30px;
	 font-weight: bold;
	 margin: 40px 0 20px;
	 background-color: #eee;
	 padding: 10px 20px;
	 border-radius: 5px;
}
 .post > h2 {
	 font-size: 24px;
	 font-weight: bold;
	 margin: 40px 0 16px;
	 border-bottom: 1px solid #ddd;
}
 .post > p {
	 line-height: 1.8;
	 letter-spacing: 0.2px;
}
 .post > ol {
	 list-style-type: decimal;
	 list-style-position: inside;
}
</style>