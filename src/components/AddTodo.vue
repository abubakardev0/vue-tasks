<template>
  <form @submit.prevent="addTodo()">
    <div
      class="flex justify-between w-full bg-white rounded-md pl-3 pr-2 py-1 focus:outline-none text-neutral-800"
    >
      <input
        type="text"
        placeholder="Add new task"
        class="w-full focus:outline-none"
        v-model="newTask"
      />
      <button class="w-fit btn btn--primary">
        <svg
          xmlns="http://www.w3.org/2000/svg"
          fill="none"
          viewBox="0 0 24 24"
          stroke-width="1.5"
          stroke="currentColor"
          class="w-6 h-6"
        >
          <path
            stroke-linecap="round"
            stroke-linejoin="round"
            d="M12 4.5v15m7.5-7.5h-15"
          />
        </svg>
      </button>
    </div>
  </form>
</template>

<script>
export default {
  data() {
    return {
      newTask: "",
    };
  },
  methods: {
    addTodo() {
      if (this.newTask.length === 0) {
        alert("Please enter a task");
        return;
      }
      this.$emit("on-add", this.newTask);
      this.newTask = "";
    },
  },
};
</script>
