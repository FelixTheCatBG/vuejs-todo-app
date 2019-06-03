<template>
  <div class='ui centered card'>
    <div class="content" v-show="!isEditing">
      <div class='header'>    <input v-model="todo.done" :disabled="todo.done" v-on:click="completeTodo(todo)" type="checkbox" />
          {{ todo.title }}
      </div>
      
      <div class='extra content'>           
        <span class='right floated trash icon ' v-on:click="deleteTodo(todo)">
           <i class='trash icon large'></i>
        </span>
       <span class='right floated edit icon' v-on:click="showForm">
         <i class='edit icon large'></i>
        </span>      
        <span>        
        </span>
      </div>
    </div>
 
    <div class="content" v-show="isEditing">
      <div class='ui form'>
        
        <div class='field'>
          <label>Title</label>         
          <input type='text' v-model="todo.title" >
        </div>
        
        <div class='ui two button attached buttons'>
          <button class='ui basic blue button' v-on:click="hideForm">
            Close X
          </button>
        </div>
      </div>
    </div>
    
    <div class='ui bottom attached green  button' v-show="!isEditing &&todo.done" disabled>
        Completed
    </div>
    <div class='ui bottom attached red  button' v-on:click="completeTodo(todo)" v-show="!isEditing && !todo.done">
        Pending
    </div>
  </div>
</template>

<script type="text/javascript">
  export default {
    props: ['todo'],
    data() {
      return {
        isEditing: false,
      };
    },
    methods: {
      completeTodo(todo) {
        this.$emit('complete-todo', todo);
      },
      deleteTodo(todo) {
        this.$emit('delete-todo', todo);
      },
      showForm() {
        this.isEditing = true;
      },
      hideForm() {
        this.isEditing = false;
      },
    },
  };
</script>
<style>
.ui.card>.content, .ui.cards>.card>.content {background-color: #CDC7D9}
</style>
