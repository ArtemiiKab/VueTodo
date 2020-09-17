<template>
    <div>
      <form @submit.prevent="addTodo">
        <input
          type="text"
          v-model.trim="inputVal"
          placeholder="input task..."
        />
        <button
          type="submit"
          :class="theme ?'blue':'red'"
        >
          Add
        </button>
      </form>
    </div>
</template>

<script>
export default {
    props:['theme'],

    data(){
      return {
          inputVal:'',
      }
    },

    methods:{
      addTodo(){
          if (this.inputVal.length === 0){
            return
          }
          this.$emit('add-todo', this.inputVal);
          this.inputVal = '';
      }
    }
}
</script>

<style scoped>
  button {
    
    color: #f5f8fa;
    font-weight: bold;
    transition: all 0.5s;
  }

  .blue {
    background-color:rgb(43,55,96)
  }

  .red {
    background-color:#E56464;
  }

  button:hover {
    transform: scale(1.1);
  }

  input {
    margin-right:10px;
  }

  button,
  input {
    border-radius: 8px;
    border:none;
    padding: .8rem;
  }
</style>