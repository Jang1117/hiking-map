# 등산 지도 (hiking-map)

전국 명산 지도 + 산 추천 + GPS 등산 기록 웹앱

## 구성
- `index.html` — 앱 본체
- `data.js` — 산 데이터 299곳 (100대명산 + 유명산 199곳, 도립공원 19곳 포함)

## 카카오 앱키 설정
1. https://developers.kakao.com → 내 애플리케이션 → JavaScript 키 발급
2. `index.html` 상단의 `KAKAO_APP_KEY`에 입력
3. 카카오 개발자 콘솔 → 플랫폼 → Web → 사이트 도메인에 배포 주소 등록

## 기록 서버 저장 (Supabase, 선택)
1. https://supabase.com → 프로젝트 생성
2. SQL Editor에서 실행:
```sql
create table hiking_records (
  id text primary key, device_id text not null, name text not null,
  date text not null, mountain text, memo text,
  distance double precision default 0, duration integer default 0,
  gain double precision default 0, points jsonb,
  updated_at timestamptz default now()
);
alter table hiking_records enable row level security;
create policy "public all" on hiking_records
  for all using (true) with check (true);
```
3. `index.html` 상단의 `SUPABASE_URL`, `SUPABASE_ANON_KEY`(Publishable key)에 입력

## GitHub Pages
Settings → Pages → Deploy from a branch → main → `https://Jang1117.github.io/hiking-map/`

## 기능
- 지도: 산 마커·클러스터, 검색, 필터(100대명산/국립공원/도립공원/초보/지역/계절)
- 발견: 조건부 랜덤 산 추천, 계절 추천, 등정 진행률
- 기록: GPS 추적, 거리·시간·상승고도, GPX 내보내기, 자동 등정 체크, Supabase 서버 동기화
