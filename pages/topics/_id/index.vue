<template>
   <div class="container">
        <h2> Single Topic Page </h2>
        <div class="bg-light my-5 p-4">
            <h2 class="display-3"> {{ topic.title }} </h2>
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