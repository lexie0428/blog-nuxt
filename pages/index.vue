<template>
  <div class="wrapper-content wrapper-content--fixed">
    <promo />
    <Intro title="My last posts:" />
    <PostsList :posts="postLoaded" />
    <contacts />
  </div>
</template>

<script>
import promo from "@/components/Promo.vue";
import contacts from "@/components/Contacts.vue";

export default {
  components: { promo, contacts },
  // asyncData(context) {
  //   return new Promise((resolve, reject) => {
  //     setTimeout(() => {
  //       resolve({
  //         postLoaded: [
  //           {
  //             id: 1,
  //             title: "1 post",
  //             descr:
  //               "Lorem Ipsum is simply dummy text of the printing and typesetting industry.",
  //             img:
  //               "https://lawnuk.com/wp-content/uploads/2016/08/sprogs-dogs.jpg"
  //           },
  //           {
  //             id: 2,
  //             title: "2 post",
  //             descr:
  //               "Lorem Ipsum is simply dummy text of the printing and typesetting industry.",
  //             img:
  //               "https://iheartdogs.com/wp-content/uploads/2017/09/Brite-Bite-0021-2.jpg"
  //           },
  //           {
  //             id: 3,
  //             title: "3 post",
  //             descr:
  //               "Lorem Ipsum is simply dummy text of the printing and typesetting industry.",
  //             img:
  //               "https://icdn.lenta.ru/images/2020/02/29/00/20200229005638945/square_1024_d3581903668a66b3bc36dd631b3544ea.jpg"
  //           }
  //         ]
  //       });
  //     }, 1500);
  //   })
  //     .then(data => {
  //       return data;
  //     })
  //     .catch(e => {
  //       context.error(e);
  //     });
  // }
  computed: {
    postLoaded () {
      return this.$store.getters.getPostsLoaded
    }
  }
};
</script>
