# MOVIE PROJECT
<img width="100%" src="https://github.com/yunyoungsik/movie-project/blob/main/src/assets/img/thumbnail.jpg?raw=true" />
TMDB API를 활용하여 제작된 Vue 기반의 영화 정보 사이트입니다.<br />
이 사이트를 통해 최신 영화 정보를 확인할 수 있으며, 사용자는 특정 영화를 선택하면 해당 영화에 대한 상세 정보를 볼 수 있습니다.<br />
영화의 포스터, 제목, 개봉일, 평점 등을 확인할 수 있고, 영화의 줄거리를 읽을 수도 있을 뿐만 아니라, 영화에 출연하는 배우들의 프로필 사진을 살펴볼 수 있습니다.<br />
사용자들은 이 사이트를 통해 자신이 관심 있는 영화에 대한 정보를 쉽게 얻을 수 있습니다.

## 설치
```js
Vue.js - The Progressive JavaScript Framework

√ Project name: ... .
√ Package name: ... movie
√ Add TypeScript? ... No
√ Add JSX Support? ... Yes
√ Add Vue Router for Single Page Application development? ... Yes
√ Add Pinia for state management? ... No
√ Add Vitest for Unit Testing? ... No
√ Add an End-to-End Testing Solution? » No
√ Add ESLint for code quality? ... Yes
√ Add Prettier for code formatting? ... Yes

Scaffolding project in C:\Users\line\Documents\GitHub\movie-project2023...

Done. Now run:

  npm install
  npm run format
  npm run dev
```
1. `npm install sass`
2. `npm install axios`

## 사용한 기술
[메인 페이지]
1. &lt;script setup&gt; 구문: Vue의 Composition API에서 제공하는 &lt;script setup&gt;을 사용하여 컴포넌트 로직을 정의합니다. 반응형 변수인 movies와 searchTerm을 정의합니다.
2. fetchMovies 함수: 다양한 카테고리의 영화를 가져오는 함수입니다. switch문을 사용하여 각 카테고리에 따라 API URL을 결정하고 Axios를 통해 해당 URL에 요청을 보냅니다. 그리고 받은 결과를 movies에 할당합니다.
3. searchMovies 함수: 사용자가 입력한 검색어로 영화를 검색하는 함수입니다. searchTerm을 쿼리로 사용하여 API를 호출하고 받은 결과를 movies에 할당합니다.
4. onMounted 훅: 페이지가 처음 로드될 때 가장 최신의 영화를 가져오는데 사용됩니다.
5. Template: 영화 정보를 표시하는 HTML 템플릿 부분입니다. HeaderSection, FooterSection 컴포넌트와 함께 검색 및 카테고리 선택을 위한 UI 요소를 포함하고 있습니다.

[상세 페이지]
1. Template: Vue 템플릿에서는 각 섹션을 컴포넌트로 분리해서 사용했습니다. HeaderSection, DetailIntro, DetailInfo, DetailImg, DetailCredits, FooterSection 등의 컴포넌트를 사용해서 영화 정보를 보여줍니다.
2. Script (Vue Composition API): setup() 함수를 사용하여 데이터와 API 호출을 관리합니다. ref를 사용하여 movieBasic, movieInfo, movieImg, movieCredits, movieVideos 등을 초기화하고, useRoute를 이용하여 현재 라우트 정보를 가져옵니다.
3. API 호출: onMounted 훅을 사용하여 컴포넌트가 마운트된 후에 API를 호출합니다. 각 API 호출은 Axios를 사용하고, 영화 ID를 사용하여 영화에 대한 정보를 가져옵니다.
4. API Key 보안: import.meta.env.VITE_API_KEY를 사용하여 환경 변수를 통해 API 키를 가져옵니다. .env 파일에 저장된 변수를 활용하여 API 키를 보호합니다.
5. 에러 핸들링: try...catch를 사용하여 API 호출 시 발생할 수 있는 에러를 처리합니다.

## 트러블슈팅
[문제]
ref를 사용 시 값이 변경되지 않는 경우
   
[해결방법]
기존 코드에서 ref가 객체를 반환하도록 설정되었다면
```js
const movieBasic = ref({}); // 초기값으로 객체 설정
const movieInfo = ref({}); // 나머지 변수들도 동일하게 객체로 초기화
```
   
API 응답을 받은 후 .value를 사용하지 않고 객체 자체를 변경하여 값을 할당할 수 있습니다
```js
const resMovieBasic = await axios.get(`https://api.themoviedb.org/3/movie/${movieId}?language=${language}&api_key=${apiKey}`);
movieBasic.value = resMovieBasic.data; // 나머지 변수들도 동일하게 .value 대신 객체 자체를 변경
```
 ref가 객체를 반환하도록 설정하고, API 응답을 받은 후 .value가 아닌 객체를 직접 변경하여 ref 값을 업데이트하는 방식입니다. 이렇게 하면 .value를 사용하지 않고도 ref의 값을 변경할 수 있습니다.

 ## 스택
<div disflay="flex" flex-direction:column; align-items:flex-start;>
  <p><strong>Environment</strong></p>
  <div>
    <img src="https://img.shields.io/badge/VisualStudioCode-007ACC?style=flat-square&logo=VisualStudioCode&logoColor=white">
    <img src="https://img.shields.io/badge/Github-181717?style=flat-square&logo=Github&logoColor=white"> 
    <img src="https://img.shields.io/badge/Git-F05032?style=flat-square&logo=Git&logoColor=white">
  </div>
  <p><strong>Development</strong></p>
  <div>
    <img src="https://img.shields.io/badge/html5-E34F26?style=flat-square&logo=html5&logoColor=white"> 
    <img src="https://img.shields.io/badge/css-1572B6?style=flat-square&logo=css3&logoColor=white">
    <img src="https://img.shields.io/badge/Vue.js-4FC08D?style=flat-square&logo=vuedotjs&logoColor=white">
  </div>
  <p><strong>Communication</strong></p>
  <div>
    <img src="https://img.shields.io/badge/Slack-4A154B?style=flat-square&logo=Slack&logoColor=white">
    <img src="https://img.shields.io/badge/Notion-000000?style=flat-square&logo=Notion&logoColor=white">
  </div>
</div>
