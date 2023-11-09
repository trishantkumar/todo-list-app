<template>
  <div class="main">
    <div class="container">
      <div class="heading">
        <div>ToDo App</div>
      </div>
      <div class="add_todo_container">
        <div class="todo_label">Add ToDo</div>
        <div class="add_todo">
          <input type="text" class="" v-model="newTodoText" placeholder="Add ToDo"/>
        </div>
        <button @click="addTodo()">Add New ToDo</button>
      </div>
      <div class="todo_list_container">
        <div class="list_lable">List of ToDo:</div>
        <ul class="todo" v-if="todoList && todoList.length">
          <li class="todo_inner" v-for="(todo, index) in todoList" :key="index">
            <div>• {{ todo }}</div>
            <div class="remove_button" @click="removeTodo(index)">&#x2716;</div>
          </li>
        </ul>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue';
const todoList = ref([])
const newTodoText = ref('')

function addTodo() {
  todoList.value.push(newTodoText.value);
  newTodoText.value = '';
}

function removeTodo(index) {
  todoList.value.splice(index, 1);
}
</script>

<style lang="scss">
.main {
  color: #fff;
  font-family: Arial, Helvetica, sans-serif;
  margin-top: 2rem;
  box-sizing: border-box !important;
  .container {
    width: 600px;
    margin: auto;
    .heading {
      font-weight: bold;
      font-size: 3rem;
    }
    .add_todo_container {
      margin-top: 2rem;
      .todo_label {
        font-weight: 600;
        font-size: 1.5rem;
        text-align: left;
      }
      .add_todo {
        padding-top: 0.5rem;
        input {
          width: 100%;
          padding: 16px 20px;
          border: none;
          border-radius: 4px;
          background-color: #f1f1f1;
          box-sizing: border-box;
        }
        input[type=text]:focus {
          border: none;
        }
      }
      button {
        background: #645bff;
        border: 2px solid white;
        color: white;
        padding: 20px;
        font-weight: 600px;
        text-align: center;
        text-decoration: none;
        display: inline-block;
        font-size: 16px;
        margin-top: 1rem;
        cursor: pointer;
        border-radius: 8px;
        width: 100%;
      }
    }
    .todo_list_container {
      background-color: #fff;
      color: black;
      border-radius: 8px;
      padding: 1rem;
      margin-top: 2rem;
      .list_lable {
        font-weight: 600;
        font-size: 1.5rem;
      }
      .todo {
        text-align: left;
        margin-top: 1rem;
        padding: 0 5px;
        .todo_inner {
          display: flex;
          justify-content: space-between;
          border-bottom: 1px solid #e0e0e0;
          padding: 10px 0;
          .remove_button {
            font-weight: bold;
            font-size: 20px;
            cursor: pointer;
            color: #3b71ca;
          }
        }
      }
    }
  }
}
</style>
