# jj-suite 지원 사이트

jj-suite iOS 앱 세 개 — Easy Web Image Collector · Easy NAS Photo Viewer · Easy NAS Download Manager — 의
개인정보 처리방침과 지원 페이지(GitHub Pages, Jekyll). https://yjinchoi.github.io/jj-suite-support/

## 정본은 이 저장소가 아니다

본문의 정본은 비공개 저장소 `jj-suite` 의 `AppStore/` 폴더다. 이 저장소의 페이지는 그것을 조립한 **사본**이다.

- 개인정보 처리방침 = `AppStore/_shared/PrivacyPolicy/<lang>.md` + `AppStore/jj-<app>/PrivacyPolicy-delta.md` 의 해당 언어 절
- 지원 = `AppStore/_shared/Support/<lang>.md` 에서 해당 없는 절을 지운 것 + `AppStore/jj-<app>/Support-delta.md`
- 조립 규칙은 `AppStore/README.md` §1.2 와 `AppStore/_shared/Support/ko.md` 말미의 조립표를 따른다.

**예외 — NAS Player(tvOS, `nasplayer-tv/`)** 는 jj-suite 가 아니라 비공개 저장소 `appletv-nas-player` 의 앱이고 `AppStore/` 정본이 없다.
이 저장소의 `nasplayer-tv/` · `en/nasplayer-tv/` 가 정본이다. 오픈소스(LGPL) 절의 서면 제의는 `nasplayer-relink` README 와 맞춘다.

문장을 고칠 일이 있으면 **`jj-suite` 의 `AppStore/` 를 먼저 고치고** 이 저장소를 다시 만든다.
여기서만 고치면 다음 조립 때 덮어써진다.

## 주소

| 앱 | 개인정보 처리방침 | 지원 |
|---|---|---|
| Easy Web Image Collector | `/webimage/privacy/` · `/en/webimage/privacy/` | `/webimage/support/` · `/en/webimage/support/` |
| Easy NAS Photo Viewer | `/nasphoto/privacy/` · `/en/nasphoto/privacy/` | `/nasphoto/support/` · `/en/nasphoto/support/` |
| Easy NAS Download Manager | `/torrent/privacy/` · `/en/torrent/privacy/` | `/torrent/support/` · `/en/torrent/support/` |
| NAS Player (tvOS) | `/nasplayer-tv/privacy/` · `/en/nasplayer-tv/privacy/` | `/nasplayer-tv/support/` · `/en/nasplayer-tv/support/` |

모든 주소는 `https://yjinchoi.github.io/jj-suite-support` 아래에 있다.
