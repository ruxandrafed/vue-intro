<template>
  <div>
    <h1>Todo ({{counter}}/{{total}})</h1>
    <task-creator v-on:new-task="addNewTask"></task-creator>
    <task-list v-bind:tasks.sync="tasks"></task-list>
    <!-- <pre>
      {{tasks | json}}
    </pre> -->
  </div>
</template>

<script>
import TaskCreator from './TaskCreator';
import TaskList from './TaskList';
import { Task } from './Task';

export default {
  data () {
    return {
      tasks: []
    };
  },
  components: {
    TaskCreator,
    TaskList
  },
  computed: {
    counter () {
      return this.tasks.filter(function (task) {
        return !task.isCompleted
      }).length;
    },
    total () {
      return this.tasks.length;
    }
  },
  methods: {
    addNewTask (title) {
      this.tasks.push(new Task(title));
    }
  }
}
</script>
