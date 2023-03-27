<template>
  <div class="app">
    <form @submit.prevent>
        <h4>Створення посту</h4>
        <input
         v-bind:value="title" 
         @input="title = $event.target.value"
         class="input" 
         type="text" 
         placeholder="Назва">
        <input 
        v-bind:value="body" 
        @input="body = $event.target.value"
        class="input"
         type="text" 
         placeholder="Опис">
        <button 
        class="btn"
         @click="createPost">Створити
         </button>

    </form>
    <div class="post" v-for="post in posts">
        <div><strong>Назва :</strong> {{post.title}}</div>
        <div><strong>Опис :</strong> {{post.body}}</div>
  
    </div>

  </div>
</template>

<script>
export default {
  data() {
    return {
   posts:[
    {id :1 , title : "Vue" , body :"About Vue"},
    {id :2 , title : "React" , body :"About React"},
    {id :3 , title : "Angular" , body :"About Angular"},
    {id :4 , title : "Node.js" , body :"About Node"},
   ],
   title : "" ,
   body :""
    };
  },
  methods: {
    createPost(evt){
    
   const newPost = {
    id:Date.now(),
    title : this.title,
    body : this.body
  }
 
   this.posts.push(newPost);
   this.title = "";
   this.body = "";


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
.post{
    padding: 20px;
    border: 2px solid teal;
    margin: 12px;
   
}
form{
    display: flex;
    flex-direction : column; 
} 
.input{
    width: 100%;
    border: 1px solid teal;
    padding: 10px 16px;
    margin-top: 12px;
}
.btn{
    margin-top: 12px;
    align-self: flex-end;
    padding: 10px 14px;
    background: none;
    color: teal;
    border: 1px solid teal;
}
</style>
