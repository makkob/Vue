<template>
    <div class="post" v-for="post in posts">
        <div><strong>Назва :</strong> {{post.title}}</div>
        <div><strong>Опис :</strong> {{post.body}}</div>
  
    </div>
   
  </template>
  
  <script>
 export default {
//   components: {PostItem},
  props: {
    posts: {
      type: Array,
      required: true
    }
  }
}

 
  </script>
  
  <style scoped>

.post{
    padding: 20px;
    border: 2px solid teal;
    margin: 12px;
   
}
  .user-list-item {
    display: inline-block;
    margin-right: 10px;
  }
  .user-list-enter-active,
  .user-list-leave-active {
    transition: all 0.4s ease;
  }
  .user-list-enter-from,
  .user-list-leave-to {
    opacity: 0;
    transform: translateX(130px);
  }
  .user-list-move {
    transition: transform 0.4s ease;
  }
  </style>