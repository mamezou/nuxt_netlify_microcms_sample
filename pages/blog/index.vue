<template>
  <main>
    <h1>ブログ一覧</h1>
    <ul>
// 以下「contents」は5-2でレスポンスで登場した、jsonデータはじめの「contents」のことです。
      <li v-for="content in contents" :key="content.id">
        <nuxt-link :to="`/blog/${content.id}`">
          {{ content.title }}
        </nuxt-link>
      </li>
    </ul>
  </main>
</template>
<script>
import axios from "axios";
export default {
  async asyncData() {
    const { data } = await axios.get(
      // 5-2でメモしたURLを記載しましょう。
      "https://あなたのサービスID.microcms.io/api/v1/blog",
      {
        // 5-2でメモしたAPIキーを記載しましょう。
        headers: { "X-API-KEY": "あなたのAPIキー" }
      }
    );
    return data;
  }
};
</script>
<style></style>
