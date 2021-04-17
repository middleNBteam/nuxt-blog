<template>
  <div class="post_container">
    <div class="post" v-for="item of list" :key="item.ID">
      <nuxt-link :to="`/post/${item.post_name}`">{{
        item.post_title
      }}</nuxt-link>
    </div>
  </div>
</template>

<script>
export default {
  async asyncData({ $axios, params }) {
    const { data } = await $axios.$post(
      `http://127.0.0.1:7001/category/getpost`,
      {
        id: params.category,
      }
    )
    return {
      list: data.data,
    }
  },
  data() {
    return {
      test: 1,
    }
  },
  mounted() {
    console.log('mounut', this.list)
  },
  computed: {},
  methods: {},
}
</script>
