<template>
  <div>
    <div class="row">
      <div class="col-md-10 col-md-offset-1">
        <div class="well">
          <h2>Create a New Todo</h2>
          <form>
            <div class="form-group">
              <label for="TodoItem">Todo Item</label>
              <input type="text" v-model="input" class="form-control" id="todoitem" placeholder="Todo Item">
            </div>
            <button type="button" v-on:click="add()" class="btn btn-default">Create</button>
          </form>
        </div>
      </div>
    </div>
    <div class="row">
      <div class="col-md-10 col-md-offset-1">
        <h2>List</h2>
        <ul class="list-group">
          <li 
            v-for="(todo, index) in todos" 
            :key="index" 
            class="list-group-item" 
            @click="e => e.target.classList.toggle('completed')"
          >
            {{ index }}: {{ todo }}
            <span class="button pull-right">
              <button type="button" v-on:click="remove(index)" class="btn btn-danger">Remove</button>
            </span>
          </li>
        </ul>
      </div>
    </div>
  </div>
</template>

<script>
  export default {
    name: "Todo",
    data() {
      return {
        todos: ["Learn Vue", "Buy groceries", "Make a Todo List"],
        input: ""
      }
    },
    methods: {
      add() {
        this.todos.push(this.input);
        this.input = "";
      },
      remove(index) {
        this.todos.splice(index, 1);
      }, 
      strike(todo) {

      }
    }
  }
</script>
<style scoped>
  .completed {
    text-decoration: line-through;
  }

  li.list-group-item {
    padding: 2em;
    margin-bottom: 0.5em;
    font-size: 20px;
  }

  li.list-group-item:hover {
    box-shadow: inset 0 0 0 4px #b8b95d, 0 0 1px rgba(0, 0, 0, 0);
    cursor: pointer;
  }

  button.btn.btn-danger {
    text-decoration: none !important;
  }
</style>
