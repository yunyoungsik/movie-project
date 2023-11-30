<template>
    <div class="movie__info ">
        <div class="info__inner container1280">
            <h2>영화정보</h2>
            <div v-if="movieInfo && movieInfo.genres && movieInfo.genres.length > 0">
                장르
                <span v-for="(genre, index) in movieInfo.genres" :key="index">
                    {{ genre.name }}
                    <span v-if="index < movieInfo.genres.length - 1">, </span>
                </span>
            </div>
            <div>
                상영시간
                <span>
                    {{ movieInfo.runtime }}
                </span>
            </div>
            <div>
                개봉일
                <span>
                    {{ movieInfo.release_date }}
                </span>
            </div>
        </div>

    </div>
</template>
<style lang="scss">
.movie__info {
    padding: 2vh 0;
    background-color: #090A0E;

    .info__inner {
        h2 {
            color: #fff;
            font-size: 2rem;
        }
    }
}
</style>
<script>
export default {
    props: {
        movieInfo: {
            type: Object,
            required: true
        }
    },
};
</script>