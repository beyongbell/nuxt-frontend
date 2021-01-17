<template>
    <div class="container">
        <h2> Letest Topics </h2>
        <pre>
            {{ topics }}
        </pre>
    </div>
</template>

<script>
export default {
    data() {
        return {
            topics: []
        }
    },
    async asyncData({ $axios }) {
        let {data} = await $axios.$get('/topics');
        return { topics : data }
    }
}
</script>

<style>

</style>