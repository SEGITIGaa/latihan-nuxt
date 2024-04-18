<script setup>
const { pending, data: completed } = await useLazyFetch('https://web-anime-psi.vercel.app/anime?type=complete');
</script>
<template>
    <div class="w-full items-center justify-between flex">
        <h1 class="h1">Completed</h1>
        <NuxtLink to="/" class="arrow-btn">more</NuxtLink>
    </div>

    <div v-if="completed" class="carousel">
        <NuxtLink :to="`/anime/${anime.slug}`" v-for="anime in completed" :key="anime.id" class="card">
            <img :src="anime.gambar" :alt="anime.judul" class="card-img" />
            <div class="flex flex-col gap-2 items-center w-56">
                <p class="text-second font-semibold break-words w-52 truncate text-center text-lg">
                    {{ anime.judul }}
                </p>
                <p class="text-second break-words truncate text-center text-xs">
                    {{ anime.eps[0] }} episode
                </p>
            </div>
        </NuxtLink>
    </div>

    <div v-if="pending" class="">
        <p>bentar mas...</p>
    </div>
</template>