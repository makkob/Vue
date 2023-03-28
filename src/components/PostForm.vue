<template>
  <form @submit.prevent>
    <h4>Створення посту</h4>
    <my-input v-model="post.title"  type="text" placeholder="Назва" />
    <my-input v-model="post.body"  type="text" placeholder="Опис" />
    <my-button class="btn" @click="createPost" style="align-self: flex-end;">Створити</my-button>
  </form>
</template>

<script>
import MyButton from './UI/MyButton.vue';
export default {
  components: { MyButton },
  data() {
    return {
      post: {
        title: "",
        body: "",
      },
    };
  },
  methods: {
    createPost() {
      this.post.id = Date.now();
      this.$emit('create', this.post)
      this.post = {
        title: '',
        body: ''
  };
}

  },
};
</script>

<style scoped>
form {
  display: flex;
  flex-direction: column;
}



</style>
