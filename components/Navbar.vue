<template>
    <nav class="navbar navbar-expand-lg navbar-light bg-light">
        <div class="container-fluid">
            <nuxt-link to="/" class="navbar-brand"> Frontend </nuxt-link>
            <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarNav" aria-controls="navbarNav" aria-expanded="false" aria-label="Toggle navigation">
            <span class="navbar-toggler-icon"></span>
            </button>
            <div class="collapse navbar-collapse" id="navbarNav">
            <ul class="navbar-nav me-auto">
                <li class="nav-item">
                    <nuxt-link to="/" class="nav-link"> Home </nuxt-link>
                </li>
                <li class="nav-item">
                    <nuxt-link to="/" class="nav-link"> Posts </nuxt-link>
                </li>
            </ul>
             <ul class="navbar-nav">
                <li class="nav-item">
                    <nuxt-link to="/login" class="nav-link"> Login </nuxt-link>
                </li>
                <li class="nav-item">
                    <nuxt-link to="/register" class="nav-link"> Register </nuxt-link>
                </li>
            </ul>
            </div>
        </div>
    </nav>
</template>