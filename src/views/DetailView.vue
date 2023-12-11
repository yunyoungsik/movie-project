<template>
    <HeaderSection />
    <DetailIntro v-if="movieBasic && movieCredits" :movieBasic="movieBasic" :movieCredits="movieCredits" />
    <DetailInfo v-if="movieInfo" :movieInfo="movieInfo" />
    <DetailVideos v-if="movieVideos" :movieVideos="movieVideos" />
    <DetailImg v-if="movieImg" :movieImg="movieImg" />
    <DetailCredits v-if="movieCredits" :movieCredits="movieCredits" />
    <FooterSection />
</template>

<script>
import { onMounted, ref } from "vue";
import { useRoute } from "vue-router";
import axios from 'axios';

import HeaderSection from "../components/section/HeaderSection.vue";
import FooterSection from "../components/section/FooterSection.vue";
import DetailIntro from "../components/detail/DetailIntro.vue";
import DetailInfo from "../components/detail/DetailInfo.vue";
import DetailImg from "../components/detail/DetailImg.vue";
import DetailCredits from "../components/detail/DetailCredits.vue";
import DetailVideos from "../components/detail/DetailVideos.vue";

export default {
    name: "MovieDetailPage",
    components: {
        HeaderSection,
        FooterSection,
        DetailIntro,
        DetailInfo,
        DetailVideos,
        DetailImg,
        DetailCredits,
    },

    setup() {
        const movieBasic = ref(null);
        const movieInfo = ref(null);
        const movieImg = ref(null);
        const movieCredits = ref(null);
        const movieVideos = ref(null);

        const route = useRoute();


        onMounted(async () => {
            const movieId = route.params.movieId;
            const apiKey = import.meta.env.VITE_API_KEY;
            const language = "ko-KR";
            try {
                const resMovieBasic = await axios.get(`https://api.themoviedb.org/3/movie/${movieId}?language=${language}&api_key=${apiKey}`);
                movieBasic.value = resMovieBasic.data;
                // console.log(movieBasic)

                const resMovieInfo = await axios.get(`https://api.themoviedb.org/3/movie/${movieId}?language=${language}&api_key=${apiKey}`);
                movieInfo.value = resMovieInfo.data;
                // console.log(resMovieInfo);

                const resmovieImg = await axios.get(`https://api.themoviedb.org/3/movie/${movieId}/images?api_key=${apiKey}`);
                movieImg.value = resmovieImg.data;
                // console.log(resmovieImg);

                const resmovieCredits = await axios.get(`https://api.themoviedb.org/3/movie/${movieId}/credits?api_key=${apiKey}`);
                movieCredits.value = resmovieCredits.data;
                // console.log(resmovieCredits);

                const resmovieVideos = await axios.get(`https://api.themoviedb.org/3/movie/${movieId}/videos?api_key=${apiKey}`);
                movieVideos.value = resmovieVideos.data;
                console.log(resmovieVideos);

            } catch (err) {
                console.log(err)
            }
        });

        return { movieBasic, movieInfo, movieImg, movieCredits, movieVideos }
    }
}
</script>