<template>
   <div class="container">
        <div class="bg-light my-5 p-4">
            <h2 class="display-3"> {{ topic.title }} </h2>
            <p class="text-muted"> {{ topic.created_at }} by {{ topic.user.name }} </p>
            <div v-for="(content, index) in topic.posts" :key="index" class="ms-5 content p-3">
                <p> {{ content.body }} </p> 
                <div v-if="authenticated">
                    <div v-if="user.id === content.user.id">
                        <button @click="deletePost(content.id)" class="btn btn-danger fa fa-trash float-end mx-2"></button>
                        <nuxt-link :to="{name: 'topics-posts-edit', params: { id: content.id }}">
                            <button class="btn btn-warning fa fa-edit float-end"></button>
                        </nuxt-link>
                    </div>
                </div>
                <p class="text-muted"> {{ content.created_at }} by {{ content.user.name }} </p>
            </div>
        </div>
        <div class="my5 mx5" v-if="authenticated">
            <form @submit.prevent="create">
                <div class="form-group">
                    <label for="post" class="my-2">  <h4>  Add a new Post  </h4></label>
                    <textarea v-model="body" rows="5" placeholder="Write something" class="form-control"></textarea>
                    <small class="form-text text-danger" v-if="errors.body"> {{ errors.body[0] }}</small>
                </div>
                <button class="btn btn-outline-primary mt-3">Add a new Post</button>
            </form>
        </div>
    </div>
</template>

<script>
export default {
    data() {
        return {
            topic: '',
            body: ''
        }
    },
    async asyncData({$axios, params}) {
        const {data} = await $axios.$get(`/topics/${params.id}`);
        return { topic : data }
    },
    methods: {
        async create() {
            await this.$axios.$post(`/topics/${this.$route.params.id}/posts`, { body : this.body })
            this.$router.push('/topics')
        },
        async deletePost(id) {
            await this.$axios.$delete(`/topics/${this.$route.params.id}/posts/${id}`)
            this.$router.push('/')
        }
    }
}
</script>

<style>

</style>