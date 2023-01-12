<template>
  <form @submit="onSubmit" class="add-form">
    <div class="form-control">
      <label>Task</label>
      <input v-model="text" type="text" name="text" placeholder="Add Task" />
    </div>
    <div class="form-control">
      <label>Day & Time</label>
      <input
        v-model="day"
        type="text"
        name="day"
        placeholder="Add Day & Time"
      />
    </div>
    <div class="form-control form-control-check">
      <label>Set Reminder</label>
      <input v-model="rem" type="checkbox" name="reminder" />
    </div>

    <input type="submit" value="Save Task" class="btn btn-block" />
  </form>
</template>

<script>

export default {
  name: "AddTAsk",
  data() {
    return {
      text: "",
      day: "",
      reminder: false,
    };
  },
  methods:{
    onSubmit(e){
        e.preventDefault();
        if(!this.text){
            alert("Please add text");
            return
        }

        const newTask = {
            id: Math.floor(Math.random() * 100000000),
            text: this.text,
            day: this.day,
            reminder: this.reminder
        }

        this.text = '';
        this.day = '';
        this.reminder = false;

        this.$emit('add-task', newTask)
    }
  }
};
</script>
