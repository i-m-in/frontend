<template>
    <div class="task" draggable="true" ref="el" v-on:drag="handleDrag" v-on:dragleave="handleDragEnd">
      <p>{{task}}</p>
      <p>{{timeStart}}-{{timeEnd}}</p>
    </div>
</template>

<script setup lang="ts">
  import { useResizeObserver } from '@vueuse/core'

  export interface TaskPropsI {
    time_start: string
    time_end: string
    task: string
    description: string
  }

  const minsToTime = (mins: number) => {
    const hours = Math.floor(mins / 60)
    const minutes = mins % 60
    return `${hours}:${minutes.toString().padStart(2, "0")}`
  }

  let props = defineProps<TaskPropsI>()

  const el = ref<HTMLElement | null>(null)
  let timeEnd = ref<string>(props.time_end)
  let timeStart = ref<string>(props.time_start)

  useResizeObserver(el, (entries) => {
    const entry = entries[0]
    const {height} = entry.contentRect
    timeEnd.value = minsToTime(Number(timeStart.value.split(":")[0]) * 60 + Number(timeStart.value.split(":")[1]) + height + 20)
  })

  const handleDragEnd = (e: DragEvent) => {
    console.log(e.pageY)
  }

  const handleDrag = (e: DragEvent) => {
    const top = e.pageY - 80

    el.value.style.top = top + "px"

    timeEnd.value = minsToTime(Number(timeStart.value.split(":")[0]) * 60 + Number(timeStart.value.split(":")[1]) + Number(el.value.style.height.slice(0, -2) ) + 80)
    timeStart.value = minsToTime(top - 10)
  }

  function getRandomColor() {
    var letters = '0123456789ABCDEF';
    var color = '#';
    for (var i = 0; i < 6; i++) {
      color += letters[Math.floor(Math.random() * 16)];
    }
    return color;
  }

  const color = getRandomColor()


  const top = ref<string | null>(null)
  top.value = Number(timeStart.value.split(":")[0]) * 60 + Number(timeStart.value.split(":")[1]) + 10  + "px"

  const height = ref<string | null>(null)
  const [hourStart, minuteStart, hourEnd , minuteEnd] = [...timeStart.value.split(":"), ...props.time_end.split(":")].map(Number)
  if (minuteEnd < minuteStart) {
    height.value = (hourEnd - hourStart - 1) * 60 + (60 - minuteStart + minuteEnd) + "px"
  } else {
    height.value = (hourEnd - hourStart) * 60 + (minuteEnd - minuteStart) + "px"
  }
</script>

<style scoped>
.task {
  width: 100%;
  position: absolute;
  display: inline-block;
  padding: 10px;
  background-color: v-bind('color');
  resize: vertical;
  overflow: auto;
  border-radius: 5px;
  top: v-bind('top');
  height: v-bind('height');
}
</style>