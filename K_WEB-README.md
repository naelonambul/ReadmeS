# FC Smart Platform 구축을 위한 시스템 개발

**소개 :** 프랜차이즈(가맹본부/가맹점), 소상공인 및 자영업자의 매장관리 및 교육을 위한 플랫폼 개발을 통해 프랜차이즈 가맹본부의 가맹점 관리 편의성 제공

## 사용 기술

- [Node.js](https://nodejs.org/ko/) **12.16.2 LTS**
- [React](https://ko.reactjs.org/) **16.12**

### client

- [axios](https://www.npmjs.com/package/axios) **0.19.2**

### server & Dev

- [express](https://www.npmjs.com/package/express/) **4.17.1**
- [Dorker](https://www.docker.com/)

### DB

- [MariaDB](https://mariadb.org/) **10.4.12**

## 참고 사이트

### Firebase push

- [공식 홈페이지](https://firebase.google.com/docs/cloud-messaging?hl=ko)

### 아이콘

- [react-incons](https://react-icons.github.io/react-icons/)

### 네이버 지도 API

- [공식홈페이지](https://www.ncloud.com/product/applicationService/maps)

## 개발 규칙

### 네이밍

- 컴포넌트 : 대문자 and 대문자

```jsx
import OneTwoThree from "./OneTwoThree";
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
├── store ( mobx )
|   └── ... (redux, vuex와 같은 상태관리 )
├── styles
|   ├── views (views 폴더 내에 있는 views의 css)
|   |   └── ...
|   ├── common ( 컴포넌트에서 사용되는 style에 적용하기 위한 css변수 )
|   |   └── ...
|   ├── fonts ( 사이트에 적용된 fonts )
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
로그인(member/login)    주석ok
회원가입(member/register)    주석ok
개인정보보호(privacy)    주석ok
아이디찾기(id)    주석ok
비밀번호찾기(password)    주석ok
대시보드(intro)    주석ok
메인(main)/
├── 회원관리(manage/member)/
|   ├── 가맹본부 관리(headquarters)/
|   |   ├── 메인(main)
|   |   ├── 등록(input)
|   |   ├── 상세(detail)
|   |   └── 수정(modify)
|   ├── 슈퍼바이저 관리(supervisor)/
|   |   ├── 메인(main)
|   |   ├── 등록(input)
|   |   ├── 상세(detail)
|   |   ├── 수정(modify)
|   |   └── 인수인계
|   ├── 가맹점주 관리(shopkeeper)/
|   |   ├── 메인(main)
|   |   ├── 등록(input)
|   |   ├── 상세(detail)
|   |   └── 수정(modify)
|   └── 탈퇴회원 관리(withdrawal)/
|       └── 탈퇴회원 메인(main)
├── 매장관리(manage/store)/
|   ├── QSC 관리(qsc)/
|   │   ├── 메인(main)-주석
|   │   ├── Quality 점검결과 (quality)-주석
|   │   ├── Service 점검결과 (service)-주석
|   │   └── Cleaness 점검결과 (cleaness)-주석
|   ├── 법규준수사항 관리(regulations)/
|   |   ├── 메인(main)-주석
|   |   └── 점검 결과 (detail)-주석
|   ├── 점주 상담 관리(advice)/
|   |   ├── 메인(main)-주석
|   |   └── 점검 결과(detail)-주석
|   ├── 점검 결과 관리(result)/
|   |   ├── 메인(main)-주석
|   |   └── 결과 리포트(detail)-주석
|   └── 항목 등록 관리(item)/
|       └── 메인(main)
├── 수익관리(manage/profit)/
|   ├── 비용 항목 관리(cost)/
|   |   └── 메인(main)
|   ├── 수익 현황 관리(condition)/
|   |   ├── 메인(main)
|   |   └── 상세(detail)
|   └── 수익 분석 관리(analysis)/
|       ├── 메인(main)
|       └── 상세(detail)
├── 소통 일정 관리(manage/participate)/
|   ├── 소통 관리(communication)/
|   |   ├── 메인(main)
|   |   ├── 리스트(list)
|   |   └── 상세(detail)
|   ├── VOC 관리(voc)/
|   |   ├── 메인(main)
|   |   ├── 리스트(list)
|   |   ├── 상세(detail)
|   |   └── 댓글 등록(register)
|   |   └── 글 답변(reply)
|   └── 일정 관리(schedule)/
|       ├── 메인(main)
|       ├── 달력(calendar)
|       └── 상세(detail)
├── 게시판 관리(manage/noticeboard)/
|   └── 공지사항 관리(notice)/
|       ├── 메인(main)
|       ├── 상세(detail)
|       ├── 등록(register)
|       └── 수정(modify)
├── 운영 관리(manage/operate)/
|   ├── 팝업 관리(popup)/
|   |   ├── 메인(main)
|   |   ├── 등록(register)
|   |   └── 수정(modify)
|   └── 관리자 관리(administrator)/
|       └── 메인(main)
└── 통계 관리(manage/statistics) /
    ├── 회원 현황 관리(member)/
    |   ├── 가맹본부 현황 메인(headquarters)
    |   |   ├── 일별(BarLineDayByDay)
    |   |   ├── 월별(BarLineMonth)
    |   |   ├── 시간대별(BarLineTime)
    |   |   └── 요일별(BarLineWeek)
    |   ├── 슈퍼바이저 현황 메인(supervisor)
    |   |   ├── 일별(BarLineDayByDay)
    |   |   ├── 월별(BarLineMonth)
    |   |   ├── 시간대별(BarLineTime)
    |   |   └── 요일별(BarLineWeek)
    |   ├── 가맹점 현황 메인(shopkeeper)
    |   |   ├── 일별(BarLineDayByDay)
    |   |   ├── 월별(BarLineMonth)
    |   |   ├── 시간대별(BarLineTime)
    |   |   └── 요일별(BarLineWeek)
    |   └── 전체 회원 현황 메인(general)
    |       ├── 일별(LineMultiDayByDay)
    |       ├── 월별(LineMultiMonth)
    |       ├── 성별(MultiGender)
    |       ├── 연령별(BarAge)
    |       └── 지역별(BarArea)
    └── 접속 현황 관리(access)/
        ├── 방문자 분석 메인(visitor)
        |   ├── 당일(LineVistorOneDay)
        |   ├── 일별(LineVistorDate)
        |   ├── 시간대별(LineVistorTime)
        |   ├── 요일별(LineVistorWeek)
        |   └── 월별(LineVistorMonth)
        ├── 방문자 환경 분석 메인(environment)
        |   ├── 운영체제(DonutSystem)
        |   └── 브라우저(DonutBrowser)
        └── 방문자 IP 분석 메인(ip)
```
