<template>
  <NuxtLayout>
    <div class="container">
      <div class="sidebar">
        <p>First project</p>
        <p>Second project</p>
        <p>Third project</p>
      </div>
    </div>
    <div class="content">
      <div class="first_row">
        <template v-for="hour in [...Array(24).keys()]">
          <p class="time" v-for="minutes in ['00', '20', '40']">{{hour.toString().length === 1 ? "0" + hour : hour}}:{{minutes}}</p>
        </template>
      </div>
      <div class="day" v-for="day in tasks">
        <Task v-for="task in day" :task="task.task" :time_start="task.time_start" :time_end="task.time_end" :description="task.description" />
      </div>
    </div>
  </NuxtLayout>
</template>

<script setup lang="ts">

import Task from "~/components/tasks/Task.vue";
import type {TaskPropsI} from "~/components/tasks/Task.vue";

const tasks: Array<TaskPropsI[]> = [
  [
    {
      time_start: "14:40",
      time_end: "16:00",
      title: "First task",
      task: "First task",
      description: "First task description",
    }, {
      time_start: "11:40",
      time_end: "13:00",
      title: "First task",
      task: "First task",
      description: "First task description",
    },
  ], [
    {
      time_start: "14:40",
      time_end: "16:00",
      title: "First task",
      task: "First task",
      description: "First task description",
    }, {
      time_start: "11:40",
      time_end: "13:00",
      title: "First task",
      task: "First task",
      description: "First task description",
    },
  ]
]
</script>

<style scoped>
  .container {
    position: relative;
  }

  .sidebar {
    z-index: 2;
    display: block;
    height: calc(100vh - 30px);
    position: fixed;
    top: 30px;
    background-color: mediumpurple;
    padding: 15px 40px 15px 15px;
    transform: translateX(calc(-100% + 40px));
    transition: .1s ease-out;
    transition-delay: .1s;
  }

  .sidebar:hover {
    transform: translateX(0);
  }

  .content {
    margin-left: 40px;
    width: calc(100vw - 40px);
    display: grid;
    grid-template-columns: auto repeat(7, 1fr);
    gap: 10px;
  }

  .day {
    position: relative;
  }

  .first_row > p {
    line-height: 20px;
  }

  .time {
    position: relative;
  }

  .time::after {
    width: calc(100vw - 100% - 40px);
    height: 1px;
    background-color: rgba(0, 0, 0, .1);
    content: "";
    position: absolute;
    top: 50%;
  }
</style>