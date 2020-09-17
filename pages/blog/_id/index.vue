<template>
  <div class="wrapper-content wrapper-content--fixed">
    <post :post="post" />
    <comments :comments="comments" />
    <newComment />
  </div>
</template>

<script>
import post from "@/components/Blog/Post.vue"
import newComment from "@/components/Comments/NewComment.vue"
import comments from "@/components/Comments/Comments.vue"

export default {
  components: { post, newComment, comments },
  data() {
    return {
    post: {
          id: 1,
          title: '1 post',
          descr: 'Lorem Ipsum is simply dummy text of the printing and typesetting industry.',
          content: 'Lorem Ipsum is simply dummy text of the printing and typesetting industry.Lorem Ipsum is simply dummy text of the printing and typesetting industry.Lorem Ipsum is simply dummy text of the printing and typesetting industry.',
          img: 'https://lawnuk.com/wp-content/uploads/2016/08/sprogs-dogs.jpg'
        },
    comments: [
      { name: 'Alex', text: 'Lorem Ipsum is simply dummy text of the printing and typesetting industry.' },
      { name: 'Evgenii', text: 'Lorem Ipsum is simply dummy text of the printing and typesetting industry.'}
    ]
    }
  }
}
</script>

<style lang="scss">
.post {
  max-width: 900px;
  margin: 0 auto;
}
.post-header {
  text-align: center;
  margin-bottom: 30px;
  img {
    max-width: 400px;
    margin-bottom: 1px;
  }
  p {
    color: #999;
  }
}
.post-body {
  text-align: left;
}
</style>