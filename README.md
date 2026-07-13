# 💕 또요니 팬 페이지 (doldolcouple)

또요니를 위한 데일리 팬 페이지예요. 매일 들어와서 오늘의 운세·날씨·포춘쿠키·오늘의 사진을 즐길 수 있어요.

## 📄 페이지 구성

- **프로필 헤더** — 프로필 사진, 애칭, "함께한 지 D+n일", 다가오는 기념일(가장 가까운 날)
- **🍀 오늘의 운세** — 행운색 · 행운 아이템 · 오늘의 응원메시지 (매일 자정에 자동으로 바뀜)
- **🎡 뭐하지 룰렛** — 버튼을 누르면 오늘 뭐 할지 랜덤으로 뽑아줘요
- **🌡️ 사랑 온도계** — 하트를 누를 때마다 온도가 차오르고, 100°C가 되면 폭죽! (브라우저에 저장돼요)
- **⛅ 이번주 날씨** — 서울 기준 7일 예보
- **🥠 포춘쿠키** — 쿠키를 깨서 오늘의 운세 한 줄 뽑기
- **📸 오늘의 사진** — 매일 한 장씩 자동으로 바뀌고, 버튼으로 슬라이드쇼처럼 넘겨볼 수 있어요

## ✏️ 내용 수정하는 법 (코드 몰라도 OK)

1. `index.html` 파일을 메모장이나 편집기로 열어요.
2. 맨 위 `<script id="config">` 영역에서 따옴표 `" "` 안의 글자만 바꿔요.
   - `name` — 이름/애칭
   - `subtitle` — 이름 밑 한 줄
   - `emoji` — 프로필 사진이 없을 때 보여줄 이모지
   - `profileImage` — 프로필 사진 경로 (`photos/profile.jpg`)
   - `anniversary` — 사귄 날 (`"2022-04-27"` 형식) → D+일수·기념일 자동 계산
   - `birthday` — 또요니 생일 (`"1999-08-15"` 형식). 넣으면 생일 D-day도 후보에 들어가요
   - `luckyColors` / `luckyItems` / `cheers` — 오늘의 운세에 나올 행운색·아이템·응원메시지 목록
   - `rouletteItems` — 룰렛에 나올 "뭐하지" 항목들
   - `weather` — 날씨 위치 (기본: 서울 좌표)
   - `fortunes` — 포춘쿠키 문구 목록
   - `gallery` — 사진 목록 (아래 참고)
3. 저장하고 `index.html`을 더블클릭하면 브라우저에서 바로 확인돼요.

## 📸 사진 추가하는 법

1. `photos` 폴더에 사진 파일을 넣어요. (예: `photos/데이트.jpg`)
2. `index.html`의 `gallery` 부분에 한 줄 추가:
   ```
   gallery: [
     { src: "photos/데이트.jpg", caption: "첫 데이트 🥰", tag: "데이트" },
   ],
   ```
3. 사진을 추가할수록 "오늘의 사진"에 매일 다른 사진이 떠요!
   - 프로필 사진은 `photos/profile.jpg` 로 저장하면 맨 위에 나와요.

## 🌐 웹으로 보기 (GitHub Pages)

이 저장소를 **공개(Public)**로 두고 **Settings → Pages → Deploy from a branch → main / root** 로 게시하면,
폰·PC 어디서든 링크로 열리는 주소가 생겨요:

```
https://julim0101.github.io/doldolcouple/
```

> 무료 플랜에서 게시하면 이 주소는 공개돼요(링크를 아는 사람은 접속 가능).
> 완전 비공개로 두고 싶으면 로컬에서 `index.html`을 더블클릭해서 보면 돼요.

## ✍️ 방명록 설정 (공유 방명록 · 파이어베이스 무료)

또요니가 남긴 글을 종욱님도 볼 수 있는 공유 방명록이에요. 딱 한 번만 설정하면 돼요.

1. **파이어베이스 프로젝트 만들기**
   [console.firebase.google.com](https://console.firebase.google.com) 접속 → **프로젝트 만들기** → 이름 입력(예: `doldolcouple`) → (애널리틱스는 꺼도 됨) → 생성.
2. **Realtime Database 만들기**
   왼쪽 메뉴 **빌드 → Realtime Database** → **데이터베이스 만들기** → 위치 선택 → **테스트 모드로 시작** → 사용 설정.
3. **규칙 열기** (Realtime Database → **규칙** 탭)에 아래를 붙여넣고 **게시**:
   ```json
   {
     "rules": {
       "guestbook": { ".read": true, ".write": true },
       "checkins":  { ".read": true, ".write": true },
       "wishlist":  { ".read": true, ".write": true },
       "capsules":  { ".read": true, ".write": true }
     }
   }
   ```
   (방명록·기분 체크인·위시리스트·타임캡슐이 모두 이 규칙을 씁니다.)
4. **웹 앱 등록해서 설정값 받기**
   프로젝트 개요(⚙️ 옆 홈) → **웹 아이콘 `</>`** 클릭 → 앱 닉네임 입력 → 등록 → 나오는 `firebaseConfig` 값(apiKey, authDomain, **databaseURL**, projectId 등)을 복사.
5. **설정값 붙여넣기**
   `index.html` 맨 위 설정의 `firebaseConfig` 안 따옴표에 그 값들을 붙여넣어요. → 저장 후 다시 업로드.

> ⚠️ 위 규칙은 링크를 아는 사람이면 방명록을 읽고 쓸 수 있어요(소규모 커플 페이지엔 보통 충분). 더 안전하게 하고 싶으면 알려주세요.

## 🏠 폰 홈 화면에 앱처럼 추가

Pages 링크를 폰 브라우저로 연 뒤:
- **아이폰(사파리)**: 공유 버튼 → **홈 화면에 추가**
- **안드로이드(크롬)**: ⋮ → **홈 화면에 추가**

아이콘은 `photos/icon.jpg`, 이름은 "또요니 💕"로 나와요.

## 📁 파일 구조

```
doldolcouple/
├── index.html      ← 페이지 본체 (여기만 편집)
├── manifest.json   ← 홈 화면 앱 정보 (아이콘/이름)
├── photos/         ← 사진 넣는 곳
│     ├── profile.jpg  = 맨 위 프로필 사진
│     └── icon.jpg     = 홈 화면 아이콘
└── README.md       ← 이 안내서
```
