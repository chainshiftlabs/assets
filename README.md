# assets

[planning](https://github.com/chainshiftlabs/planning) 레포의 무거운 파일을 두는 곳이다. 영상·녹음·3D·디자인 원본·압축 파일을 Git LFS 로 관리한다.

- planning 에는 md·코드·작은 이미지만 남기고, 무거운 원본은 여기에 둔다
- LFS 대상 확장자는 [.gitattributes](.gitattributes) 에 있다

## 처음 한 번

```bash
brew install git-lfs
git lfs install
git clone git@github.com:chainshiftlabs/assets.git
```

- `git lfs install` 을 안 하면 클론해도 파일 대신 수백 바이트짜리 포인터 텍스트만 받는다

## 폴더 구조

planning 과 같은 경로를 쓴다. planning 의 `project/f05-search-seoul-2026/연설녹음/` 에 있을 파일은 여기서도 `project/f05-search-seoul-2026/연설녹음/` 에 둔다.

- 어느 문서가 이 파일을 쓰는지 경로만 보고 찾을 수 있게 하려는 것이다

| 폴더 | 무엇을 두나 |
| --- | --- |
| `project/` · `mockups/` | 스펙·목업에 쓰는 영상·3D·원본 이미지 |
| `meetings/` | 회의 녹음(m4a) |
| `workspace/<이름>/` | 개인 작업 원본. 남의 폴더는 요청 없이 고치지 않는다 |
| `knowledge/` · `research/` · `roadmap/` · `docs/` · `incidents/` · `board/` | planning 같은 폴더의 문서가 쓰는 첨부 |
| `etc/_archive/` | 지난 버전 원본 |

- 빈 폴더는 `.gitkeep` 으로 자리만 잡아 두었다

## 지금 들어 있는 것

- `mockups/apps/mockup-hub/public/f19-cheto-flow/*-source.mp4` — 체토 모션 원본 38개 (57MB). planning 에는 없고 여기가 유일한 사본이다. 쓰는 법은 planning 의 `mockups/apps/mockup-hub/scripts/cheto-flow/README.md`

## 올릴 때

```bash
git lfs track "*.새확장자"   # .gitattributes 에 없는 확장자만
git add <파일>               # 파일 단위로
git commit -m "..."
git push
```

- **올리기 전에 `git lfs status` 로 LFS 로 잡혔는지 확인한다.** `.gitattributes` 에 없는 확장자는 일반 git 객체로 올라가고, 한 번 들어가면 히스토리를 재작성해야 뺄 수 있다
- 회의 녹음도 planning 과 같이 32kbps AAC 모노로 재인코딩해서 올린다
- 인사·평가·미공개 계약 발언이 담긴 녹음은 올리지 않는다

## 용량

LFS 저장 공간과 다운로드 대역폭은 조직 단위로 과금된다. 결제 화면은 Settings → Billing → Git LFS.

- 지운 파일도 LFS 저장 공간은 그대로 차지한다. 확실히 필요한 원본만 올린다
