<template>
    <div class="container col-md-6 mt-5">
        <h2 class="text-center"> Register </h2>
        <br>
        <form @submit.prevent="submit">
            <div class="mb-3">
                <label for="fullName" class="form-label">Full Name</label>
                <input v-model.trim="form.name" type="text" class="form-control" autofocus>
                <small class="form-text text-danger" v-if="errors.name"> {{ errors.name[0] }}</small>
            </div>
             <div class="mb-3">
                <label for="email" class="form-label">Email address</label>
                <input v-model.trim="form.email" type="email" class="form-control">
                <small class="form-text text-danger" v-if="errors.email"> {{ errors.email[0] }}</small>
            </div>
            <div class="mb-3">
                <label for="password" class="form-label">Password</label>
                <input v-model.trim="form.password" type="password" class="form-control">
                <small class="form-text text-danger" v-if="errors.password"> {{ errors.password[0] }}</small>
            </div>
            <button type="submit" class="btn btn-primary">Register</button>
        </form>
        <br>
        <p> Already have an account? <nuxt-link to="/login"> Login </nuxt-link></p>
    </div>
</template>

<script>
export default {
    middleware: ['guest'],
    data() {
        return {
            form: {
                name: '',
                email: '',
                password: ''
            }
        }
    },
    methods: {
        async submit() {
            try {
                await this.$axios.$post('register', this.form)
                await this.$auth.loginWith('local', {
                    data: {
                        email : this.form.email,
                        password: this.form.password
                    }
                })
                this.$router.push({
                    path: this.$route.query.redirect || '/dashboard'
                })
            } catch (e) {
                return;
            }
        }
    }
};
</script>

<style>
</style>