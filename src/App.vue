<template>
  <div class="app">
    <h1>Сторінка з постами</h1>
    <div class="app__btns">
      <my-button @click="showDialog" >Створити пост</my-button>
      <my-select 
      v-model="selectedSort"
      :options="sortOptions"
      />
    </div>
    <my-dialog v-model:show="dialogVisible">
      <post-form @create="createPost" />
    </my-dialog>

    <post-list :posts="posts" @remove="removePost" v-if="!isPostLoading" />
    <div v-else>Завантажується ...</div>
  </div>
</template>

<script>
import PostForm from "@/components/PostForm.vue";
import PostList from "@/components/PostList.vue";
import MyButton from "@/components/UI/MyButton.vue";
import MySelect from "@/components/UI/MySelect.vue";
import axios from "axios";
export default {
  components: { PostForm, PostList, MyButton, MySelect },
  data() {
    return {
      posts: [
        // { id: 1, title: "Vue", body: "About Vue" },
        // { id: 2, title: "React", body: "About React" },
        // { id: 3, title: "Angular", body: "About Angular" },
        // { id: 4, title: "Node.js", body: "About Node" },
      ],
      dialogVisible: false,
      isPostLoading: false,
      selectedSort:"",
      sortOptions: [
            {value: 'title', name: 'По названию'},
            {value: 'body', name: 'По содержимому'},
        ]
    };
  },
  methods: {
    createPost(post) {
      this.posts.push(post);
      this.dialogVisible = false;
    },
    removePost(post) {
      this.posts = this.posts.filter((p) => p.id !== post.id);
    },
    showDialog() {
      this.dialogVisible = true;
    },
    async fetchPosts() {
      try {
        this.isPostLoading = true;
        const response = await axios.get(
          "https://jsonplaceholder.typicode.com/posts",
          {
            params: {
              _page: 1,
              _limit: 10,
            },
          }
        );
        this.posts = response.data;
        // console.log(response);
      } catch (err) {
        alert("Помилка");
      } finally {
        this.isPostLoading = false;
      }
    },
  },
  mounted() {
    this.fetchPosts();
  },
};
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  border-radius: 4px;
}

.app {
  padding: 18px;
}

.app__btns {
  margin: 12px 0;
  display: flex;
  justify-content:space-between;
}
</style>
