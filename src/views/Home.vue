<template>
  <AddTask v-show="showAddTask" @add-task="addTask"/>
  <Tasks @toggle-reminder="toggleReminder" @delete-task="deleteTask" :tasks="tasks"/>
</template>

<script>
import AddTask from "@/components/AddTask.vue";
import Tasks from "@/components/Tasks.vue";

export default {
  name: "Home",
  components: {
    AddTask,
    Tasks,
  },
  props: {
    showAddTask: Boolean
  },
  data() {
    return {
      tasks: [],
    }
  },
  methods: {
    async deleteTask(id) {
      if (confirm("Are u sure?")) {
        const res = await fetch(`api/tasks/${id}`, {
          method: "DELETE"
        })
        res.status === 200 ? this.tasks = this.tasks.filter(task => task.id !== id) : alert("Error deleting task")
      }
    },
    async toggleReminder(id) {
      const task = await this.fetchTask(id)
      const updatedTask = {...task, reminder: !task.reminder}

      const res = await fetch(`api/tasks/${id}`, {
        method: "PUT",
        headers: {
          "Content-Type": "application/json"
        },
        body: JSON.stringify(updatedTask)
      })

      const data = await res.json()

      this.tasks = this.tasks.map(task => task.id === id ? {...task, reminder: data.reminder} : task)
    },
    async addTask(task) {
      const res = await fetch("api/tasks", {
        method: "POST",
        headers: {
          "Content-Type": "application/json"
        },
        body: JSON.stringify(task)
      })
      const data = await res.json()
      this.tasks = [...this.tasks, data]
    },
    async fetchTasks() {
      const res = await fetch("api/tasks")
      return res.json();
    },
    async fetchTask(id) {
      const res = await fetch(`api/tasks/${id}`)
      return res.json()
    }
  },
  async created() {
    this.tasks = await this.fetchTasks()
  },
}
</script>