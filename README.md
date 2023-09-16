# nextjs-blog

![main-image](https://cdn.discordapp.com/attachments/1142343767941201923/1152535025330425986/screely-1694856154768.png)

## 🧤 프로젝트 소개

nextjs를 배우기 위해 시작한 nextjs-blog 클론 프로젝트입니다

- **배포링크** : [링크클릭](https://joyful-dango-ed1e84.netlify.app)

<br>

## 🎯 구현 사항

> 구현은 Next.js 홈페이지에서 [블로그 만들면서 배우기](https://nextjs.org/learn/basics/create-nextjs-app)를 따라하며 구현하였습니다

### lib/posts.ts

- `getSortedPostsData()`는 **\_\_posts**폴더에서 fs모듈로 posts전체리스트를 읽어오고 날짜순으로 정렬하여 반환 함수입니다.
- `getAllPostIds()`는 **\_\_posts폴더**에서 파일들을 순회하면서 `[{params : {id: 파일명}}, ...]`배열을 만듭니다.
- `getPostData()`는 id와 일치하는 포스트의 데이터를 반환합니다.

<br>

### pages/index.tsx

- `getStaticProps()`함수는 빌드(build)시 `getSortedPostsData()`함수를 사용하여 전체 post리스트를 불러오고 **Home 컴포넌트**에게 데이터를 props로 전달합니다.

<br>

### pages/[id].tsx

- Next.js의 [Dynamic Routes](https://nextjs.org/docs/routing/dynamic-routes)를 활용하기 위해 파일명을 `[id].tsx`로 설정하였습니다.

- `getStaticPaths()`함수는 `getAllPostIds()`함수를 사용하여 빌드(build)시 전체 포스트중 id와 일치하는 포스트만 걸러내고 `getStaticProps()`함수에게 포스트 id 정보를 params로 전달합니다.
- `getStaticProps()`함수는 빌드(build)시 `getPostData(params.id)`함수를 사용하여 포스트 한개의 데이터를 **Post 컴포넌트**에게 props로 전달합니다.

<br>

## 🤔 구현 후 느낀점

- Next.js 개념만 익히고 API들은 전혀 모르는 상태로 시작하였는데 하나하나씩 구현하면서 API를 통해서 SSG가 어떻게 작동하는지 좀 더 알게되었습니다.
