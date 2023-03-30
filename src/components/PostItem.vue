<template>
  <div class="post">
    <div>
      <div>{{ post.id }}</div>
      <div><strong>Назва:</strong> {{ post.title }}</div>
      <div><strong>Опис:</strong> {{ post.body }}</div>
    </div>
    <div class="post__btn">
        <my-button
        @click="$emit('remove' , post)"
        >
            Видалити
        </my-button>

    </div>
  </div>
</template>

<script>
import { remove } from '@vue/shared';


// console.log("post>>>>>>>>",post);
export default {

  props: {
    post: {
      type: Array,
      required: true,
    },
  },
};
</script>

<style>

.post {
  padding: 10px;
  border: 2px solid teal;
  margin-top: 10px;
  display: flex;
  align-items: center;
  justify-content: space-between;
}
</style>
