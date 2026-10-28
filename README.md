# 보카데이 (VocaDay)

해커스 토플 보카 30일(1,701단어)을 플래시카드로 공부하는 개인용 웹앱입니다.
파일 하나(`index.html`)로 동작하고, 서버나 빌드 과정이 필요 없습니다.

- 카드 앞면: 그림(이모지 장면), 단어, 품사, 발음 기호, 유의어
- 카드 뒷면: 뜻·예문, 🌱 어원(접두사·어근·접미사 분해, 같은 어근 단어), 💡 출제 포인트
- 탭(전체 · ✓ 외움 · ✕ 모름), 자동 재생(단어 → 뜻 → 예문 음성), 스펠링 게임, 단어장·검색
- 음성: Day별 MP3 파일(`audio/g01.mp3` ~ `g30.mp3`)

## GitHub Pages에 올리기

Mac 터미널에서 이 폴더로 이동해 커밋합니다.

```bash
cd ~/Documents/vocaday
git init -b main
git add .
git commit -m "보카데이 v61"
```

github.com에서 빈 저장소(`vocaday`, README 추가 없이)를 만든 뒤 push합니다.
`<아이디>`는 본인의 GitHub 아이디로 바꿉니다.

```bash
git remote add origin https://github.com/<아이디>/vocaday.git
git push -u origin main
```

GitHub CLI(`gh`)가 있으면 저장소 생성과 push를 한 번에 할 수 있습니다.

```bash
gh repo create vocaday --public --source . --push
```

마지막으로 저장소 **Settings → Pages**에서 *Deploy from a branch*, 브랜치 `main`, 폴더 `/ (root)`를 고르고 저장합니다.
1~2분 뒤 `https://<아이디>.github.io/vocaday/` 에서 열립니다.

## 폰에 설치하기

- **아이폰**: Safari로 위 주소를 열고 공유 버튼 → **홈 화면에 추가**
- **안드로이드**: Chrome으로 열고 메뉴 → **홈 화면에 추가**(또는 *앱 설치*)

홈 화면 아이콘으로 열면 주소창 없이 전체 화면으로 열립니다.

## 진행 기록

- 이 버전은 외움/모름 표시를 **그 기기의 브라우저에만** 저장합니다. Claude 버전처럼 PC와 폰이 자동으로 동기화되지는 않습니다.
- 기기 사이에 옮기거나 백업하려면 ⚙️ 설정 → **💾 진행 기록 옮기기 · 백업**에서 코드를 복사해, 다른 기기의 같은 화면에 붙여넣습니다(파일로 저장·불러오기도 됩니다).
- Claude 앱 버전(v61 이상)에도 같은 화면이 있어서, 지금까지의 기록을 이쪽으로 옮길 수 있습니다.
- 브라우저의 사이트 데이터를 지우면 기록도 지워지니, 가끔 파일로 백업해 두세요.

## 주의

- 단어·뜻·예문은 해커스 토플 보카 교재 내용입니다. 공개 저장소의 GitHub Pages 주소는 주소를 아는 사람 누구나 열 수 있으니 주소를 공유하지 마세요. 검색엔진 노출은 `robots.txt`와 `noindex`로 막아 두었습니다.
- 저장소를 비공개로 두고 싶다면 GitHub Pro(유료)에서 비공개 저장소로 Pages를 쓰거나, 비공개 저장소를 무료로 배포할 수 있는 Cloudflare Pages나 Netlify에 연결하면 됩니다(설정만 다르고 파일은 그대로 씁니다).
- 오프라인에서도 앱 화면은 열리지만(서비스 워커), 음성은 인터넷이 있어야 나옵니다.

## 파일 구성

| 경로 | 내용 |
| --- | --- |
| `index.html` | 앱 전체(데이터·그림·어원·코드 포함) |
| `audio/gNN.mp3` | Day별 음성(단어·뜻·예문), 약 3.3MB씩 |
| `manifest.webmanifest`, `icons/` | 홈 화면 설치용 이름·아이콘 |
| `sw.js` | 오프라인용 앱 화면 캐시 |
| `robots.txt`, `.nojekyll` | 검색 노출 차단, Pages 설정 |

## 업데이트

새 버전의 `index.html`(필요하면 `sw.js`도)을 덮어쓴 뒤 커밋하고 push하면 몇 분 안에 반영됩니다.

```bash
git add . && git commit -m "보카데이 업데이트" && git push
```
