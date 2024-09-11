# React2

## 0911 수업내용

- 그 밖에 설정..

    - 개발 시 타입스크립트를 주 언어로 쓰고 싶다면 앞서 살펴본 것과 같은 방법으로 타입스크립트 전용 플러그인을 설치하고, 설정을 바꿔주면 됩니다.
    - 프로잭트를 생성할 때 선택할 수 있기 때문에 생성할 때 설정하는 것을 추천합니다.

    - 웹팩은 특정 라이브러리, 페이지, 기능에 대해 컴파일된 코드를 전부 포함하는 번들을 만들어줍니다.
- 하지만..
    - 설정을 바꿀 일은 그렇게 많지 않습니다.
    - 꼭 수정해야 한다면 대부분 next.config.js 파일의 기본값을 변경하는 것으로도 충분합니다.
    - 이 파일을 root에 만들고 객체를 export하면 해당 내용은 Next.js의 기본 설정 값을 덮어씁니다.
    - 만일 기본 웹팩 설정을 바꾸고 싶다면 webpack이라는 키에 새로운 속성값을 지정합니다.

- 몇 가지 일어날 수 있는 오류
    - 처음 Next 프로젝트를 생성할 때 오류로 생성되지 않는 경우가 있습니다.
    이것은 CPA가 설치되어 있지 않아서 생기는 현상입니다.
    - 이런 경우는 다음과 같이 create-react-app을 Gloabal로 설치해 주면 됩니다.
    - $npm i -g create-react-app
    - 이제 프로젝트를 생성합니다.
    - $ npx create-next-app@latest 

- Transpile은 어떻게 동작하나
    - Babel은 ECMAScript와 같은 자바스크립트 최신 버전이나, TypeScript를 이전 버전의 코드로 변환시켜주는 Transpile 도구입니다.
    - 개발자가 작성한 코드 -> Parse -> Transform -> Generate -> 이전 버전의 코드

- 왜 SWC (Speedy Web Compiler)를 사용해야 하는가?
    - babel의 단점
        - Babel로 변환된 코드를 이해하기 어렵다.
        - 원 코드에 비해 변환 코드의 길이가 늘어난다.
        - 변환에 시간이 많이 걸린다.
    - SWC의 장점
        - Next 12 이후 별도의 설정 없이 SWC를 사용할 수 있다. 
- SWC를 프로젝트에 적용하려면?
    - 새로운 프로젝트에 적용하는 것은 다음 명령으로 프로젝트를 생성하면 바로 사용 가능합니다.
    - $ npx create-next-app@latest
    - 또는 $ npx create-next-app@12
    - Next 12 이전 버전의 프로젝트에 적용하려면 다음과 같이 업그레이드 해줘야 합니다.
    - $ npm install next@12
    - 그리고 Babel을 설정했다면 설정 파일 (.babelrc 또는 babel.config.js) 을 삭제해 줍니다.

- ch2 에서는 다음과 같은 내용을 다룹니다.
    - 서버 사이드 랜더링을 사용하여 각 요청별로 페이지를 동적으로 랜더링하는 방법
    - 특정 컴포넌트를 클라이언트에서만 랜더링하는 다양한 방법
    - 빌드 시점에서 정적 페이지를 생성하는 방법
- 서버 사이드 랜더링 (SSR)
    - 생소할 수도 있지만 웹 페이지를 제공하는 가장 흔한 방법입니다.
    - APM을 이용하는 일반적인 웹 페이지 생성이라고 보면 됩니다.
    - 여기에 자바스크립트 코드가 적재되면 동적으로 페이지 내용을 랜더링합니다.
    - Next.js도 이와 같이 동적으로 페이지를 렌더링할 수 있습니다.
    - 그리고 여기에 스크립트 코드를 집어 넣어서 나중에 웹 페이지를 동적으로 처리할 수도 있는데 이를 하이드레이션이라고 합니다.
    - 예를 들면 어떤 사람이 작성한 블로그 글을 한 페이지 모아서 작성해야 한다면 SSR을 이용하는 것이 적당합니다.
    - 서버 사이드 랜더링 -> 자바스크립트가 하이드레이션된 페이지를 전송 -> 클라이언트에서 DOM 위에 각 스크립트 코드를 하이드레이션 : 페이지 새로고침 없이 사용자와 웹 페이지간 상호작용을 가능하게 합니다.

    - 리액트 하이드레이션 덕분에 이 상태에서 웹 앱은 싱글 페이지 애플리케이션(SPA) 처럼 작동할 수 있습니다.
    - CSR과 SSR의 장점을 모두 가지는 것입니다.
    - 특정 전략만 사용한다고 가정하면 SSR이 CSR에 비해 여러가지 장점이 많습니다.

    - SSR의 장점
        - 더 안전한 웹 애플리케이션 : 쿠키관리, 주요 API, 데이터 검증 등과 같은 작업을 서버에서 처리하기 떄문에 중요한 데이터를 클라이언트에 노출할 필요가 없기 떄문입니다.
        - 더 뛰어난 웹 사이트 호환성 : 클라이언트 환경이 자바스크립트를 사용하지 못하거나 오래된 브라우저를 사용하더도 서비스를 제공할 수 있습니다.
        - 더 뛰어난 SEO : 서버가 렌더링한 HTML을 받기 때문에 봇이나 웹 크롤러가 페이지를 랜더링할 필요가 없기 때문입니다.

- SSR이 최적의 랜더링 전략이 아닌 경우
    - 클라이언트가 페이지를 요청할 때마다 페이지를 다시 랜더링할 수 있는 서버가 필요합니다.
    - 다른 방식에 비해 SSR이 더 많은 자원을 소모하고, 더 많은 부하를 보이며, 유지보수 비용도 증가합니다.
    - 페이지에 대한 요청을 처리하는 시간이 길어집니다.
    - 페이지가 외부 API 또는 데이터 소스에 접근해야 한다면, 해당 페이지를 랜더링할 때마다 이를 다시 요청해야 합니다.
    - 페이지 간의 이동은 CSR에 비해 느립니다.
    - 중요한 것은 Next.js가 기본적으로 빌드 시점에 정적으로 페이지를 만든다는 것 입니다.
    - 페이지에서 외부 API를 호출하거나 데이터베이스에 접근하는 등 동적 작업을 해야한다면 해당하는 함수를 페이지에 export 해야 합니다.

- 페이지에 대한 요청이 들어오면 서버가 Rest API를 호출해서 필요한 사용자 정보를 가져옵니다.
- 이 과정은 다음과 같은 세부 단계로 나눌 수 있습니다.
1. getServerSideProps라는 비동기 함수를 export 합니다.
    - 빌드 과정에서 Next.js는 이 함수를 export하는 모든 페이지를 찾아서 서버가 페이지 요청을 처리할 때 getServerSideProps 함수를 호출하도록 만듭니다.
2. getServerSideProps 함수는 props라는 속성값을 갖는 객체를 반환합니다.
    - 이 props는 컴포넌트로 전달되 서버와 클라이언트 모두가 props에 접근할 수 있게 됩니다.
    - fetch API는 서버에서 실행되기 때문에 별도의 폴리필을 끼워 넣을 필요는 없습니다.
3. IndexPage 함수를 수정해서 props를 인자로 받습니다.
    - 이 props는 getServerSideProps 함수에서 반환한 props의 모든 내용을 갖고 있습니다.

- 클라이언트 사이드 랜더링 (CSR)
    - 리액트 앱을 실행하면 렌더링 시작전에 빈 화면이 한동안 유지 되는 것이 보입니다.
    - 이는 서버에서 스크립트와 스타일만 포함된 HTML을 전송하기 때문입니다.
    - 실제 랜더링은 클라이언트에서 이루어 집니다.
    - CSR로 생성한 앱의 HTML을 보면 div 태그 하나 밖에 없습니다. 그래서 빈 화면만 보였던 겁니다.
    -  빌드 과정에서 js와 css파일을 html 페이지에 불러오도록 만들고 root div에 랜더링 합니다.
    



## 0904 수업내용

- 기본 환경설정 정리 (0904 환경설정)

파워쉘 관리자 권한으로 열고 아래 내용 입력하기

Set-ExecutionPolicy Bypass -Scope Process -Force; [System.Net.ServicePointManager]::SecurityProtocol = [System.Net.ServicePointManager]::SecurityProtocol -bor 3072; iex ((New-Object System.Net.WebClient).DownloadString('https://community.chocolatey.org/install.ps1'))

이러면 설치 중...끝나면 확인완료를 위해

choco -v 로 버전 체크

https://community.chocolatey.org/packages?q=git

맨 위에 있는 거 설치 choco install git 똑같이 입력

node -v
npm -v
npx -v 로 버전 체크 (설치 확인)

(
   필수 아닌 거 같긴 한데 메모
   비쥬얼스튜디오코드를 zip으로 다운 받아서 D드라이브에 옮김
   교수님 진도 똑같이 하려면 이렇게
)


폴더 만들기 (C 드라이븐던 D 드라이브던)

npm i -g create-react-app

npx create-next-app@latest

y 치고 프로젝트 이름 page-router 입력

차례대로 no yes no no no yes 그리고 엔터하면 설치

그리고 설치한 page-router로 폴더이동

npm run dev 명령어 실행 

윈도우 기본 앱 설정으로 마이크로소프트로 켜지면 창을 크롬으로 바꿀 수 있음


인덱스.js 파일을 카피. 그리고 카피한 이름을 about.js 로 수정

그리고 about.js의 21번째 라인을 about.js로 수정


다시 원래의 폴더로 돌아와서 npx create-next-app@latest 입력

프로젝트 이름은 app-router

차례대로 n, y, n, y, y, 엔터

app-router 만든 폴더로 이동해서 npm run dev 입력

아까랑 똑같이 이번엔 page.js를 카피해서 이름 바꾸기 >> about.js 로

했다가..? 다시 바꿈 그리고 src app에서 about 폴더 생성하고 about.js 넣기

그리고 이름을 page.js로 재변경..? << 일단 이렇게 실행은 가능.

page.js 확인하기

2 번째 라인 확인 : import styles from "../page.module.css";

10 번째 라인 확인 :   <code className={styles.code}>src/app/about/page.js</code>


https://github.com/vercel (참고용 자료)


그리고 다시 원래의 d 드라이브로 돌아오기

npx create-next-app --example blog-starter

프로젝트 이름 my-blog

다시 my-blog 폴더 선택해서 열기

깃베쉬 명령어 입력 : npm run dev  >>> 이러면 열리는 걸 확인가능



