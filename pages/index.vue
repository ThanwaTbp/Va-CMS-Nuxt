<template>
  <div>
    <b-row>
      <b-col v-for="post in posts" :key="post.slug">
        <b-card
          :title="post.title"
          tag="article"
          style="max-width: 20rem; border-radius: 30px;"
          class="mb-2 border-0 shadow"
        >
          <b-card-text>
            {{ post.description }}
          </b-card-text>

          <b-button 
          :to="{ name: 'posts-slug', params: { slug: post.slug } }" 
          variant="info" style="border-radius: 20px;">View Detail</b-button>
        </b-card>
      </b-col>
    </b-row>
  </div>
</template>

<script>
export default {
  async asyncData({$content}) {
    const postsData = await $content('posts').fetch()
    return {
      posts: postsData,
    }
  },
  mounted() {
    this.posts
    console.log('THIS.POSTS', this.posts)
  }
}
</script>

<style>
  
</style>
