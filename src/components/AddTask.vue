<template>
  <form @submit="onsubmit()" class="add-form">

    <div class="form-control">
      <label>Task</label>
      <input type="text" v-model="text" name="text" placeholder="Add Task"/>
    </div>

    <div class="form-control">
      <label>Date</label>
      <input type="text" v-model="day" name="day" placeholder="Date"/>
    </div>

    <div class="reminder-save-inline">
      <div class="form-control form-control-check">
        <label>Set Reminder</label>
        <input type="checkbox" v-model="reminder" name="reminder"/>
      </div>

      <input type="submit" value="Save Task" class="btn btn-block">
    </div>

  </form>
</template>

<script>
export default {
  name: "AddTask",
  data() {
    return {
      text: '',
      day: '',
      reminder: false
    }
  },
  methods: {
    onSubmit(e, taskArraySize) {
      e.preventDefault()

      if(!this.text) {
        alert('Please add a task')
        return
      }

      const newTask = {
        id: taskArraySize + 1,
        text: this.text,
        day: this.day,
        reminder: this.reminder
      }

      this.$emit('add-task', newTask);

      this.text = '';
      this.day = '';
      this.reminder = false;

    }
  }
}
</script>

<style scoped>
.add-form {
  margin-bottom: 40px;
}

.form-control {
  margin: 20px 0;
}

.form-control label {
  display: block;
}

.form-control input {
  width: 100%;
  height: 40px;
  margin: 5px;
  padding: 3px 7px;
  font-size: 17px;
}

.form-control-check {
  display: flex;
  align-items: center;
  justify-content: space-between;
}

.form-control-check input {
  margin-left: 10px;
  height: 20px;
  width: 18px;
}

.reminder-save-inline {
  display: flex;
  height: 55px;
  justify-content: space-between;
}

.btn {
  float: right;
}
</style>
