<template>
  <div class="container">
  <h2>To-Do List</h2>
    <TodoSimpleForm/>

<div v-if="!todos.length">
    추가된 Todo가 없습니다.
</div>
    <div v-for="(todo,index) in todos"
         :key="todo.id"
         class="card mt-2">

      <div class="card-body p-2 d-flex align-items-center">
        <div class="form-check flex-grow-1">
          <input class="form-check-input"
                 type="checkbox"
                  v-model="todo.completed">
          <label class="form-check-label"
                 :class="{ todo: todo.completed  }">
            {{todo.subject}}
          </label>
        </div>
        <div>
          <button class="btn btn-danger bts-sm"
                  @click="deleteTodo(index)">
            Delete
          </button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import TodoSimpleForm from "@/components/TodoSimpleForm.vue";


export default {
  components:{
    TodoSimpleForm
  },
  setup(){

    const todoStyle ={
      textDecoration: 'line-through',
      color:'gray'
    }


    return{
      todoStyle,
    }
  }
}
</script>

<style>
  .todo{
    color:gray;
    text-decoration: line-through;
  }

</style>