# 솔브텍 홈페이지 (준비 중 페이지)

## 저장소 구조

```
index.html              대기열이 있는 메인 페이지
detail.css              상세 내용 공통 스타일
literacy/
  index.html            디지털 문해 프로그램 내용
  assets/
    01-class.jpg
    02-kiosk.jpg
    03-guide.jpg
    intro.mp4
    intro-poster.jpg
```

대기열의 `[JOB 010] 디지털 문해 프로그램` 을 클릭하면 `literacy/index.html` 을
불러와 팝업에 띄웁니다. 같은 파일을 주소로 직접 열어도 (`.../literacy/`)
정상적인 페이지로 보입니다. 나중에 상세 페이지로 그대로 쓰시면 됩니다.

## 내용 바꾸기

`literacy/index.html` 의 `<article class="detail">` 안쪽만 고치면 됩니다.
팝업은 이 `article` 안쪽만 뽑아 쓰기 때문에, 바깥의 `<head>` 나 `<body>` 는
직접 접속할 때만 쓰입니다.

쓸 수 있는 조각들:

```html
<!-- 글은 읽기 좋은 폭까지만 -->
<div class="col">
  <p class="status">RUNNING · 2026</p>
  <h2>제목</h2>
  <ul class="tags"><li>태그</li></ul>
  <p class="lead">첫 문단</p>
  <p>본문</p>
  <h3>소제목</h3>
  <ul class="points"><li>항목</li></ul>
</div>

<!-- 사진은 col 밖에 두면 넓게 나옵니다 -->
<figure>
  <img src="assets/01-class.jpg" alt="설명" loading="lazy">
  <figcaption>캡션</figcaption>
</figure>

<!-- 사진 두 장 나란히 -->
<div class="grid2">
  <figure>...</figure>
  <figure>...</figure>
</div>

<!-- 영상 (파일) -->
<figure>
  <div class="ratio">
    <video controls playsinline preload="metadata" poster="assets/intro-poster.jpg">
      <source src="assets/intro.mp4" type="video/mp4">
    </video>
  </div>
  <figcaption>캡션</figcaption>
</figure>

<!-- 영상 (유튜브) -->
<div class="ratio">
  <iframe src="https://www.youtube-nocookie.com/embed/영상ID"
          title="소개 영상" allowfullscreen></iframe>
</div>

<!-- 문의 버튼 -->
<div class="cta">
  <a href="mailto:securecasino@gmail.com">문의하기</a>
  <small>보통 하루 안에 회신드립니다.</small>
</div>
```

이미지 경로는 **그 폴더 기준**으로 적으면 됩니다 (`assets/01.jpg`).
팝업으로 불러올 때 자동으로 `literacy/assets/01.jpg` 로 고쳐집니다.

## 다른 사업도 열고 싶을 때

1. 폴더를 만들고 `literacy/index.html` 을 복사해 내용을 바꿉니다.
   예: `holdem/index.html`
2. `index.html` 의 `jobs` 배열에서 해당 줄 맨 뒤 칸에 폴더 이름을 적습니다.

```js
["JOB 009","홀덤 RFID카드 방송 솔루션","RUNNING","","holdem"],
```

그 줄이 자동으로 클릭 가능해집니다.

## 확인 방법

`index.html` 을 더블클릭해서 열면 브라우저 보안 정책 때문에 다른 파일을 못 읽습니다.
아래 중 하나로 확인하세요.

- GitHub Pages 에 올린 주소로 접속 (실제 운영 환경)
- 로컬에서 `python3 -m http.server` 실행 후 `http://localhost:8000`

## 영상 용량 주의

GitHub 은 파일 하나당 100MB 제한이 있고, Pages 대역폭도 넉넉하지 않습니다.
긴 영상은 mp4 를 올리기보다 유튜브 링크를 쓰는 편이 안전합니다.
