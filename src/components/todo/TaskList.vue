<template>
  <ul class="tasks">
    <li
        class="task"
        v-bind:class="{'complated': task.isCompleted}"
        v-for="task in tasks"
        v-on:click="task.isCompleted = !task.isCompleted"
    >
      <span>{{ task.title }}</span> <strong v-on:click="deleteTask(task)">X</strong>
    </li>
  </ul>
</template>
<script>
export default {
  props: ['tasks'],
  methods: {
    deleteTask (task) {
      this.tasks.$remove(task)
    }
  }
}
</script>
<style>
.tasks {
    list-style-type: none;
    text-align: left;
}
.task {
    cursor: pointer;
    padding: 5px 0;
}
.task.complated > span {
  text-decoration: line-through;
}
</style>
