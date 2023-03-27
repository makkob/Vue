<template>
   
        <form @submit.prevent>
        <h4>Створення посту</h4>
        <input
         v-bind:value="post.title" 
         @input="post.title = $event.target.value"
         class="input" 
         type="text" 
         placeholder="Назва">
        <input 
        v-bind:value="post.body" 
        @input="post.body = $event.target.value"
        class="input"
         type="text" 
         placeholder="Опис">
        <button 
        class="btn">
         Створити   
         </button>

    </form>
   
  
  </template>
  
  <script>


  export default {
    data(){
        return{

            post:{
                title :'',
                body : ''
            }
        }
    }
  }
  
  </script>
  
  <style scoped>
  form {
    display: flex;
    flex-direction: column;
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