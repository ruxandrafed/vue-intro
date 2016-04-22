<template>
  <div>
    <h1>Todo ({{counter}})</h1>
  </div>
</template>

<script>
export default {
  data () {
    return {
      tasks: []
    }
  },
  computed: {
    counter: function () {
      return this.tasks.filter(function (task) {
        return !task.completed
      }).length
    }
  }
}
</script>
