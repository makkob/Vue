<template>
    <button class="btn">
      <slot></slot>
    </button>
  </template>
  
  <script>
  export default {
    name: 'my-button'
  }
  </script>
  
  <style scoped>

  .btn {
  margin-top: 10px;
  align-self: flex-end; 
  padding: 10px 14px;
  background: rgb(219, 252, 255);
  color: teal;
  border: 1px solid teal; 
  min-width: 92px;
  border-radius: 4px;
 } 
 .btn:hover{
  cursor: pointer;
  background: rgb(43, 202, 202);
  color: white;
  border: solid 1px rgb(14, 92, 92);
 }
  </style>