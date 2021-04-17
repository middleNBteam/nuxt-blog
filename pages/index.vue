<template>
  <div class="">
    <div class="category-list">
      <div class="category" v-for="item of list" :key="item.id">
        <nuxt-link :to="`/category/${item.id}`">{{ item.name }}</nuxt-link>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  async asyncData({ $axios, params }) {
    const { data } = await $axios.$get(`http://127.0.0.1:7001/category`)
    return {
      list: data.items,
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
  methods: {},
}
</script>

<style>
.container {
  margin: 0 auto;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}

.title {
  font-family: 'Quicksand', 'Source Sans Pro', -apple-system, BlinkMacSystemFont,
    'Segoe UI', Roboto, 'Helvetica Neue', Arial, sans-serif;
  display: block;
  font-weight: 300;
  font-size: 100px;
  color: #35495e;
  letter-spacing: 1px;
}

.subtitle {
  font-weight: 300;
  font-size: 42px;
  color: #526488;
  word-spacing: 5px;
  padding-bottom: 15px;
}

.links {
  padding-top: 15px;
}
</style>
