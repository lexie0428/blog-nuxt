<template>
  <newPostForm
  :postEdit="post"
   @submit="onSubmit"/>
</template>

<script>
import axios from 'axios'

import newPostForm from "@/components/Admin/NewPostForm.vue"
export default {
  components: { newPostForm },
  layout: 'admin',
  asyncData(context) {
      return axios.get(`https://blog-nuxt-6f33e.firebaseio.com/posts/${context.params.postId}.json`)
      .then(res => {
        return {
          post: { ...res.data, id: context.params.postId }
        }
      })
      .catch(e => context.error(e))
  },
  methods: {
    onSubmit(post) {
      console.log('Post editing!');
      this.$store.dispatch('editPost', post)
      .then(() => {
        this.$router.push('/admin')
      })
    }
  }
}
</script>