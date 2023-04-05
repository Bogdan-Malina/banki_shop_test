<template lang="pug">
.container.main
  h1.text-start.ms-3 Картины эпохи возрождения
  .col-12.row.m-0
    .col-12.col-lg-6.col-xl-4.col-xxl-3.p-3(v-for="painting in content" :id="`card-content${painting.id}`")
      CardContent(:painting="painting")
</template>

<script>
import CardContent from "@/components/CardContent";
export default {
  components: {
    CardContent
  },
  props: {
    content: Array
  },
}
</script>

<style scoped>
.main {
  min-height: 80vh;
}
</style>
