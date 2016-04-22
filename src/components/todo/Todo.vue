<template>
  <div>
    <h1>Todo ({{counter}})</h1>
    <task-creator v-on:new-task="addNewTask"></task-creator>

    <!-- <pre>
      {{tasks | json}}
    </pre> -->
  </div>
</template>

<script>
import TaskCreator from './TaskCreator';
import { Task } from './Task';

export default {
  data () {
    return {
      tasks: []
    };
  },
  components: {
    TaskCreator
  },
  computed: {
    counter () {
      return this.tasks.filter(function (task) {
        return !task.isCompleted
      }).length;
    }
  },
  methods: {
    addNewTask (title) {
      this.tasks.push(new Task(title));
    }
  }
}
</script>
