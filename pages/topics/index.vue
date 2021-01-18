<template>
    <div class="container">
        <h2> Letest Topics </h2>
        <div v-for="(topic, index) in topics" :key="index" class="bg-light my-5 p-4">
            <h2> <nuxt-link :to="{name: 'topics-id', params: { id: topic.id }}"> {{ topic.title }} </nuxt-link></h2>
            <div v-if="authenticated">
              <div v-if="user.id === topic.user.id">
                <nuxt-link :to="{name: 'topics-edit', params: { id: topic.id }}">
                  <button class="btn btn-warning fa fa-edit float-end"></button>
                </nuxt-link>
                <button @click="deleteTopic(topic.id)" class="btn btn-danger fa fa-trash float-end mx-2"></button>
              </div>
            </div>
            <p class="text-muted"> {{ topic.created_at }} by {{ topic.user.name }} </p>
            <div v-for="(content, index) in topic.posts" :key="index" class="ms-5 content p-3">
                {{ content.body }}
                <p class="text-muted"> {{ content.created_at }} by {{ content.user.name }} </p>
            </div>
        </div>

        <nav aria-label="Page navigation">
        <ul class="pagination justify-content-center">
            <li v-for="(link, item) in links" :key="item"  class="page-item">
                <a @click="loadMore(link)" class="page-link" href="#">{{ item }}</a>
            </li>
        </ul>
        </nav>
    </div>
</template>

<script>
export default {
  data() {
    return {
      topics: [],
      links: [],
    };
  },
  async asyncData({ $axios }) {
    let { data, links } = await $axios.$get("/topics");
    return { topics: data, links };
  },
  methods: {
      async loadMore(link) {
        let { data } = await this.$axios.$get(link);
        return this.topics = { ...this.topics, ...data }
      },
      async deleteTopic(id) {
        await this.$axios.$delete(`/topics/${id}`)
        this.$router.push('/')
      }
  }
};
</script>

<style>
.content {
  border-left: 10px solid white;
}
</style>