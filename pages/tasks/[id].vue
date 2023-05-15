<template>
  <NuxtLayout>
    <main>
      <div class="sidebar_left">
        <div class="project">
          <div class="project_info">
            <p class="created_date">Created: 10.05.2023</p>
            <p class="project_name">Cool course project</p>
          </div>
          <div class="project_members">
            <div class="members_avatars">
              <img v-for="member in members.slice(0, 5)" :src="member.avatar" :alt="member.name">
            </div>
            <div class="members">
              <p class="members_names">{{members.slice(0, 3).map(member => member.name.split(" ")[0]).join(", ")}}</p>
              <p class="members_plus">+{{members.length - 3}}</p>
            </div>
          </div>
        </div>
      </div>
      <div class="content">
        <MdEditor v-model="text" v-if="isEditable" language="en-US" class="editor" :preview="false" :preview-only="false"/>
        <MdEditor v-model="text" v-else language="en-US" class="editor" :preview="true" :preview-only="true"/>
        <button class="edit" v-on:click="handleEdit">
          {{isEditable ? "Save" : "Edit"}}
        </button>
      </div>
      <div class="sidebar_right">
        <p class="information">Information</p>
        <div class="information_inner">
          <label for="title">Title:</label>
          <input type="text" name="title">
          <label for="date_start">Start:</label>
          <input type="datetime-local" name="date_start">
          <label for="date_start">End:</label>
          <input type="datetime-local" name="date_start">
        </div>
        <div class="member_info" v-if="members.length">
          <p class="sidebar_members">Members</p>
          <div class="sidebar_members_inner">
            <div class="sidebar_member" v-for="member in members.slice(0, 6)">
              <img class="members_avatar" :src="member.avatar">
              <p class="member_name">{{member.name}}</p>
            </div>
          </div>
        </div>
        <p class="files">Attached files</p>
        
      </div>
    </main>
  </NuxtLayout>
</template>

<script setup lang="ts">
import { ref } from 'vue';
import MdEditor from 'md-editor-v3';
import 'md-editor-v3/lib/style.css';

const text = ref<string>('# hello world');
const isEditable = ref<boolean>(false)

const handleEdit = () => {
  text.value = !text.value ? "# Hello world" : text.value

  isEditable.value = !isEditable.value
}

import type {Member} from "~/components/dashboard/EventCard.vue";

const route = useRoute()
const taskId = route.params.id

const members: Member[] = [
  {
    avatar: "https://i.postimg.cc/MpWg57Qz/2023-04-28-12-31-1.png",
    name: "Руслан Мельник"
  },
  {
    avatar: "https://i.postimg.cc/MpWg57Qz/2023-04-28-12-31-1.png",
    name: "Шамиль Хайрутдинов"
  },
  {
    avatar: "https://i.postimg.cc/MpWg57Qz/2023-04-28-12-31-1.png",
    name: "Дима Матвеев"
  },
  {
    avatar: "https://i.postimg.cc/MpWg57Qz/2023-04-28-12-31-1.png",
    name: "Сергей Павлов"
  },
  {
    avatar: "https://i.postimg.cc/MpWg57Qz/2023-04-28-12-31-1.png",
    name: "Артемий Лебедев"
  }
]

</script>

<style scoped>
  main {
    margin: 0 20px;
    display: grid;
    grid-template-columns: 1fr 3fr 1fr;
    gap: 15px;
    height: calc(100vh - 60px)
  }

  .project {
    background-color: royalblue;
    color: white;
    padding: 15px;
    border-radius: 10px;
    height: 30vh;
    display: flex;
    flex-direction: column;
    justify-content: space-between;
  }

  .created_date {
    color: #f2f2f2;
  }

  .project_name {
    font-size: 1.3rem;
    font-weight: 600;
    margin-top: 10px;
  }

  .members_avatars > img {
    height: 2rem;
    border-radius: 50%;
    border: 1px solid #f1f1f1;
  }

  .members_avatars > img:not(:first-child) {
    margin-left: -5px;
  }

  .members {
    display: flex;
    align-items: center;
  }

  .members_names {
    overflow: hidden;
    text-overflow: ellipsis;
    white-space: nowrap;
    width: 60%;
    font-size: 1rem;
    margin-top: 5px;

  }

  .members_plus {
    font-size: .6rem;
    border-radius: 6px;
    background-color: rgba(200, 200, 200, .4);
    padding: 4px;
  }

  .editor {
    border-radius: 15px;
  }

  .edit {
    all: unset;
    cursor: pointer;
    background-color: #4A5CFF;
    color: #fefefe;
    border-radius: 5px;
    margin-top: 10px;
    padding: 5px 15px;
  }

  .sidebar_right {
    background-color: #fefefe;
    border-radius: 15px;
    height: 100%;
    padding: 15px;
  }

  .sidebar_right > p, .sidebar_members  {
    font-size: 1.3em;
    color: #5252ff;
  }


  .information_inner {
    margin-top: 10px;
    display: grid;
    grid-template-columns: 3fr 5fr;
    margin-bottom: 15px;
  }

  .information_inner > input{
    margin-bottom: 10px;
    padding: 2px 7px;
  }

  .information_inner > label {
    color: #888;
  }

  .sidebar_member {
    display: flex;
    margin-top: 5px;
    gap: 5px;
  }

  .members_avatar {
    height: 2.5em;
    border-radius: 50%;
  }
</style>