<script setup>
const slug = useRoute().params;

const { data: animeDetail, pending, } = await useFetch(`https://web-anime-psi.vercel.app/anime/${slug.anime}`);

console.log(animeDetail);

</script>
<template>
    ini laman anime detail 
    <p>{{ animeDetail.nama }}</p>
    <img :src="animeDetail.gambar" alt="">

</template>