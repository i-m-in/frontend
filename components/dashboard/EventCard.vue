<template>
  <div class="container">
    <div class="event_date">
      <div class="event_date_inner">
        <p class="date">{{date}}</p>
        <p class="weekday">{{weekday}}</p>
      </div>
      <div class="event_info">
        <div class="event_inner">
          <p class="event_title">{{props.event.title}}</p>
          <div class="members">
            <div class="members_avatars">
              <img :src="member.avatar" :alt="member.name" v-for="member in props.event.members.slice(0, 5)">
            </div>
            <div class="members_info">{{props.event.members.map(member => member.name.split(" ")[0]).join(", ")}}</div>
          </div>
        </div>
        <div class="event_time">
          <div class="time_period">
            <p class="time_start">{{timeStart.toLocaleTimeString("en-US", {hour: "2-digit", minute: "2-digit"})}}</p>
            -
            <p class="time_end">{{timeEnd.toLocaleTimeString("en-US", {hour: "2-digit", minute: "2-digit"})}}</p>
          </div>
          <div class="duration">{{duration}}</div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">

  export interface Member {
    avatar: string
    name: string
  }

  interface Event {
    title: string
    members: Member[]
    timeStart: string
    timeEnd: string
  }

  export interface EventCardPropsI {
    rawDate: string
    event: Event
  }

  const props = defineProps<EventCardPropsI>()

  const date = new Date(props.rawDate).toLocaleDateString("en-US", {month: 'long', day: 'numeric'})
  const weekday = new Date(props.rawDate).toLocaleDateString("en-US", {weekday: "long"})

  const timeStart = new Date(props.event.timeStart)
  const timeEnd = new Date(props.event.timeEnd)
  const duration = (timeEnd.getTime() - timeStart.getTime()) / 1000 / 60 < 120 ? `${(timeEnd.getTime() - timeStart.getTime()) / 1000 / 60} minutes` : `${(timeEnd.getTime() - timeStart.getTime()) / 1000 / 60 / 60} hours`
</script>

<style scoped lang="less">
  .container {
    background-color: #fefefe;
    border-radius: 7px;
    height: 100%;
    padding: 10px;
  }

  .event_date {
    height: 100%;
    display: grid;
    grid-template-rows: auto 1fr;
  }

  .date {
    font-weight: 600;
  }

  .event_info {
    color: #fefefe;
    background-color: #4A5CFF;
    padding: 10px;
    border-radius: 5px;
    margin-top: 10px;
    display: flex;
    flex-direction: column;
    justify-content: space-between;
  }

  .event_inner {
    display: flex;
    justify-content: space-between;
  }

  .event_title {
    font-size: 1.6rem;
    font-weight: bold;
  }

  .members {
    max-width: 8rem;

    .members_avatars {
      display: flex;
      justify-content: flex-end;

      img {
        height: 2rem;
        border-radius: 50%;
        border: 2px solid #f2f2f2;

        &:not(:first-child) {
          margin-left: -0.5rem;
        }
      }
    }

    .members_info {
      overflow: hidden;
      text-overflow: ellipsis;
      white-space: nowrap;
      width: 100%;
      font-size: .8rem;
      text-align: right;
      margin-top: 5px;
    }
  }

  .event_time {
    align-items: center;
    display: flex;
    justify-content: space-between;
    margin-top: 10px;
  }

  .time_period {
    display: flex;
    gap: 8px;
  }

  .duration {
    padding: 5px 10px;
    border-radius: 5px;
    background-color: rgba(255, 255, 255, .2);
  }
</style>