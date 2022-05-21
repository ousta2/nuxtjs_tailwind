<template>
  <main>
    <h1>Task Board</h1>
    <p>Create a list of tasks</p>
    <nuxt-link to='/about'>about</nuxt-link>

    <div class="create-new">
      <input
        type="text"
        v-model="newTask"
        placeholder="Add a new task"
        @keypress.enter="addTask" />
      <button @click="addTask">Addd</button>
    </div>

    <div class="tasks">
      <Task
        v-for="t in $store.state.tasks"
        :key="t.content"
        :task="t" />
    </div>

  </main>
</template>

<script>
export default {
  data (){
    return {
      newTask: ''
    }
  },
  methods: {
    addTask () {
      if (this.newTask) {
        this.$store.commit('ADD_TASK', this.newTask);
        this.newTask = '';
      }
    }
  }
}
</script>
