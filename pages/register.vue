<template>
    <div class="container col-md-6 mt-5">
        <h2 class="text-center"> Register </h2>
        <br>
        <form>
            <div class="mb-3">
                <label for="fullName" class="form-label">Full Name</label>
                <input type="text" class="form-control">
                <small class="form-text text-danger"> Show error message!</small>
            </div>
            <div class="mb-3">
                <label for="email" class="form-label">Email address</label>
                <input type="email" class="form-control">
                <small class="form-text text-danger"> Show error message!</small>
            </div>
            <div class="mb-3">
                <label for="password" class="form-label">Password</label>
                <input type="password" class="form-control">
                <small class="form-text text-danger"> Show error message!</small>
            </div>
            <button type="submit" class="btn btn-primary">Register</button>
        </form>
    </div>
</template>

<script>
export default {};
</script>

<style>
</style>