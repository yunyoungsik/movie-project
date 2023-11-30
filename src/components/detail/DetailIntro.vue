<template>
    <div class="movie__slider">
        <div class="slider__inner container1280" :style="{
            'background-image': 'url(' + 'https://image.tmdb.org/t/p/w500/' + movieBasic.backdrop_path + ')',
            'background-size': 'cover',
            'background-repeat': 'no-repeat',
            'backdrop-filter': 'blur(30px)'
        }">
            <div class="img play__icon">
                <img :src="'https://image.tmdb.org/t/p/w500' + movieBasic.poster_path" :alt="movieBasic.title">
            </div>
            <div class="text">
                <div class="title">{{ movieBasic.title }}</div>
                <div class="info">
                    <div class="date">{{ movieBasic.release_date }}</div>
                    <div class="average">{{ movieBasic.vote_average }}</div>
                </div>
                <div class="desc">
                    {{ movieBasic.overview }}
                </div>
                <div class="credit">
                    <div v-for="(crew, index) in movieCredits.crew.slice(0, 5)" :key="index">
                        <img :src="'https://image.tmdb.org/t/p/w500' + crew.profile_path" :alt="crew.name">
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>
<style lang="scss">
.movie__slider {
    width: 100%;
    height: 90vh;

    .slider__inner {
        width: 100%;
        height: 100%;
        display: flex;
        align-items: center;
        justify-content: center;

        .img {
            width: 20vw;

            img {
                width: 100%;
                vertical-align: top;
            }
        }

        .text {
            margin-left: 2vw;

            .title {
                font-size: 3rem;
                font-weight: 700;
            }

            .info {
                display: flex;
                font-size: 0.8rem;

                .date {
                    padding-right: 1rem;
                    border-right: 1px solid var(--white);
                }

                .average {
                    padding-left: 1rem;
                }
            }

            .desc {
                margin-top: 1rem;
                width: 40vw;
                white-space: pre-line;

                overflow: hidden;
                text-overflow: ellipsis;
                display: -webkit-box;
                -webkit-line-clamp: 3;
                -webkit-box-orient: vertical;
            }
        }

        .credit {
            display: flex;

            img {
                margin-top: 1rem;
                margin-right: 1vw;
                width: 5vw;
                vertical-align: top;
            }

        }
    }

}
</style>
<script>
export default {
    props: {
        movieBasic: {
            type: Object,
            required: true
        },
        movieCredits: {
            type: Object,
            required: true
        },
    },
};
</script>