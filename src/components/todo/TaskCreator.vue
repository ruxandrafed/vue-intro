<template>
  <form v-on:submit.prevent="addTask">
    <input  type="text" v-model="newTaskTitle" v-el:title-input></input>
    <button type="submit">Add</button>
  </form>
</template>

<script>
export default {
  data () {
    return {
      newTaskTitle: ''
    }
  },
  methods: {
    addTask () {
      this.$dispatch('new-task', this.newTaskTitle);
      this.newTaskTitle = '';
      this.$els.titleInput.focus();
    }
  }
}
</script>
