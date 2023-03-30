<template>
  <div class="app">
    <h1>Сторінка з постами</h1>
    <my-button @click="fetchPosts">Отримати пости</my-button>
    <my-button @click="showDialog" style="margin: 12px 0" >Створити пост</my-button>
    <my-dialog v-model:show="dialogVisible">
    <post-form @create="createPost" />
    </my-dialog>

    <post-list :posts="posts" @remove="removePost" />
  </div>
</template>

<script>
import PostForm from "@/components/PostForm.vue";
import PostList from "@/components/PostList.vue";
import MyButton from "@/components/UI/MyButton.vue";
import axios from 'axios'
export default {
  components: { PostForm, PostList },
  data() {
    return {
      posts: [
        // { id: 1, title: "Vue", body: "About Vue" },
        // { id: 2, title: "React", body: "About React" },
        // { id: 3, title: "Angular", body: "About Angular" },
        // { id: 4, title: "Node.js", body: "About Node" },
      ],
      dialogVisible: false,
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
    async fetchPosts(){
      try{
        const response = await axios.get('https://jsonplaceholder.typicode.com/posts', {
                params: {
                    _page: 1,
                    _limit: 10
                }
            });
            this.posts = response.data
            // console.log(response);
      }catch(err){
        alert("Помилка")
      }
    }
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
</style>
