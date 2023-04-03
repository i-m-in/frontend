<template>
  <div class="container">
    <img src="https://yt3.ggpht.com/2ymA_X0qpfSs8jULiEmI4zGTu6niU4z3rhKAmlpHCnsZf6oUp9y1yESm2t-ylQBlPlRSDR3T_HI=s900-c-k-c0x00ffffff-no-rj" alt="">
    <div class="meta">
      <div class="name">Сергей Павлов</div>
      <div class="status">Online</div>
    </div>
  </div>
</template>

<script>
export default {
  name: "metaCard"
}
</script>

<style scoped lang="less">
  .container {
    display: flex;
    gap: 1em;

    img {
      height: 3rem;
      width: 3rem;
      border-radius: 50%;
    }

    .meta {
      .name {
        font-size: 1.5em;
      }

      .status {
        display: flex;
        gap: .3em;
        align-items: center;

        &:before {
          display: inline-block;
          height: .4em;
          width: .4em;
          content: ' ';
          background-color: lime;
          border-radius: 50%;
        }
      }
    }
  }
</style>