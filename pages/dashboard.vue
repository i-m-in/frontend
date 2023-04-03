<template>
  <NuxtLayout>
    <main>
      <meta-card />
      <div class="content">
        <dashboard-group title="This week">
          hello
        </dashboard-group>
      </div>
    </main>
  </NuxtLayout>
</template>

<script>
import MetaCard from "~/components/dashboard/metaCard.vue";
import DashboardGroup from "~/components/dashboard/dashboardGroup.vue";

export default {
  name: "index",
  components: {DashboardGroup, MetaCard}
}
</script>

<style scoped lang="less">
  main {
    width: 1200px;
    margin: 0 auto;
  }
</style>