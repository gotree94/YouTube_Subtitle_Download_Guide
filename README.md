# 유튜브에서 자막 파일만 다운로드하기 (yt-dlp)

유튜브에서 영상 없이 자막 파일만 다운로드하려면 [`yt-dlp`](https://github.com/yt-dlp/yt-dlp)를 사용할 수 있습니다.

## 1. SRT 형식으로 한국어 자막 다운로드 (권장)

```bash
yt-dlp --skip-download --write-subs --sub-langs ko --convert-subs srt "https://youtu.be/VIDEO_ID"
```

**옵션 설명**

- `--skip-download` : 영상은 다운로드하지 않고 자막만 저장합니다.
- `--write-subs` : 자막 파일을 다운로드합니다.
- `--sub-langs ko` : 한국어(`ko`) 자막만 다운로드합니다.
- `--convert-subs srt` : 다운로드된 `.vtt` 자막을 `.srt` 형식으로 변환합니다.

> 영상에 한국어 자막이 제공되지 않으면 다운로드할 수 없습니다.

## 2. ffmpeg 오류 해결 (`ffmpeg not found`)

`.srt`로 변환할 때 `ERROR: Preprocessing: ffmpeg not found.` 오류가 발생하면 ffmpeg이 설치되어 있지 않기 때문입니다.

### Windows에서 ffmpeg 설치

아래 명령어 중 하나를 사용해서 설치할 수 있습니다.

| 패키지 매니저 | 명령어 |
|---|---|
| **winget** | `winget install Gyan.FFmpeg` |
| **scoop** | `scoop install ffmpeg` |
| **chocolatey** | `choco install ffmpeg` |

설치 완료 후 **터미널(Command Prompt/PowerShell)을 재시작**한 뒤, 위 1번 명령어를 다시 실행하면 `.srt` 파일이 정상적으로 다운로드됩니다.

## 3. ffmpeg 없이 VTT 형식으로 다운로드 (대안)

ffmpeg을 설치하지 않고 자막만 받고 싶다면 `--convert-subs srt` 옵션을 제거하면 됩니다.

```bash
yt-dlp --skip-download --write-subs --sub-langs ko "https://youtu.be/VIDEO_ID"
```
이 경우 `*.ko.vtt` 파일로 다운로드되며, VLC, PotPlayer 등 대부분의 플레이어에서 바로 사용할 수 있습니다.

* 영문 자막을 다운로드 받을때

```
yt-dlp --skip-download --write-auto-subs --sub-langs en "https://youtu.be/M5KOgtk9VfI"
```

## 주의사항

- YouTube 이용약관과 저작권을 반드시 준수해야 합니다.
- 다운로드한 자막은 개인 용도 이외의 목적으로 사용하지 마시기 바랍니다.
