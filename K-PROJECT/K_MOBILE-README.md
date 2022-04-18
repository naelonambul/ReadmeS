# FC Smart Platform 구축을 위한 시스템 개발(모바일)

**소개 :** 프랜차이즈(가맹본부/가맹점), 소상공인 및 자영업자의 매장관리 및 교육을 위한 플랫폼 개발을 통해 프랜차이즈 가맹본부의 가맹점 관리 편의성 제공

## 빌드 안될때

- npx react-native start and --reset-cache
- 또는
- npx react-native run-android --reset-cache
- cd android && gradlew clean && cd .. && npm run and
- cd android && gradlew clean && cd .. && npx react-native start and --reset-cache
- blacklist.js 확인

## debug

- devtools failed to load sourcemap could not load content for react native (크롬 광고차단 어플 끄기)

## VSCODE 익스텐션

- [Yamoo](https://yamoo9.github.io/react-master/lecture/r-setting-up.html#prettier-code-formatter)

## 사용 기술(20.04.07)

- [Node.js](https://nodejs.org/ko/) **12.16.1 LTS** (npm 6.13.4)
- [React](https://ko.reactjs.org/) **16.13.1**
- [React Native](https://reactnative.dev/) **0.62**
- [MariaDB](https://mariadb.org/) **10.4.12**
- [Dorker](https://www.docker.com/)

## UI

- [Toast](https://github.com/mochixuan/react-native-smart-tip) toast

### client

- [axios](https://www.npmjs.com/package/axios) **0.19.2**

### server

- [express](https://www.npmjs.com/package/express/) **4.17.1**
- [request](https://www.npmjs.com/package/request-promise-native) **deprecated(npm audit로 의존성 트리 취약점 확인요먕)**
- [mariadb](https://www.npmjs.com/package/mariadb)

## 참고 사이트

### Firebase push

- [공식 홈페이지](https://firebase.google.com/docs/cloud-messaging?hl=ko)
- [블로그](https://romeoh.tistory.com/entry/React-Native-Firebase-Push-Notification-%EC%B6%94%EA%B0%80-Android?category=338449)

### 네이버 지도 API

- [공식홈페이지](https://www.ncloud.com/product/applicationService/maps)

## 디비 설계

- [OKKY](https://okky.kr/article/347032)

## 리액트 관련

- [우아한](https://woowabros.github.io/experience/2019/01/02/kimcj-react-mobx.html)

## 리액트 네이티브 관련

- [사이트모음](https://github.com/jondot/awesome-react-native#frameworks)
- [NativeBase](https://nativebase.io/)
- [progress](https://www.npmjs.com/package/react-native-progress)
- [image-picker](https://www.npmjs.com/package/react-native-image-picker)
- [material-textfield](https://www.npmjs.com/package/react-native-material-textfield)
- [camera](https://www.npmjs.com/package/react-native-camera)
- [autogrow-textinput](https://www.npmjs.com/package/react-native-autogrow-textinput)
- [react-native-image-viewing](https://www.npmjs.com/package/react-native-image-viewing)
- [react-native-toast-message](https://www.npmjs.com/package/react-native-toast-message)

## 리액트 네이티브 관련

-[아이콘 react-native-vector-icons directory](https://oblador.github.io/react-native-vector-icons/)

## 개발 규칙

### 네이밍

- 컴포넌트 : 대문자 and 대문자

```jsx
// 파일명 OneTwoThree.js
import OneTwoThree from './OneTwoThree';
```

- 함수 : 소문자 and 대문자

```jsx
function oneTwoThree () {
  ...
};
```

- 변수 : 소문자 and 대문자

```jsx
const oneTwoThree;
```

### CSS 적용

- .css 및 .scss 파일의 클래스 스타일 적용

### 폴더 구조

```text
src
├── assets
├── components
|   ├── App.jsx
|   ├── App.css
|   ├── common ( 2개 이상의 컴포넌트에 의해 참조되는 경우 )
|   |   └── ...
|   └── individual ( 컴포넌트 명 폴더별로 분류 )
|       └── ...
├── styles
|   ├── views (views 폴더 내에 있는 views의 css)
|   |   └── ...
|   └── ... ( react-create-app css )
├── views
|   └── ...
├── index.jsx
├── .env
├── package.json
└── README.md
```

### 화면 페이지 및 라우트명

> ()안의 Path가 없는 경우 팝업형태 등의 별도의 라우트가 없는 페이지
>
> 상위 폴더의 Path는 생략
>
> 메인 하위 Path는 main 생략

1. 웹 페이지

```text
로그인(member/login)
회원가입(member/register)
메인(main)/
├── 회원관리(manage/member)/
|   ├── 가맹본부 관리(headquarters)/
|   |   ├── 관리 메인(main)
|   |   ├── 상세 화면(detail)
|   |   ├── 수정 화면(modify)
|   |   └── 권한등록 화면(authority)
|   ├── 슈퍼바이저(SV) 관리(supervisor)/
|   |   ├── 관리 메인(main)
|   |   ├── 상세 화면(detail)
|   |   ├── 인수인계 화면
|   |   ├── 가맹본부 화면
|   |   ├── 가맹점 화면
|   |   ├── 수정 화면(modify)
|   |   └── 권한등록(authority)
|   ├── 가맹점주 관리(shopkeeper)/
|   |   ├── 가맹점주 메인(main)
|   |   ├── 상세 화면(detail)
|   |   └── 수정 화면(modify)
|   └── 탈퇴회원 관리(withdrawal)/
|       └── 탈퇴회원 메인(main)
├── 매장관리(manage/store)/
|   ├── QSC 관리(qsc)/
|   │   ├── QSC 메인(가맹본부 선택)(headquarters)
|   │   ├── 가맹점 점검 리스트 화면(shopkeeper)
|   │   └── 점검 정보 화면(result)
|   ├── 법규준수사항 관리(regulations)/
|   |   ├── 법규준수사항 메인(main)
|   |   └── 점검 결과 화면(result)
|   ├── 점주 상담 관리(advice)/
|   |   ├── 점주 상담 메인(main)
|   |   └── 점검 결과 화면(result)
|   ├── 점검 결과 관리(inspection)/
|   |   ├── 점검 결과 메인(main)
|   |   └── 결과 리포트 화면(result)
|   └── 항목 등록 관리(item)/
|       └── 결과 리포트 메인(main)
├── 수익관리(manage/profit)/
|   ├── 비용 항목 관리(cost)/
|   |   └── 비용 항목 메인(main)
|   ├── 수익 현황 관리(condition)/
|   |   ├── 수익 현황 메인(main)
|   |   └── 상세 화면(detail)
|   └── 수익 분석 관리(analysis)/
|       ├── 수익 분석 메인(main)
|       └── 상세 화면(detail)
├── 소통 일정 관리(manage/participate)/
|   ├── 소통 관리(communication)/
|   |   ├── 소통 메인(main)
|   |   ├── 리스트 화면(list)
|   |   └── 상세 화면(detail)
|   ├── VOC 관리(voc)/
|   |   ├── VOC 메인(main)
|   |   ├── 리스트 화면(list)
|   |   ├── 상세 화면(detail)
|   |   └── 댓글 등록 화면(register)
|   └── 일정 관리(schedule)/
|       ├── 일정 메인(main)
|       ├── 일정 화면(calendar)
|       └── 수정 화면(detail)
├── 게시판 관리(manage/noticeboard)/
|   └── 공지사항 관리(notice)/
|       ├── 공지사항 메인(main)
|       ├── 상세 화면(detail)
|       └── 수정 화면(modify)
├── 운영 관리(manage/operate)/
|   ├── 기본 설정 관리(basics)/
|   |   └── 기본 설정 메인(main)
|   ├── 배너 관리(banner)/
|   |   └── 배너 메인(main)
|   ├── 팝업 관리(popup)/
|   |   ├── 팝업 메인(main)
|   |   └── 수정 화면(modify)
|   ├── 그룹 관리(group)/
|   |   ├── 그룹 메인(main)
|   |   └── 수정 화면(modify)
|   ├── 권한 관리(authority)/
|   |   └── 권한 메인(main)
|   └── 관리자 관리(administrator)/
|       ├── 관리자 메인(main)
|       └── 수정 화면(modify)
└── 통계 관리(manage/statistics) /
    ├── 회원 현황 관리(member)/
    |   ├── 가맹본부 현황 메인(headquarters)
    |   |   ├── 일별(day)
    |   |   ├── 시간대별(time)
    |   |   ├── 요일별(week)
    |   |   └── 월별(month)
    |   ├── 슈퍼바이저(SV) 현황 메인(supervisor)
    |   |   ├── 일별(day)
    |   |   ├── 시간대별(time)
    |   |   ├── 요일별(week)
    |   |   └── 월별(month)
    |   ├── 가맹점 현황 메인(shopkeeper)
    |   |   ├── 일별(day)
    |   |   ├── 시간대별(time)
    |   |   ├── 요일별(week)
    |   |   └── 월별(month)
    |   └── 전체 회원 현황 메인(general)
    |       ├── 일별(day)
    |       ├── 월별(month)
    |       ├── 성별(gender)
    |       ├── 연령별(age)
    |       └── 지역별(area)
    └── 접속 현황 관리(access)/
        ├── 방문자 분석 메인(visitor)
        |   ├── 당일(day)
        |   ├── 일별(day)
        |   ├── 시간대별(time)
        |   ├── 요일별(week)
        |   └── 월별(month)
        ├── 방문자 환경 분석 메인(environment)
        |   ├── 운영체제(os)
        |   └── 브라우저(browser)
        └── 방문자 IP 분석 메인(ip)
```

2. 모바일 페이지

```text
로그인(m/member/login)
회원가입(m/member/register)
개인정보설정(m/member/info)
메인(m/main)/
알림(alarm)/
공지사항(noticeboard)/
  메인(main)
  세부사항(:숫자/detail)
정보관리(infocontrol)/
  메인(main)
  세부사항(:숫자/detail)
매장관리(shopcontrol)/
      매장 상세 정보(info)
        매장 검색(search)
        매장 상세 정보(:숫자/detail)/
          회 차별 결과 리포트(report)/
            리스트 선택창(search)
            회차별 결과창(:숫자/detail)
          점검결과 세부내용(inspect)/
            여러 회차 내용 리스팅(list)
          QSC 점검 바로가기(링크)
      QSC(qsc)
        매장 검색(search)
        신규 회차 점검페이지 (new)
      법규준수 관리(regulations)
        매장 검색(search)
        탭(자가진단, 일,월,분기,연도) 별 입력페이지(new)
      점주 상담(advice) //이번달 등록하는것만
        매장 검색(search)
        신규 점주 상담 입력페이지(new)
      결과 리포트(report) //이번달
        매장 검색(search)
        점검 결과 페이지(new)
수익분석(profit)/
  수익현황(condition)
    상세페이지(detail)
  수익분석 리포트(report)
    상세페이지(detail)
      해당점포 연도별 분석(year)
        ?? 페이지(:숫자)
      동일 지역/동일 규모 분석(same)
        형태별 페이지 (form:기간검색)
        지역별 페이지 (location:기간검색)
소통일정(particpate)/
  소통(communication)
    관리 점포 리스팅 페이지(search)
      소통 리스팅(board)
      소통 내부 페이지(:숫자)
      소통 등록 페이지(write)
      소통 답글 페이지(reply)
  VOC(voc)
    voc 리스팅(board)
    voc 내부 페이지(:숫자)
    voc 등록 페이지(write)
    voc 답글 등록 페이지(reply)
  일정(schedule)
    달력 페이지(calander)(색상 알림 포함) + 하단 정보 서랍
    일정 등록 페이지(register)
    일정 수정 페이지(modify)
```
