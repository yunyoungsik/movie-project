<template>
    <div class="movie__img">
        <div class="img__inner container1280">
            <h2>이미지</h2>
            <div v-for="(img, index) in movieImg.backdrops.slice(0, 5)" :key="index">
                <div class="slider__inner container1280" :style="{
                    'background-image': 'url(' + 'https://image.tmdb.org/t/p/w500/' + img.file_path + ')',
                    'background-size': 'cover',
                    'background-repeat': 'no-repeat',
                    'backdrop-filter': 'blur(30px)'
                }">
                </div>
            </div>
        </div>
    </div>
</template>
<style lang="scss">
.movie__img {
    width: 100%;

    .img__inner {
        div {
            display: flex;

            div {
                padding-bottom: 56.25%;
            }
        }
    }
}
</style>
<script>
export default {
    props: {
        movieImg: {
            type: Object,
            required: true
        }
    },
};
</script>