<script setup>
import Navbar from "./../Partials/Navbar.vue";
</script>

<template>
    
    <main class="min-h-screen" data-theme="fantasy">
        <Navbar />
        <div class="flex justify-center items-center mx-auto">
            <slot />
        </div>
    </main>
</template>