<script setup>

const { pending, data: genres } = await useLazyFetch('https://web-anime-psi.vercel.app/genre')

const layout = 'main';

</script>

<template>
    <NuxtLayout :name="layout">

        <Ongoing />

        <div class="carousel gap-2 mb-5" v-if="genres">
            <NuxtLink to="/" v-for="genre in genres" :key="genre.slug" class="genre">
                {{ genre.judul }}
            </NuxtLink>
        </div>

        <div v-if="pending" class="">
            <p>bentar mas...</p>
        </div>

        <Complete />

    </NuxtLayout>
</template>