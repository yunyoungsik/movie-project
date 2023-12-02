<template>
    <div class="movie__img">
        <div class="img__inner container1280">
            <h2>이미지</h2>
            <div class="imgWrap">
                <div class="" v-for="(img, index) in movieImg.backdrops.slice(0, 5)" :key="index">
                    <div class="img" :style="{
                        'background-image': 'url(' + 'https://image.tmdb.org/t/p/w500/' + img.file_path + ')',
                        'background-size': 'cover',
                        'background-repeat': 'no-repeat',
                        'backdrop-filter': 'blur(30px)'
                    }">
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>
<style lang="scss">
.movie__img {
    width: 100%;
    padding: 2vh 0;
    .img__inner {
        h2{
            font-size: 2rem;
        }
        .imgWrap {
            width: 100%;
            display: flex;
            div {
                width: 100%;
                .img{
                    padding-bottom: 56.25%;
                }
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