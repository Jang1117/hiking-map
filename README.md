# 등산 지도 (hiking-map)

전국 100대 명산 지도 + 산 추천 + GPS 등산 기록 웹앱 (단일 HTML 파일)

## 구성
- `index.html` — 앱 본체 (산 데이터 100개 내장, 외부 의존성은 카카오맵 SDK만)

## 카카오 앱키 설정
1. https://developers.kakao.com → 내 애플리케이션 → 앱 생성
2. JavaScript 키 발급
3. `index.html` 상단의 `KAKAO_APP_KEY = "여기에_카카오_앱키_입력"` 부분에 키 입력
4. 카카오 개발자 콘솔 → 플랫폼 → Web → 사이트 도메인에 배포 주소 등록
   (예: `https://Jang1117.github.io`)

## GitHub Pages로 열기
1. 저장소 Settings → Pages → Source: Deploy from a branch → Branch: main → Save
2. `https://Jang1117.github.io/hiking-map/` 접속
3. GPS 추적은 HTTPS에서만 동작 (Pages 주소에서는 정상 동작)

## 기능
- 지도: 100대 명산 마커·클러스터, 검색, 필터(100대명산/국립공원/초보/지역/계절)
- 발견: 조건부 랜덤 산 추천, 계절 추천, 등정 진행률
- 기록: GPS 추적(시작/일시정지/종료), 거리·시간·상승고도, GPX 내보내기, 자동 등정 체크

## 데이터
- 산림청 100대 명산 목록 기반 (난이도는 추정치, 일부 좌표는 근사치)
