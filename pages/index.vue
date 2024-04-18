<script setup>
const baseUrl = 'https://web-anime-psi.vercel.app';


const { data: completed } = await useFetch(`${baseUrl}/anime?type=complete`);
const { data: ongoing } = await useFetch(`${baseUrl}/anime?type=ongoing`);
const { data: genres } = await useFetch(`${baseUrl}/genre`)

const layout = 'main';


</script>

<template>
    <NuxtLayout :name="layout">

        <div class="w-full items-center justify-between flex">
            <h1 class="h1">Ongoing</h1>
            <NuxtLink to="/" class="arrow-btn">more</NuxtLink>
        </div>

        <div v-if="ongoing" class="carousel mb-10">
            <NuxtLink :to="`/anime/${anime.slug}`" v-for="anime in ongoing" :key="anime.id" class="card">
                <img :src="anime.gambar" :alt="anime.judul" class="card-img" />
                <div class="flex flex-col gap-2 items-center w-56">
                    <p class="text-second font-semibold break-words w-52 truncate text-center text-lg">
                        {{ anime.judul }}
                    </p>
                    <p class="text-second break-words truncate text-center text-xs">
                        {{ anime.eps[1] }} episode
                    </p>
                </div>
            </NuxtLink>
        </div>

        <div class="carousel gap-2 mb-5" v-if="genres">
            <NuxtLink to="/" v-for="genre in genres" :key="genre.slug" class="genre">
                {{ genre.judul }}
            </NuxtLink>
        </div>

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
        <div v-else>
            Loading...
        </div>


    </NuxtLayout>
</template>