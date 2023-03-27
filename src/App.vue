<template>
  <div class="app">
    <post-form
    @create="createPost"
    />
    <post-list 
    :posts="posts"
   
    />
    

  </div>
</template>

<script>
import PostForm from '@/components/PostForm.vue';
import PostList from '@/components/PostList.vue';

export default {
  components: { PostForm , PostList},
  data() {
  
    return {
   posts:[
    {id :1 , title : "Vue" , body :"About Vue"},
    {id :2 , title : "React" , body :"About React"},
    {id :3 , title : "Angular" , body :"About Angular"},
    {id :4 , title : "Node.js" , body :"About Node"},
   ],

    };
  },
  methods: {
    createPost(post){
    this.posts.push(post)

    },
  },
};
</script>

<style >
* {
    margin : 0;
    padding: 0;
    box-sizing: border-box;
     border-radius: 4px;
}
.app{
    padding: 18px;
}


</style>