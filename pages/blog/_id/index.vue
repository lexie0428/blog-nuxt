<template>
  <div class="wrapper-content wrapper-content--fixed">
    <post :post="post" />
    <comments :comments="comments" />
    <newComment :postId="$route.params.id" />
  </div>
</template>

<script>
import axios from "axios";

import post from "@/components/Blog/Post.vue";
import newComment from "@/components/Comments/NewComment.vue";
import comments from "@/components/Comments/Comments.vue";

export default {
  components: { post, newComment, comments },
  async asyncData(context) {
    let [post, comments] = await Promise.all([
      axios.get(
        `https://blog-nuxt-6f33e.firebaseio.com/posts/${context.params.id}.json`
      ),
      axios.get(`https://blog-nuxt-6f33e.firebaseio.com/comments.json`)
    ]);

    let postComments = Object.values(comments.data).filter(
      comment => comment.postId === context.params.id && comment.publish
    );

    return {
      post: post.data,
      comments: postComments
    };
  }
};
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