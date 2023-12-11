<template>
    <div class="movie__video">
        <div class="video__inner container1280">
            <h2>영상</h2>
            <div class="videoWrap">
                <div v-for="(video, index) in movieVideos.results.slice(0, 1)" :key="index">
                    <div class="video">
                        <iframe :src="`https://www.youtube.com/embed/${video.key}`" frameborder="0" allowfullscreen></iframe>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>
<style lang="scss">
.movie__video {
    .video__inner {
        .videoWrap {
            .video {
                position: relative;
                width: 100%;
                padding-bottom: 56.25%;

                iframe {
                    position: absolute;
                    width: 100%;
                    height: 100%;
                    top: 0;
                    left: 0;
                }
            }
        }
    }
}
</style>
<script>
export default {
    props: {
        movieVideos: {
            type: Object,
            required: true
        }
    },
};
</script>