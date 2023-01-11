<template>
  <main class="p-10 grid place-content-center">
    <h1 class="text-center text-5xl font-medium">Vue Tasks</h1>
    <div class="w-96 mt-10 space-y-3">
      <AddTodo @on-add="addTodo($event)" />
      <h3 v-if="todos.length > 0">Your Tasks:</h3>
      <p v-if="todos.length === 0" class="text-center py-20">No tasks found</p>
      <ul class="space-y-1.5 max-h-96 overflow-y-auto list-scrollbar pr-1">
        <li v-for="todo in todos" :key="todo.id">
          <Todo
            :id="todo.id"
            :task="todo.task"
            @on-delete="removeTodo(todo.id)"
            @on-update="updateTodo(todo, $event)"
          />
        </li>
      </ul>
    </div>
  </main>
</template>

<script>
import Todo from "./components/Todo.vue";
import AddTodo from "./components/AddTodo.vue";
export default {
  components: {
    AddTodo,
    Todo,
  },
  data() {
    return {
      todos: [],
    };
  },
  methods: {
    addTodo(todo) {
      this.todos.push({
        id: Date.now(),
        task: todo,
      });
    },
    updateTodo(todo, newTask) {
      todo.task = newTask;
    },
    removeTodo(todoId) {
      this.todos = this.todos.filter((todo) => todo.id !== todoId);
    },
  },
};
</script>
