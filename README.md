# 솔브텍 홈페이지 (준비 중 페이지)

## 저장소 구조

```
index.html
content/
  literacy.json          디지털 문해 프로그램 상세 내용
assets/
  literacy/
    01-class.jpg
    02-kiosk.jpg
    intro.mp4
    intro-poster.jpg
```

대기열의 `[JOB 010] 디지털 문해 프로그램` 을 클릭하면 `content/literacy.json` 을
불러와 레이어에 그립니다. **HTML은 건드릴 필요 없이 JSON과 파일만 바꾸면 됩니다.**

## 내용 바꾸기

`content/literacy.json` 의 `blocks` 배열에 원하는 순서대로 쌓습니다.

| 블록 | 쓰는 법 |
|---|---|
| 문단 | `{"type":"text","value":"내용","lead":true}` — `lead`는 첫 문단 강조 |
| 목록 | `{"type":"list","title":"소제목","items":["항목1","항목2"]}` |
| 이미지 | `{"type":"image","src":"assets/literacy/01.jpg","alt":"설명","caption":"캡션"}` |
| 영상(파일) | `{"type":"video","src":"assets/literacy/intro.mp4","poster":"assets/literacy/intro-poster.jpg"}` |
| 영상(유튜브) | `{"type":"video","src":"https://youtu.be/영상ID","caption":"캡션"}` |

- 경로는 `index.html` 기준 상대경로입니다. `assets/...` 형태로 적으면 됩니다.
- 유튜브는 주소만 넣으면 자동으로 embed 로 바뀝니다.
- `value` 안에 `<b>`, `<br>` 같은 간단한 태그를 써도 그대로 반영됩니다.

## 다른 사업도 열고 싶을 때

1. `content/holdem.json` 처럼 파일을 하나 더 만듭니다.
2. `index.html` 의 `jobs` 배열에서 해당 줄 맨 뒤 칸에 키를 적습니다.

```js
["JOB 009","홀덤 RFID카드 방송 솔루션","RUNNING","","holdem"],
```

그 줄이 자동으로 클릭 가능해집니다.

## 확인 방법

`index.html` 을 더블클릭해서 열면 브라우저 보안 정책 때문에 JSON을 못 읽습니다.
아래 중 하나로 확인하세요.

- GitHub Pages 에 올린 주소로 접속 (실제 운영 환경)
- 로컬에서 `python3 -m http.server` 실행 후 `http://localhost:8000`

## 영상 용량 주의

GitHub 은 파일 하나당 100MB 제한이 있고, Pages 대역폭도 넉넉하지 않습니다.
긴 영상은 mp4 를 올리기보다 유튜브 링크를 쓰는 편이 안전합니다.
