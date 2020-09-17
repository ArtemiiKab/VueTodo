<template>
    <li>
       <span :class='{completed: todo.completed}'>
         <input type="checkbox" @change='toggleTodo' />
         <span>{{index + 1 +'.'}}</span>
         {{todo.title}}
       </span>
       <button
         type="button"
         class="btn-rm"
         @click="$emit('remove-todo', todo.id)"
       >
         &times;
       </button>
    </li>
</template>

<script>
  export default {
    props: {
      todo: {
        type: Object,
        required: true,
      },

      index: {
         type:Number,
         required: true,
      }
    },
    methods:{
     toggleTodo(){
       this.todo.completed = !this.todo.completed
     },
    }, 
  }
</script>

<style scoped>
  li {
    box-shadow: 0px 5px 8px 1px #0F1423;
    padding: .5rem 2rem;
    margin-bottom: 1rem;
    border-radius: 8px;
    display: flex;
    align-items: center;
    justify-content: space-between;
    width: 80%;
    background-color: #fff;
    color:black;
  }

  li:hover{
    box-shadow: 0px 0px 1px 2px #E56464;
  }

  .btn-rm {
    color: #fff;
    background-color: #E56464;
    border-radius: 50%;
    font-weight: bold;
    border: none;
  }

  .completed {
    text-decoration: line-through;
  }

  input {
    margin-right: 1rem;
     
  }
</style>