<template>
  <div id="app">    
    <nav class="navbar navbar-dark bg-dark-blue">
      <div class="container">
        <a href="#" class="navbar-brand">Learn Vue: ToDo</a>
      </div>
    </nav>
    <div class="container">
      <TodoList :todos="todos" />  

    </div>
  </div>
</template>

<script>
import TodoList from './components/TodoList.vue'
export default {
  name: 'App',
  components: {
    TodoList
  },
  data() {
    return {
      todos: [
        {title: 'Setup environment', dueDate: new Date(2020,0,24), completed: true},
        {title: 'Create main list of components', dueDate: new Date(2020,2,24), completed: false},
        {title: 'Display TODO items', completed: false}
      ]
    }
  }
}
</script>
