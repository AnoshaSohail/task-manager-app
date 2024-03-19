<template>
  <div>
    <TaskForm @add-task="addNewTask"></TaskForm>
    <div v-for="task in tasks" :key="task.id">
      <input type="text" v-model="task.title" :disabled="!task.editing" />
      <button @click="toggleEditing(task)">Edit</button>
      <button @click="deleteItem(task.id)">Delete</button>
      <button @click="saveChanges(task)">Save</button>
    </div>
  </div>
</template>
  
  <script>
import TaskForm from "./TaskForm.vue";
export default {
  components: {
    TaskForm,
  },
  data() {
    return {
      tasks: JSON.parse(localStorage.getItem("tasks")) || [],
    };
  },
  methods: {
    addNewTask(newTask) {
      const taskId = this.tasks.length
        ? this.tasks[this.tasks.length - 1].id + 1
        : 1;
      const task = {
        id: taskId,
        title: newTask,
        completed: false,
        editing: false, // Add a new property to track editing state
      };
      this.tasks.push(task);
      localStorage.setItem("tasks", JSON.stringify(this.tasks)); //add new tasks to local storage
    },
    deleteItem(taskId) {
      this.tasks = this.tasks.filter((task) => task.id !== taskId);
      localStorage.setItem("tasks", JSON.stringify(this.tasks));
    },
    toggleEditing(task) {
      task.editing = !task.editing; // Toggle editing state
    },
    saveChanges(task) {
      task.editing = false; // Disable editing mode
      localStorage.setItem("tasks", JSON.stringify(this.tasks)); // Save changes
    },
  },
};
</script>
  