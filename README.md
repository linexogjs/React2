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



