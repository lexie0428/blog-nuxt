<template>
  <newPostForm
  :postEdit="post"
   @submit="onSubmit"/>
</template>

<script>
import newPostForm from "@/components/Admin/NewPostForm.vue"
export default {
  components: { newPostForm },
  layout: 'admin',
  data() {
    return {
    post: {
          id: 1,
          title: '1 post',
          descr: 'Lorem Ipsum is simply dummy text of the printing and typesetting industry.',
          content: 'Lorem Ipsum is simply dummy text of the printing and typesetting industry.Lorem Ipsum is simply dummy text of the printing and typesetting industry.Lorem Ipsum is simply dummy text of the printing and typesetting industry.',
          img: 'https://lawnuk.com/wp-content/uploads/2016/08/sprogs-dogs.jpg'
        },
    }
  },
  methods: {
    onSubmit(post) {
      console.log('Post editing!');
      console.log(post);
    }
  }
}
</script>