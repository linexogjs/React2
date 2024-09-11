# React2


## 0904 수업내용
- 기본 환경설정

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



