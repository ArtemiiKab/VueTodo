<template>

  <div class="TodoList">
    <div class="TodoList__container">
      <h3>Total todos: {{todos.length}}</h3>
      <ul>
        <Todo
          v-for="(todo, i) in todos"
          :todo="todo"
          @remove-todo="removeTodo"
          :key="todo.title"
          :index="i"
        />
      </ul>
    </div>
    <TodoInput
        :theme="theme"
        @add-todo="addTodo"
        class="TodoList__input"
    />
    
  </div>
</template>

<script>
import Todo from './Todo';
import TodoInput from './TodoInput';

export default {
  props:['todos', 'theme'],
  components:{
    Todo,
    TodoInput,
  },

  methods:{
    removeTodo(id){
      this.$emit('remove-todo', id);
    },

    addTodo(title) {
      this.$emit('add-todo', title)
    }
  }

}
</script>

<style scoped>
  ul {
    list-style: none;
    margin: 0;
    padding: 2rem;
    display:flex;
    flex-direction: column;
    align-items: center;
  }

  h3 {
    padding-top: 3rem;
    padding-left: 2.5rem;
  }

  .TodoList {
    display:grid;
    grid-template-columns: 6fr 5fr;
  }

  .TodoList__container {
    text-align: left;
    box-shadow: 0px 10px 10px 5px #0F1423;
    border-radius: 8px;
    transition: all 1.2s;
  }

  .TodoList__container:hover{
    transform: scale(1.05);
  }

  @media(max-width: 800px) {
    .TodoList {
      grid-template-columns: 1fr;
    }

    .TodoList__input {
      grid-row: 1;
      margin-bottom: 50px;
    }

    ul {
      margin-top: 50px;
    }
  }
</style>