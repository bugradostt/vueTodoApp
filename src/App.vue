
<template>
  <div class="content" style="margin: 20px;">
    
  <h1>Todo App</h1>

  <hr>
  <form method="post" @submit.prevent="AddTodo">

    <div class="field">
        <label class="label">Todo List</label>
      <div class="control">
        <input class="input" v-model="todo" type="text" placeholder="Görev ekle">
        
      </div>
    </div>
    
    <button type="submit" class="button is-warning">Ekle</button>
    
</form>
<hr>
<div class="card my-5 mx-5"  v-for="i in todos" v-bind:key="i" >
 
  <div class="card-content">
    <div class="media">
      <div class="media-left">
      </div>
      <div class="media-content">
        <p class="title is-4">{{ i.content }}</p>
        <p class="subtitle is-6">
          <span v-if="i.done == true">
            Yapıldı
          </span>
          <span v-else-if="i.done == false">
            Yapılmadı
          </span>

        </p>
      </div>
    </div>

    
  </div>
</div>


  </div>  
</template>

<script >
import {ref} from 'vue'
export default{
  setup(){
   const todo= ref('');
   const todos = ref([]);

   function AddTodo() {
    todos.value.push({
      done:false,
      content : todo.value,
    });
    todo.value = '';

   }

   return{
    todo,
    todos,
    AddTodo
   }
  },
}
</script>



<style scoped>

</style>


