<template>
  <div id="app">
    <todo-header></todo-header>
    <todo-input
      v-on:add="addTodoItem"
    ></todo-input>
    <todo-list
      v-bind:todolist="todoItems"
      v-on:remove="removeTodoItem"
      >
    </todo-list>
    <todo-footer v-on:clear="removeAllItems"></todo-footer> 
  </div>
</template>

<script>

import TodoHeader from './components/TodoHeader.vue';
import TodoInput from './components/TodoInput.vue';
import TodoList from './components/TodoList.vue';
import TodoFooter from './components/TodoFooter.vue';

export default {
  components: {
    'todo-header':TodoHeader,
    'todo-input':TodoInput, 
    'todo-footer':TodoFooter, 
    'todo-list':TodoList,
  },
  data() {
    return {
      todoItems: []
    }
  },
  methods: {
    fetchTodoItems: function() {
      for (var i =0; i < localStorage.length; i++){
          var item = localStorage.key(i);
          this.todoItems.push(item);            
      }
    },
    addTodoItem: function(value) {
      // 배열에 추가
      this.todoItems.push(value);
      // 저장소에 저장
      localStorage.setItem(value, value);
    },
    removeTodoItem: function() {
      console.log('deleted', todo, index);
      this.todoItems.spliace(index, 1);
      //저장소에서 삭제
      localStorage.removeitem(todo);
    },
    removeAllItems: function() {
      this.todoItems = [];
      localStorage.clear();
    }
  },
  created: function() {
    this.fetchTodoItems();
  }
}
</script>

<style>

</style>
