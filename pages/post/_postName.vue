<template>
  <div class="post_container">
    <div class="title">
      {{ post.post_title }}
    </div>
    <div class="content">
      {{ post.post_content }}
    </div>
  </div>
</template>

<script>
export default {
  async asyncData({ $axios, params }) {
    const { data } = await $axios.$get(
      `http://127.0.0.1:7001/post/bypostname`,
      {
        params: {
          postName: params.postName,
        },
      }
    )
    return {
      list: data.items.data,
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
  computed: {
    post() {
      return this.list[0]
        ? this.list[0]
        : {
            post_title: '',
            post_content: '',
          }
    },
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
