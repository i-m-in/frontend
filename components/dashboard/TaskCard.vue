<template>
  <div class="container">
    <div class="info">
      <p class="project">{{project.name}}</p>
      <p class="title">{{title}}</p>
    </div>
    <div class="avatar">
      <img :src="project.avatar" :alt="title">
    </div>
  </div>
</template>

<script setup lang="ts">

interface ProjectI {
  avatar: string
  name: string
  color: string
}

export interface TaskCardPropsI {
  title: string
  project: ProjectI

}

const props = defineProps<TaskCardPropsI>()
</script>

<style scoped>
  .container {
    display: flex;
    flex-direction: row;
    align-items: center;
    justify-content: space-between;
    background-color: v-bind('project.color');
    padding: 10px;
    border-radius: 8px;
    color: #fefefe;
  }

  .project {
    font-weight: bold;
  }

  .title {
    font-size: 1.2rem;
  }

  .avatar>img {
    height: 3rem;
    width: 3rem;
    border-radius: 50%;
  }
</style>