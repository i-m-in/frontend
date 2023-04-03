<template>
  <div>
    <div class="header_line"></div>
    <slot></slot>
  </div>
</template>

<style lang="less">
.header_line {
  display: block;
  content: ' ';
  width: 100vw;
  height: 30px;
  background-color: #4A5CFF;

  margin-bottom: 20px;
}
</style>