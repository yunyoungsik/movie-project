<script setup>
import { ref, onMounted } from 'vue';
import axios from 'axios';

const movies = ref([]);
const searchTerm = ref('');

const fetchMovies = async (category) => {
  let url = 'https://api.themoviedb.org/3/movie/popular'

  switch (category) {
    case 'latest':
      url = 'https://api.themoviedb.org/3/movie/now_playing'
      break;
    case 'popular':
      url = 'https://api.themoviedb.org/3/movie/popular'
      break;
    case 'upcoming':
      url = 'https://api.themoviedb.org/3/movie/upcoming'
      break;
    case 'toprated':
      url = 'https://api.themoviedb.org/3/movie/top_rated'
      break;
  }
  try {
    const response = await axios.get(url, {
      params: {
        api_key: '12b99ef290ad212dfcf448ba402f97ab',
        language: 'ko-KR',
        page: '1'
      }
    });
    movies.value = response.data.results;
    console.log(response.data.results);
  } catch (err) {
    console.log(err);
  }
}
const searchMovies = async () => {
  try {
    const response = await axios.get('https://api.themoviedb.org/3/search/movie', {
      params: {
        api_key: '12b99ef290ad212dfcf448ba402f97ab',
        language: 'ko-KR',
        query: searchTerm.value,
        page: '1'
      }
    });
    movies.value = response.data.results;
    console.log(response.data.results)
  } catch (err) {
    console.log(err);
  }
}

onMounted(async () => {
  // 초기 페이지 로딩 시 최신 영화를 가져옴
  await fetchMovies('latest');
});
</script>

<template>
  <HeaderSection />
  <main id="main" role="main">
    <div class="movie__slider">
        <div class="slider__inner container1280">
            <div class="img play__icon">
              <a href="#">
            <img src="https://image.tmdb.org/t/p/w500/7M2pc9OboapgtoBbkU49Aim7O5B.jpg">
          </a>
            </div>
            <div class="text">
          <div class="title">트롤 밴드 투게더</div>
          <div class="info">
            <div class="date">2023-10-12</div>
            <div class="average">7.204</div>
          </div>
          <div class="desc">
            전 세계 모든 트롤을 열광케 했던 최고의 아이돌 그룹 ‘브로존’.
            역대급 무대 실수와 형제 간의 불화로 결국 해체한 뒤, 모두에게 잊혀 간다.
            그러던 어느 날, ‘브로존’의 황금막내 ‘브랜치’는 메인보컬 ‘플로이드’가 슈퍼스타 ‘벨벳’과 ‘비니어’에게 잡혀 재능을 빼앗기고 있다는 소식을 듣는다.
            그를 구하기 위해서는 흩어져 있는 ‘브로존’을 재결합하고 완벽한 화음을 되찾아야 하는데…
            12월, 가장 짜릿한 컴백 무대의 시작!"
          </div>
          <div class="credit">
            <img src="https://image.tmdb.org/t/p/w500/yirl6fEmeXY5xcvJw3nTcCNq9Cw.jpg" alt="Anna Kendrick">
            <img src="https://image.tmdb.org/t/p/w500/6Yk5t9RwkdkAT8Qv45934Eez2CA.jpg" alt="Justin Timberlake">
            <img src="https://image.tmdb.org/t/p/w500/8XJzD4mrxlBvtYjP1wVNTW5K9ya.jpg" alt="Camila Cabello">
            <img src="https://image.tmdb.org/t/p/w500/e9XlcFnZQiBSQ1vISQVyTOrkIaq.jpg" alt="Eric André">
            <img src="https://image.tmdb.org/t/p/w500/6u95ZNLrADSlK7CVkgEvC0jLIJh.jpg" alt="Amy Schumer">
          </div>
        </div>
        </div>
        <div class="slider__bg" style="background-image: url(https://image.tmdb.org/t/p/w500/xgGGinKRL8xeRkaAR9RMbtyk60y.jpg); background-size: cover; background-repeat: no-repeat;"></div>
    </div>
    <div class="container">
      <div class="movie__inner container1280">

        <!-- <MovieSearch @onSearch="search" />
            <MovieTage @onSearch="tags" />
            <MovieCont /> -->
        <section class="movie__search">
          <h2 class="blind">검색</h2>
          <input type="search" placeholder="검색어를 입력해주세요." v-model="searchTerm" @keyup.enter="searchMovies">
          <button type="submit" @click="searchMovies">
            <svg clip-rule="evenodd" fill-rule="evenodd" stroke-linejoin="round" stroke-miterlimit="2" viewBox="0 0 24 24"
              xmlns="http://www.w3.org/2000/svg">
              <path
                d="m15.97 17.031c-1.479 1.238-3.384 1.985-5.461 1.985-4.697 0-8.509-3.812-8.509-8.508s3.812-8.508 8.509-8.508c4.695 0 8.508 3.812 8.508 8.508 0 2.078-.747 3.984-1.985 5.461l4.749 4.75c.146.146.219.338.219.531 0 .587-.537.75-.75.75-.192 0-.384-.073-.531-.22zm-5.461-13.53c-3.868 0-7.007 3.14-7.007 7.007s3.139 7.007 7.007 7.007c3.866 0 7.007-3.14 7.007-7.007s-3.141-7.007-7.007-7.007z"
                fill-rule="nonzero" />
            </svg>
          </button>
        </section>
        <div class="movie__tag">
          <ul>
            <li><a href="#" @click="fetchMovies('latest')">최신영화</a></li>
            <li><a href="#" @click="fetchMovies('popular')">인기영화</a></li>
            <li><a href="#" @click="fetchMovies('upcoming')">개봉예정</a></li>
            <li><a href="#" @click="fetchMovies('toprated')">최고평점</a></li>
          </ul>
        </div>
        <section class="movie__cont">
          <h2 class="blind">영화</h2>
          <div class="movie play__icon" v-for="movie in movies" :key="movie.id">
            <a :href="'/detail/' + movie.id">
              <img :src="'https://image.tmdb.org/t/p/w500' + movie.poster_path" :alt="movie.title">
            </a>
          </div>
        </section>
      </div>
    </div>
  </main>
  <FooterSection />
</template>
<script>
import HeaderSection from '@/components/section/HeaderSection.vue'
import FooterSection from '@/components/section/FooterSection.vue'

// import MovieSearch from "@/components/contents/MovieSearch.vue";
// import MovieTage from "@/components/contents/MovieTag.vue";
// import MovieCont from "@/components/contents/MovieCont.vue";

// export default {
//   name: "MovieHomePage",
//   components: {
//     HeaderSection,
//     FooterSection,
//     MovieSearch,
//     MovieTage,
//     MovieCont,
//   },
//   data() {
//     return {
//       movies: [],
//     }
//   },
//   methods: {
//     async search(query) {
//       try {
//         const response = await fetch(`https://api.themoviedb.org/3/search/movie?api_key=12b99ef290ad212dfcf448ba402f97ab&language:ko-KR&query=${query}`)
//         const result = await response.json();
//         console.log(result);
//       } catch (error) {
//         console.log(error)
//       }
//     },
//     async tags(query) {
//       try {
//         const response = await fetch(`https://api.themoviedb.org/3/search/movie?api_key=12b99ef290ad212dfcf448ba402f97ab&language:ko-KR&query=${query}`)
//         const result = await response.json();
//         console.log(result);
//       } catch (error) {
//         console.log(error)
//       }
//     }
//   }
// }

</script>

<style lang="scss">
.movie__slider {
    width: 100%;
    height: 90vh;
    position: relative;

    .slider__inner {
        width: 100%;
        height: 100%;
        display: flex;
        align-items: center;
        justify-content: center;
        z-index: 2;

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
    .slider__bg {
        position: absolute;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        z-index: -1;
        filter: blur(5px);
        &::after {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-color: rgba(0,0,0,0.5);
            z-index: 1;
        }
    }
}

.movie__inner {
  padding: 1rem;
  background-color: #0F1014;

  .movie__search {
    position: relative;
    margin-bottom: 1rem;

    input {
      width: 100%;
      height: 50px;
      border-radius: 5px;
      padding: 10px;
      background-color: transparent;
      border: 1px solid rgba(255, 255, 255, 0.15);
      color: var(--white);

      &:focus {
        outline: 1px solid rgba(255, 255, 255, 0.3);
      }
    }

    button {
      position: absolute;
      right: 10px;
      background-color: transparent;
      cursor: pointer;
      width: 50px;
      height: 50px;

      svg {
        fill: rgba(255, 255, 255, 0.3);
        width: 24px;
        height: 24px;
      }
    }
  }

  .movie__tag {
    margin-bottom: 1rem;

    ul {
      display: flex;

      li {
        border-right: 1px solid rgba(255, 255, 255, 0.15);

        &:last-child {
          border: 0;
        }

        a {
          color: var(--white);
          // background-color: rgba(255, 255, 255, 0.15);
          border-radius: 5px;
          padding: 0.5rem 1rem;
          // margin-right: 1rem;

          &:hover {
            color: #F80147;
            // background-color: #F80147;
          }
        }
      }
    }
  }

  .movie__cont {
    display: flex;
    flex-wrap: wrap;
    justify-content: space-between;

    .movie {
      width: 24%;
      margin-bottom: 2vh;
    }
  }
}
</style>
