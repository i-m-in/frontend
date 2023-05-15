<template>
  <div>
    <div class="header_line"></div>
    <slot></slot>
  </div>
</template>

<style lang="less">
.header_line {
  position: sticky;
  top: 0;
  z-index: 4;
  display: block;
  content: ' ';
  width: 100vw;
  height: 30px;
  background-color: #4A5CFF;

  margin-bottom: 20px;
}
</style>