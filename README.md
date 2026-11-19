# Shadowing Player

유튜브 영상(예: Hey Tablo)으로 영어 쉐도잉을 연습하는 웹앱입니다. 모바일에서도 쓸 수 있도록 PWA로 만듭니다.

## 구조

```
scripts/   로컬 Python 스크립트: YouTube URL → 자막 → 문장 단위 JSON
web/       정적 프론트엔드 (Vite + React + TypeScript): 플레이어 + 문장 리스트
```

- 자막은 **로컬에서** 받습니다. `youtube-transcript-api` 같은 방식은 클라우드 서버 IP에서 막히기 때문에 서버 없이 JSON 파일로 저장해 프론트에서 읽습니다.
- 재생은 YouTube IFrame Player API를 씁니다. 구간 반복은 `seekTo` + `getCurrentTime` 확인, 속도는 `setPlaybackRate`로 처리합니다.

문장 JSON 형식:

```json
[{ "start": 12.34, "end": 15.02, "text": "So what did you do this weekend?" }]
```

## MVP 일정

| 주차 | 범위 |
| --- | --- |
| 1주차 (~11/26) | `scripts/`: YouTube URL → 자막(yt-dlp, json3) → 문장 단위 JSON |
| 2주차 (11/26) | `web/`: IFrame 플레이어 + 문장 리스트 + 문장 반복 + 0.75x 재생 + 녹음/재생 |
| 3주차 (12/03) | 이번 주 에피소드로 직접 써보고 회고 |

## 이후에 해볼 것 (stretch)

- 내 녹음을 STT로 받아 원문과 비교하고, 빠진 단어 하이라이트
- 틀린 문장만 Notion으로 export

GDGoC CAU Weekly Meetup 26-2에서 AI를 활용해 만드는 프로젝트입니다.
