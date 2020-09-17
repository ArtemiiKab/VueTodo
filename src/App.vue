<template>
  <div id="app" :class="theme?'light':'dark'" class='app'>
   <ThemeToggler :theme="theme" @toggle-theme="toggleTheme" />
   <h1>Todo app </h1>
   <TodoList
     :todos='todos'
     @remove-todo="removeTodo"
     @add-todo="addTodo"
     :theme="theme"
   />
  </div>
</template>

<script>
import TodoList from './components/TodoList';
import ThemeToggler from './components/ThemeToggler';

export default {

  name: 'App',
  components: {
    TodoList,
    ThemeToggler,
  },

  data() {
    return {
      todos:[
        {id:1, title: 'Buy dino', completed:false},
        {id:2, title: 'Tame tiger', completed:false},
        {id:3, title: 'Buy second dino', completed:false},
      ],

      theme: true,
    }
  }, 

  methods:{
    removeTodo(id) {
      this.todos = this.todos.filter(t => t.id !== id);
    },

    addTodo(title) {
      this.todos.push({id: this.todos.length + 1, title:title, completed:false})
    },

    toggleTheme(T) {
      this.theme = T;
    }
  }

}
</script>

<style lang="scss">
  $mainColor: rgb(43,55,96);
  $shadowColor: rgb(14, 20, 41);
  $lightColor: #f79393;
  $lightShadow:#E56464;
 
  .app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    padding:10%;
    transition:'background-color' 1.4s;
  }

  .light {
    background:radial-gradient($lightColor, $lightShadow);
    color:black;
  }

  .dark {
    background:radial-gradient($mainColor,  $shadowColor);
    color: #f5f8fa;
  }

</style>
