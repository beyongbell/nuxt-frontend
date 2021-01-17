<template>
  <div class="container">
      <h2> Single Topic Page </h2>
      <pre>
          {{ topic }}
      </pre>
  </div>
</template>

<script>
export default {
    data() {
        return {
            topic: ''
        }
    },
    async asyncData({$axios, params}) {
        const {data} = await $axios.$get(`/topics/${params.id}`);
        return { topic : data }
    }
}
</script>

<style>

</style>