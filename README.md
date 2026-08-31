# 字源 — 한자 분해·부수 뜻 사전

한자 입력 시 구성 요소 분해, 부수 뜻(한국어), 음훈·JLPT 정보까지 한번에 보여주는 웹앱임. 핵심 기능은 완전 오프라인으로 동작함.

## 사용 방법

브라우저로 `index.html` 열면 바로 동작함.

GitHub Pages 배포 시 접속 주소: `https://bernardchoi.github.io/jlpt_study/`

## 기능

- 한자 입력 → 구성 요소(부수) 분해 트리, 뜻·음훈·JLPT 등급·획수 표시
- JLPT 등급별(N5~N1) 한자 찾아보기
- 즐겨찾기(북마크) — 브라우저 `localStorage`에 저장
- 예문·단어 — 검색한 한자가 포함된 상용 어휘 예시
- 학습 모드(퀴즈) — 즐겨찾기·JLPT 등급 범위로 뜻 맞히기 4지선다
- 사진으로 한자 찾기 — 교재 사진을 올려 한자 한 글자를 크롭해 인식(OCR)

## 오프라인 동작 범위

검색·분해·JLPT 찾아보기·즐겨찾기·예문·퀴즈는 모두 페이지에 내장된 데이터만 사용하며 완전 오프라인으로 동작함(외부 서버·API 연결 없음).

**예외:** "사진으로 한자 찾기" 기능은 [Tesseract.js](https://github.com/naptha/tesseract.js) 기반 OCR을 브라우저 안(WebAssembly)에서 실행함. 최초로 이 기능을 사용할 때만 인식 엔진과 일본어 인식 모델(약 10~15MB)을 CDN(jsdelivr)에서 내려받으며, 이후엔 브라우저 캐시로 재사용됨. 이 과정에서도 **사진 자체는 서버로 전송되지 않고 브라우저 안에서만 처리됨.**

## 데이터 범위

- 분해 구조(IDS): 상용·교육한자 중심 약 3,400자 수록
- 뜻·음훈: KANJIDIC 기반 데이터 수록, 한국어로 번역(약 5,300개 어구 사전 내장, 일부 문맥 오역 가능성 있음)
- 부수 214자 한국어 훈음: 자체 정리
- 예문·단어: 상용 어휘 약 180개 자체 정리

## 출처

- 분해 구조: [CHISE / cjkvi-ids](https://github.com/cjkvi/cjkvi-ids) 프로젝트
- 한자 뜻·음훈: [davidluzgouveia/kanji-data](https://github.com/davidluzgouveia/kanji-data) (KANJIDIC 기반)
- 사진 한자 인식: [Tesseract.js](https://github.com/naptha/tesseract.js)
