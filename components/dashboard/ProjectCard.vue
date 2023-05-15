<template>
  <div class="container">
    <div class="avatar">{{short}}</div>
    <div class="info">
      <div class="title">{{title}}</div>
      <div class="meta">
        <div class="description">{{description}}</div>
        <div class="members">
          <img v-for="member in members.slice(0, 5)" :src="member.avatar" :alt="member.name">
        </div>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
  import type {Member} from "~/components/dashboard/EventCard.vue";

  export interface ProjectCardPropsI {
    members: Member[]
    title: string
    description: string
    short: string
    color: string
  }

  const props = defineProps<ProjectCardPropsI>()
</script>

<style scoped>
  .container {
    display: flex;
    gap: 10px;
    align-content: center;
  }

  .avatar {
    width: 3rem;
    height: 3rem;
    border-radius: 8px;
    display: flex;
    justify-content: center;
    align-items: center;
    font-size: 1.5rem;
    background-color: v-bind(color);
  }

  .info {
    display: flex;
    flex-direction: column;
    gap: 5px;
    justify-content: space-between;
  }

  .title {
    font-size: 1.2rem;
    font-weight: bold;
  }

  .meta {
    display: flex;
    gap: 10px;
    align-content: center;
  }

  .members > img {
    width: 1.3rem;
    height: 1.3rem;
    border-radius: 50%;
    border: 2px solid white;
    margin-left: -.2rem
  }
</style>