<template>
  <no-ssr>
    <commentTable :thead="['Name', 'Text', 'Status', 'Change Status', 'Delete']">
      <tbody slot="tbody">
        <tr v-for="comment in comments" :key="comment.id">
          <td>
            <span>{{comment.name}}</span>
          </td>
          <td>
            <span>{{comment.text}}</span>
          </td>
          <td>
            <span v-if="comment.publish" class="status true">Publish</span>
            <span v-else class="status false">Hidden</span>
          </td>
          <td>
            <span @click="changeComment(comment)" class="link">Change status</span>
          </td>
          <td>
            <span @click="deleteComment(comment.id)" class="link">Delete</span>
          </td>
        </tr>
      </tbody>
    </commentTable>
  </no-ssr>
</template>

<script>
import axios from "axios";
import commentTable from "@/components/Admin/CommentTable.vue";

export default {
  components: { commentTable },
  layout: "admin",
  data() {
    return {
      comments: []
    };
  },
  mounted() {
    this.loadComments();
  },
  methods: {
    changeComment(comment) {
      comment.publish = !comment.publish;
      axios.put(`https://blog-nuxt-6f33e.firebaseio.com/comments/${comment.id}.json`, comment)
    },
    deleteComment(id) {
      axios.delete(`https://blog-nuxt-6f33e.firebaseio.com/comments/${id}.json`)
      .then((res) => {this.loadComments()})
    },
    loadComments() {
      axios.get("https://blog-nuxt-6f33e.firebaseio.com/comments.json")
      .then(res => {
        let commentArray = [];
        Object.keys(res.data).forEach(key => {
          const comment = res.data[key];
          commentArray.push({...comment, id: key});
        })
        this.comments = commentArray;
      });
    }
  }
};
</script>