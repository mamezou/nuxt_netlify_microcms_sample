<template>
  <main>
// ここに5-2でメモしたキーを入れると、右側のバリューが出力されます。画像などの表示は
    <h1>{{ title }}</h1>
    <p>{{ date }}</p>
    <div v-html="contents"></div>
  </main>
</template>

<script>
import axios from 'axios'

export default {
  async asyncData({ params }) {
    const { data } = await axios.get(
      `https://あなたのサービスID.microcms.io/api/v1/blog/${params.slug}`,
      {
        headers: { 'X-API-KEY': 'あなたのAPIキー' }
      }
    )
    return data
  }
}
</script>