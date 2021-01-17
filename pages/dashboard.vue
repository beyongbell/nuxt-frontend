<template>
    <div class="container col-md-6 mt-5">
        <h2 class="text-center"> Create a new Topic </h2>
        <br>
        <form @submit.prevent="submit">
            <div class="mb-3">
                <label for="email" class="form-label"> <strong> Topic Title: </strong> </label>
                <input v-model="form.title" type="text" class="form-control" autofocus>
                <small class="form-text text-danger" v-if="errors.title"> {{ errors.title[0] }}</small>
            </div>
            <div class="mb-3">
              <label for="email" class="form-label"> <strong> Topic Body: </strong> </label>
              <textarea v-model="form.body" class="form-control" rows="5"></textarea>
              <small class="form-text text-danger" v-if="errors.body"> {{ errors.body[0] }}</small>
            </div>
            <button type="submit" class="btn btn-primary">Create</button>
        </form>
    </div>
</template>

<script>
export default {
   middleware: ['auth'],
   data() {
     return {
       form : {
         title: '',
         body: ''
       }
     }
   },
   methods: {
     async submit() {
        try {
          await this.$axios.$post('/topics', this.form)
          this.$router.push('/')
        } catch (e) {
          return;
        }
     }
   }
};
</script>

<style>
</style>