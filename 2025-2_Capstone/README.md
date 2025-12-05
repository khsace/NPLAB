# MFC 프로그램 사용 설명서
<p align="center">
  <img src="./New-logo.png" alt="NPLAB" width="400">
</p>

## 1. 배경
- 본 과제는 25-2 국립금오공과대학교 RISE사업단 주최하 기업연계형 캡스톤 프로젝트 일환으로써, LIG-Nex1과 NPLAB 연구실의 협력으로 진행됨
- 작품명: MFC 기반 IMU 유효수명 예측 모니터링 프로그램 설계
- 팀명: 라이프내비
- 학과명: 컴퓨터공학과
- 지도교수: 김태형
- 참여학생: 김형석, 배진우, 박지호, 이상민, 유진하, 허준형
- 작성 일시: 2025년 12월 5일

<br/>
<br/>

## 2. 프로젝트 설명
- 무인기 탑재 IMU의 다시점 점검 데이터를 가지고 항법 드리프트 열화 모델을 설계
- 잔여유효수명(RUL, Remaining Useful Life)를 확률로 예측

### 2-1. 기본적인 동작
<p align="center">
  <img src="./RUL_예측흐름도.png" width="1200">
</p>

- 추출된 잠재벡터로 시험용 IMU와 유사한 훈련 데이터셋 수집
- A시점에서 B시점 항법 드리프트를 예측하는 베이지안 모델 학습
- 시험용 IMU의 B시점 드리프트 예측 분포 획득
- A시점 훈련셋의 드리프트 분포와 B시점 예측 분포의 평균 분산을 선형 회귀
- Month-Drift 그래프에서 드리프트가 불량 임계값을 넘는 지점을 수명이 0인 지점이라고 가정
- 시험용 IMU의 A시점과 RUL=0 지점 차이를 계산
- RUL 획득

### 2-2. 유효성 검증
- 위에서 계산한 RUL 열화 모델을 가지고 수명을 계산한 결과, 평균 200~300개월, 오차범위 10개월 이내로 예측되는 것을 확인
- 소량의 다시점 데이터를 활용하여 Month가 커질수록 분산이 커지는 현상이 존재

자세한 베이지안 모델 설계 내용은 결과보고서를 참고하시길 바랍니다.

<br/>
<br/>

## 3. 주요 기능 설명
- **회원가입**:
  - 회원가입 시 DB에 유저정보가 등록됩니다.

<br/>
<br/>

## 4. 프로젝트 구조
```plaintext
project/
├── public/
│   ├── index.html           # HTML 템플릿 파일
│   └── favicon.ico          # 아이콘 파일
├── src/
│   ├── assets/              # 이미지, 폰트 등 정적 파일
│   ├── components/          # 재사용 가능한 UI 컴포넌트
│   ├── hooks/               # 커스텀 훅 모음
│   ├── pages/               # 각 페이지별 컴포넌트
│   ├── App.js               # 메인 애플리케이션 컴포넌트
│   ├── index.js             # 엔트리 포인트 파일
│   ├── index.css            # 전역 css 파일
│   ├── firebaseConfig.js    # firebase 인스턴스 초기화 파일
│   package-lock.json    # 정확한 종속성 버전이 기록된 파일로, 일관된 빌드를 보장
│   package.json         # 프로젝트 종속성 및 스크립트 정의
├── .gitignore               # Git 무시 파일 목록
└── README.md                # 프로젝트 개요 및 사용법
```

<br/>
<br/>

<img width="100%" alt="코드 컨벤션" src="https://github.com/user-attachments/assets/0dc218c0-369f-45d2-8c6d-cdedc81169b4">
<img width="100%" alt="깃플로우" src="https://github.com/user-attachments/assets/2a4d1332-acc2-4292-9815-d122f5aea77c">
