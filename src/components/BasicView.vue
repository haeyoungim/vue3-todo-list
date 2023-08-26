<template>
  <div class="container">
  <h2>To-Do List</h2>
    <input class="form-control"
           type="text"
           v-model="searchText"
           placeholder="Search">
    <hr/>
    <TodoSimpleForm @add-todo="addTodo"/>
<div v-if="!filteredTodos.length">
    there is noting to display
</div>
  <TodoList :todos="filteredTodos"
            @toggle-todo="toggleTodo"
            @delete-todo="deleteTodoApp"/>
  </div>
</template>

<script>
import TodoSimpleForm from "@/components/TodoSimpleForm.vue";
import TodoList from "@/components/TodoList.vue";
import {ref,computed} from "vue";

export default {
  components:{
    TodoSimpleForm,
    TodoList
  },
  setup(){
    const todos = ref([]);
    const todoStyle ={
      textDecoration: 'line-through',
      color:'gray'
    }

    const deleteTodoApp = (index) => {
      todos.value.splice(index,1);
    };

    const addTodo = (todo) => {
      todos.value.push(todo);
    };

    const toggleTodo = (index) => {
      // console.log(todos.value[index]);
      todos.value[index].completed = !todos.value[index].completed
    };

    const searchText = ref('');
    const filteredTodos = computed(() => {
      if (searchText.value) {
        return todos.value.filter(todo => {
          return todo.subject.includes(searchText.value);
        });
      }
      return todos.value;
    });

    return{
      todos,
      todoStyle,
      deleteTodoApp,
      addTodo,
      toggleTodo,
      searchText,
      filteredTodos
    }
  }
}
</script>

<style>
  /*.todo{*/
  /*  color:gray;*/
  //  text-decoration: line-through;
  //}

</style>