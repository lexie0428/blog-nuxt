<template>
  <PostsList :posts="posts" />
</template>

<script>
export default {
  layout: "admin",
  data() {
    return {
      posts: [
        {
          id: 1,
          title: "1 post",
          descr:
            "Lorem Ipsum is simply dummy text of the printing and typesetting industry.",
          img: "https://lawnuk.com/wp-content/uploads/2016/08/sprogs-dogs.jpg"
        },
        {
          id: 2,
          title: "2 post",
          descr:
            "Lorem Ipsum is simply dummy text of the printing and typesetting industry.",
          img:
            "https://iheartdogs.com/wp-content/uploads/2017/09/Brite-Bite-0021-2.jpg"
        },
        {
          id: 3,
          title: "3 post",
          descr:
            "Lorem Ipsum is simply dummy text of the printing and typesetting industry.",
          img:
            "https://icdn.lenta.ru/images/2020/02/29/00/20200229005638945/square_1024_d3581903668a66b3bc36dd631b3544ea.jpg"
        }
      ]
    };
  }
};
</script>
