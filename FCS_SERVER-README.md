# FC Smart Platform 구축을 위한 시스템 개발

**소개 :** 프랜차이즈(가맹본부/가맹점), 소상공인 및 자영업자의 매장관리 및 교육을 위한 플랫폼 개발을 통해 프랜차이즈 가맹본부의 가맹점 관리 편의성 제공

## 사용 기술

### node
- [Node.js](https://nodejs.org/ko/) **12.16.2 LTS**
- [axios](https://www.npmjs.com/package/axios) **0.19.2**
- [bcrypt](https://www.npmjs.com/package/bcrypt) **4.0.1**
- [moment](https://www.npmjs.com/package/moment) **2.27.0**
- [request-ip](https://www.npmjs.com/package/request-ip) **2.1.3**
- [dotenv](https://www.npmjs.com/package/dotenv) **8.2.0**
- [express](https://www.npmjs.com/package/express) **4.16.1**
- [Firebase Admin](https://www.npmjs.com/package/firebase-admin) **8.12.1**
- [jsonwebtoken](https://www.npmjs.com/package/jsonwebtoken) **8.5.1**
- [mariadb](https://www.npmjs.com/package/mariadb) **2.3.1**
- [morgan](https://www.npmjs.com/package/morgan) **1.9.1**
- [nodemailer](https://www.npmjs.com/package/nodemailer) **6.4.6**
- [passport](https://www.npmjs.com/package/passport) **0.4.1**
- [passport-jwt](https://www.npmjs.com/package/passport-jwt) **4.0.0**
- [passport-local](https://www.npmjs.com/package/passport-local) **1.0.0**
- [typedi](https://www.npmjs.com/package/typedi) **0.8.0**
- [winston](https://www.npmjs.com/package/winston) **3.2.1**
- [winston-daily-rotate-file](https://www.npmjs.com/package/winston-daily-rotate-file) **4.4.2**
- [node-schedule](https://www.npmjs.com/package/node-schedule) **1.3.2**

### server
- [Dorker](https://www.docker.com/) **19.03.12**
- [docker-compose](https://www.docker.com/) **1.26.2**

### DB
- [MariaDB](https://mariadb.org/) **10.4.12**

## 참고 사이트

### Firebase push

- [공식 홈페이지](https://firebase.google.com/docs/cloud-messaging?hl=ko)

### 네이버 지도 API

- [공식홈페이지](https://www.ncloud.com/product/applicationService/maps)

### 폴더 구조

```text
FCS_SERVER
├── nginx
|   ├── build(웹페이지 빌드)
|   ├── cert.pem (ssl 관련 파일)
|   ├── key.pem (ssl 관련 파일)
|   ├── newChain.pem (ssl 관련 파일)
|   ├── nginx.conf (ssl 관련 파일)
|   └── SymantecDigiCert-Newchain.pem (ssl 관련 파일)
├── admin & user
|   ├── config( 메일발송, 인증(로그인), 로그 관련 소스 )
|   ├── models( 디비 접근 소스 )
|   ├── routes( 라우트 소스 )
|   ├── services ( 디비와 연결된 인터페이스 소스 )
|   └── utils ( 크론잡 소스 )
|   └── .env ( 설정 관련 파일 )
|   └── Dockerfile ( 이미지 관련 실행 파일 )
├── file ( 파일서버 )
|   └── routes ( 섬네일, 이미지,  공지사항 파일 제공 )
|       └── index.js
|       └── controllters.js
└── mariadb (디비서버)
    └── config
        └── my.cnf (mariadb 설정 파일)
        └── 2020-06-17.sql (aqueryTool 백업 쿼리)
        └── dump.sql (실제 디비 백업용 파일)
```

### API 구조

1. 관리자 admin

```text
route(main)/
├── v1(이용자 소스와 같음, 주석처리 됨)/ 
└── v2(v2)/
    ├── board.js (게시판 관리)/
    ├── book.js (수익 관리)/
    ├── member.js (회원 관리)/
    ├── operate.js (관리자 기능 관리)/
    ├── particepate.js (일정 관리)/
    ├── push.js (푸시메시지 관리)/
    ├── statistics.js (통계 관리)/
    ├── store.js (QSC 관리)/
    ├── user.js (로그인, 검증, 로그 기능 관리)/
    └── index.js(라우터 연결 파일)

```

2. 이용자 user

```text
route(main)/
├── v2(관리자 소스와 같음, 주석처리 됨)/ 
└── v1(v1)/
    ├── board.js (게시판 관리)/
    ├── book.js (수익 관리)/
    ├── member.js (회원 관리)/
    ├── operate.js (관리자 기능 관리)/
    ├── particepate.js (일정 관리)/
    ├── push.js (푸시메시지 관리)/
    ├── statistics.js (통계 관리)/
    ├── store.js (QSC 관리)/
    ├── user.js (로그인, 검증, 로그 기능 관리)/
    └── index.js(라우터 연결 파일)

```
3. 공통 서비스(주석은 admin참조)

```text
models(디비)/
└── mariadb.js (마리아디비)
services(서비스)/
├── authService.js (로그인 서비스)
├── boardService.js (게시판 서비스)
├── logService.js (로그 서비스) // 사용되지 않음.
├── mailService.js (메일 서비스)
├── operatorService.js (운영 서비스) qsc 리포트 난수 생성시 사용.
├── storeService.js (매장 검사, 수익관리 서비스)
├── userService.js (유저 서비스)
└── validateService.js (타입값 검증 서버)

```
