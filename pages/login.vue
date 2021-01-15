<template>
    <div class="container col-md-6 mt-5">
        <h2 class="text-center"> Login </h2>
        <br>
        <form @submit.prevent="submit">
            <div class="mb-3">
                <label for="email" class="form-label">Email address</label>
                <input v-model.trim="form.email" type="email" class="form-control" autofocus>
                <small class="form-text text-danger" v-if="errors.email"> {{ errors.email[0] }}</small>
            </div>
            <div class="mb-3">
                <label for="password" class="form-label">Password</label>
                <input v-model.trim="form.password" type="password" class="form-control">
                <small class="form-text text-danger" v-if="errors.password"> {{ errors.password[0] }}</small>
            </div>
            <button type="submit" class="btn btn-primary">Login</button>
        </form>
        <br>
        <p> Don't have an account? <nuxt-link to="/register"> Register </nuxt-link></p>
    </div>
</template>

<script>
export default {
    data() {
        return {
            form: {
                email: '',
                password: ''
            }
        }
    },
    methods: {
        async submit() {
            try {
                await this.$auth.loginWith('local', { data: this.form })
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