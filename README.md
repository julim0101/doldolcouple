# 💕 서돌이 팬 페이지

여자친구를 위한 비공개 팬 페이지예요.

## ✏️ 내용 수정하는 법 (코드 몰라도 OK)

1. `index.html` 파일을 메모장이나 편집기로 열어요.
2. 맨 위 `<script id="config">` 영역에서 따옴표 `" "` 안의 글자만 바꿔요.
   - `name` — 이름/애칭
   - `subtitle` — 이름 밑 한 줄
   - `anniversary` — 사귄 날 (`"2024-01-01"` 형식) → D+며칠 자동 계산
   - `charms` — 매력 포인트 카드들
   - `timeline` — 추억 타임라인
   - `gallery` — 사진 (아래 참고)
   - `letter` — 손편지 내용
3. 저장하고 `index.html`을 더블클릭하면 브라우저에서 바로 확인돼요.

## 📸 사진 추가하는 법

1. `photos` 폴더에 사진 파일을 넣어요. (예: `photos/데이트.jpg`)
2. `index.html`의 `gallery` 부분에 한 줄씩 추가:
   ```
   gallery: [
     { src: "photos/데이트.jpg", caption: "첫 데이트 🥰" },
   ],
   ```

## 🔒 비공개로 관리하기 (GitHub)

이 폴더에서:

```bash
git init
git add .
git commit -m "우리 팬 페이지 시작 💕"
```

GitHub에서 **Private** 저장소를 새로 만든 뒤:

```bash
git remote add origin https://github.com/내계정/저장소이름.git
git branch -M main
git push -u origin main
```

> ⚠️ **주의:** 저장소를 Private으로 두면 코드는 안전하지만,
> GitHub Pages로 **게시**하면 무료 플랜에선 URL이 공개돼요.
> 완전 비공개로 보려면:
> - **로컬에서 보기** — 그냥 `index.html` 더블클릭 (가장 간단, 완전 비공개)
> - **GitHub Pro** — Private Pages 지원
> - **비밀번호 잠금** — 페이지에 암호 걸기 (원하시면 추가해드릴게요)

## 📁 파일 구조

```
서돌이/
├── index.html      ← 페이지 본체 (여기만 편집)
├── photos/         ← 사진 넣는 곳
└── README.md       ← 이 안내서
```
