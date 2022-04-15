<template>
  <div class="container">
    <Header title="Task Tracker"/>
    <Tasks
        @toggle-reminder="toggleReminder"
        @delete-task="deleteTask"
        :tasks="tasks"/>
  </div>
</template>

<script>
import Header from "@/components/Header";
import Tasks from "@/components/TaskList";

export default {
  name: 'App',
  components: {
    Header,
    Tasks
  },
  data() {
    return {
      tasks: []
    }
  },
  methods: {
    deleteTask(id) {
      this.tasks = this.tasks.filter((task) => task.id !== id);
    },
    // check if task id matches, if it does, change the boolean value to the opposite
    toggleReminder(id) {
      this.tasks = this.tasks.map((task) => task.id === id
          ? {...task, reminder: !task.reminder} : task)
    }
  },
  created() {
    this.tasks = [
      {
        id: 1,
        text: 'Provezbaj AEM/Vue strukturu',
        day: '15 April 2022',
        reminder: true,
      },
      {
        id: 2,
        text: 'Zavrsi projekat iz Web sistema',
        day: '17 April 2022',
        reminder: true,
      },
      {
        id: 3,
        text: 'Odraditi FE walkthrough na FSBP projektu',
        day: '18 April 2022',
        reminder: true,
      },
      {
        id: 4,
        text: 'Upiši sate za danas i naruči hranu za sutra',
        day: 'Svaki dan',
        reminder: false,
      },
    ]
  }
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Poppins:ital,wght@0,100;0,200;0,300;1,300&display=swap');

* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

body {
  font-family: 'Poppins', sans-serif;
}

.container {
  max-width: 500px;
  margin: 30px auto;
  overflow: auto;
  min-height: 300px;
  border: 1px solid steelblue;
  padding: 30px;
  border-radius: 5px;
}

.btn {
  display: inline-block;
  background: #000;
  color: #fff;
  border: none;
  padding: 10px 20px;
  margin: 5px;
  border-radius: 5px;
  cursor: pointer;
  text-decoration: none;
  font-size: 15px;
  font-family: inherit;
}

</style>
