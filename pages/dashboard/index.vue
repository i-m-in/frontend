<template>
  <NuxtLayout>
    <main>
      <div class="account_info">
        <AccountInfo :name="account.name" :url="account.avatar" />
      </div>
      <div class="this_week">
        <h2>This week</h2>
        <div class="week_events">
          <EventCard :rawDate="event.rawDate" :event="event.event" v-for="event in Events" />
        </div>
      </div>
      <section>
        <div class="tasks">
          <h2>Tasks</h2>
          <div class="task_list">
            <TaskCard v-for="task in tasks" :project="task.project" :title="task.title" :avatar="task.avatar" />
          </div>
        </div>
        <div class="projects">
          <h2>Projects</h2>
          <div class="project_list">
            <ProjectCard v-for="project in Projects" :members="project.members" :title="project.title" :description="project.description" :short="project.short" :color="project.color" />
          </div>
        </div>
      </section>
    </main>
  </NuxtLayout>
</template>

<script setup lang="ts">

import AccountInfo from "~/components/dashboard/AccountInfo.vue";
import EventCard from "~/components/dashboard/EventCard.vue";
import type {EventCardPropsI} from "~/components/dashboard/EventCard.vue";
import type {TaskCardPropsI} from "~/components/dashboard/TaskCard.vue";
import type {ProjectCardPropsI} from "~/components/dashboard/ProjectCard.vue";
import TaskCard from "~/components/dashboard/TaskCard.vue";
import ProjectCard from "~/components/dashboard/ProjectCard.vue";

const account = {
  name: "Руслан Мельник",
  avatar: "https://i.postimg.cc/MpWg57Qz/2023-04-28-12-31-1.png"
}

const Events: EventCardPropsI[] = [
  {
    rawDate: "August 19, 1975 00:00:00",
    event: {
      title: "Meet with friends",
      members: [
        {
          avatar: "https://i.postimg.cc/MpWg57Qz/2023-04-28-12-31-1.png",
          name: "Руслан Мельник"
        },
        {
          avatar: "https://i.postimg.cc/MpWg57Qz/2023-04-28-12-31-1.png",
          name: "Шамиль Хайрутдинов"
        }
      ],
      timeStart: "August 19, 1975 12:00:00",
      timeEnd: "August 19, 1975 15:00:00",
    }
  }, {
    rawDate: "August 19, 1975 00:00:00",
    event: {
      title: "I\'m in backend meeting",
      members: [
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
      ],
      timeStart: "August 19, 1975 13:40:00",
      timeEnd: "August 19, 1975 15:00:00",
    }
  },{
    rawDate: "August 19, 1975 00:00:00",
    event: {
      title: "I\'m in backend meeting",
      members: [
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
      ],
      timeStart: "August 19, 1975 12:00:00",
      timeEnd: "August 19, 1975 13:00:00",
    }
  }
]

const Projects: ProjectCardPropsI[] = [
  {
    members: [
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
    ],
    title: "Course project",
    color: "#db48ff",
    description: "Cool course project",
    short: "CP"
  },
  {
    members: [
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
    ],
    title: "Course project",
    color: "#db48ff",
    description: "Cool course project",
    short: "CP"
  },
  {
    members: [
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
    ],
    title: "Course project",
    color: "#db48ff",
    description: "Cool course project",
    short: "CP"
  },
  {
    members: [
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
    ],
    title: "Course project",
    color: "#db48ff",
    description: "Cool course project",
    short: "CP"
  },
]

const tasks: TaskCardPropsI[] = [
  {title: "Make UI for course project", project: {avatar: "https://i.postimg.cc/MpWg57Qz/2023-04-28-12-31-1.png", name: "Course project", color: "#db48ff"}},
  {title: "Make UI for course project", project: {avatar: "https://i.postimg.cc/MpWg57Qz/2023-04-28-12-31-1.png", name: "Course project", color: "#63c3ff"}},
  {title: "Make UI for course project", project: {avatar: "https://i.postimg.cc/MpWg57Qz/2023-04-28-12-31-1.png", name: "Course project", color: "#db48ff"}},
]

console.log(await $fetch("http://localhost:8080/tasks/1", {
  method: "GET",
}))

</script>

<style scoped lang="less">
  main {
    width: 1200px;
    margin: 0 auto;
  }

  .week_events {
    display: grid;
    grid-template-columns: 1fr 1fr 1fr;
    gap: 10px;
    background-color: #dac1f3;
    padding: 10px;
    border-radius: 10px;
  }

  section {
    display: grid;
    grid-template-columns: 5fr 4fr;
    gap: 2rem;
  }

  .task_list, .project_list {
    background-color: #dac1f3;
    padding: 10px;
    border-radius: 10px;
    display: flex;
    flex-direction: column;
    gap: 10px;
  }


</style>