<template>
    <div class="movie__credits">
        <div class="credits__inner container1280">
            <h2>출연진</h2>
            <div class="credit">
                <div v-for="(cast, index) in movieCredits.cast.slice(0, 5)" :key="index">
                    <img :src="'https://image.tmdb.org/t/p/w500' + cast.profile_path" :alt="cast.name">
                    <p>{{cast.character}}</p>
                    <p>{{ cast.name }}</p>
                </div>
            </div>
            <h2>제작진</h2>
            <div class="credit crew">
                <div v-for="(crew, index) in movieCredits.crew.slice(0, 5)" :key="index">
                    <img :src="'https://image.tmdb.org/t/p/w500' + crew.profile_path" :alt="crew.name">
                    <p>{{ crew.department }}</p>
                    <p>{{ crew.name }}</p>
                </div>
            </div>
        </div>
    </div>
</template>
<style lang="scss">
.movie__credits {
    padding: 2vh 0;
    .credits__inner{
        h2 {
            font-size: 2rem;
        }
        .credit {
            width: 100%;
            display: flex;
            justify-content: space-between;
            flex-wrap: wrap;
            div {
                width: 19%;
                margin-bottom: 1vh;
                text-align: center;
                color: #777777;
                font-size: 0.8rem;
                img {
                    width: 100%;
                    vertical-align: top;
                }
            }
        }
    }
}
</style>
<script>
export default {
    props: {
        movieCredits: {
            type: Object,
            required: true
        }
    },
};
</script>