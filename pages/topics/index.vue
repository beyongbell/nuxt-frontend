<template>
    <div class="container">
        <h2> Letest Topics </h2>
        <div v-for="(topic, index) in topics" :key="index" class="bg-light my-5 p-4">
            <h2>{{ topic.title }}</h2>
            <p class="text-muted"> {{ topic.created_at }} by {{ topic.user.name }} </p>
            <div v-for="(content, index) in topic.posts" :key="index" class="ms-5 content p-3">
                {{ content.body }}
                <p class="text-muted"> {{ content.created_at }} by {{ content.user.name }} </p>
            </div>
        </div>
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
    .content {
        border-left: 10px solid white;
    }
</style>