<script setup>
import Main from "./Layouts/Main.vue";
import { Head } from "@inertiajs/inertia-vue3";
import Jumbotron from './Components/Jumbotron.vue';
import Testimonials from './Components/Testimonials.vue';
</script>

<template>
    <Head>
        <title>Beranda</title>
        <meta name="description" content="Beranda" />
    </Head>

    <Main>
        <div class="container pt-10">
            <div class="space-y-10">
                <Jumbotron />
                <Testimonials />
            </div>
        </div>
    </Main>
</template>
