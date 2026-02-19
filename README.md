<div align="center">

![header](https://capsule-render.vercel.app/api?type=waving&color=0:1a1a2e,100:16213e&height=250&section=header&text=Ready%20or%20Not&fontSize=70&fontColor=e94560&fontAlignY=35&desc=Unofficial%20Korean%20Patch%20%F0%9F%87%B0%F0%9F%87%B7&descSize=22&descAlignY=55&animation=fadeIn)
<br>
[![Total Downloads](https://img.shields.io/github/downloads/Junh2x/Ready-or-Not-Korean-Patch/total?style=for-the-badge&logo=github&label=Total%20Downloads&labelColor=111827&color=2563eb)](https://tooomm.github.io/github-release-stats/?username=Junh2x&repository=Ready-or-Not-Korean-Patch)
<br>
<br>

[**다운로드**](https://github.com/Junh2x/Ready-or-Not-Korean-Patch/releases) | [**패치 노트**](https://github.com/Junh2x/Ready-or-Not-Korean-Patch/releases) | [**오류 제보**](https://docs.google.com/forms/d/e/1FAIpQLScaUi2sWcu3M973bb7nG7NqEid35ohaTijuy1Ly6Sx3946xEg/viewform?usp=sf_link) | [**버전별 통계**](https://tooomm.github.io/github-release-stats/?username=Junh2x&repository=Ready-or-Not-Korean-Patch)



</div>

---

## 개요

**Ready or Not**의 비공식 유저 한글 패치입니다.  
한국어를 지원하지 않아 게임 플레이에 불편을 겪는 한국 유저들을 위해 제작하였습니다.

개발사의 정식 한국어 지원이 될 때까지, 유저들이 사용할 수 있는 유의미한 한글 패치를 제작하는 것이 목표입니다.  
해결되지 않은 언어 현지화 관련 버그를 수정하고, 공식 번역 40% + 기계 번역 60%를 적용하였습니다.

번역을 도와주신 번역가와 익명 유저분들께 다시 한번 감사드립니다. 😊 <br>
기존 배포되었던 VO 자막 한글패치를 통합하였습니다. 허락해주신 제작자님께 감사드립니다.

</br>

## 작동 방식

이 패치는 Unreal Engine 4의 로컬라이제이션 시스템을 활용하여 게임 내 텍스트들을 한국어로 교체합니다.

```
[Game .pak 추출] → [.locres 파일 디코딩] → [번역 작업] → [.locres 재인코딩] → [.pak 리패키징]
```

| 단계 | 설명 | 도구 |
|------|------|------|
| 추출 | 게임의 `.pak` 아카이브에서 로컬라이제이션 에셋 추출 | [FModel](https://github.com/4sval/FModel) |
| 디코딩 | UE4 `.locres` 바이너리를 편집 가능한 `Key=Value` 텍스트로 변환 | [UE4localizationsTool](https://github.com/amrshaheen61/UE4LocalizationsTool) |
| 번역 | 영문 텍스트를 한국어로 번역 (AI + 수작업) | [DeepL API](https://www.deepl.com/api), [GPT-4 API](https://platform.openai.com/docs/models/gpt-4) |
| 병합 | 기존 공식 한국어 번역과 신규 번역 데이터를 키 매칭으로 병합 | Python |
| 인코딩 | 번역된 텍스트를 `.locres` 바이너리로 재변환 | [UE4localizationsTool](https://github.com/amrshaheen61/UE4LocalizationsTool) |
| 패키징 | 최종 `.pak` 파일로 리패키징하여 게임에 적용 | [UnrealPak](https://github.com/UnrealPak-tool/UnrealPak-tool) |

</br>

## 설치

1. [**최신 릴리즈**](https://github.com/Junh2x/Ready-or-Not-Korean-Patch/releases)에서 `RoN-korean-patch.zip`을 다운로드합니다.
2. 압축 해제 후, `.pak` 파일을 아래 경로에 붙여넣기합니다.
   ```
   Ready Or Not/ReadyOrNot/Content/Paks/
   ```
3. **(선택)** 자막 한글패치를 적용하지 않으신 경우, `VO.zip`을 다운로드합니다.
   - `VO` 폴더를 게임의 `Content` 폴더에 붙여넣기(덮어씌우기)합니다.
4. 게임을 실행합니다.
5. **옵션 > 언어**를 **영어(English)**로 설정 후 재시작합니다.
   - **텍스트 언어**, **오디오 > 자막 언어** 모두 변경해주세요.

</br>

## 안내

- 기계 번역은 DeepL, GPT-4 API를 사용하였습니다.
- AI 번역 서비스를 이용하였으므로, 오역이 있을 수 있습니다.
- 부자연스러운 부분이 많으므로 지속적으로 업데이트할 예정입니다.
- 수동 작업이 필요한 경우가 많아 일반적인 게임에 비해 현지화 작업 시간이 더 소요됩니다.

> **기술적으로 해결해야 할 문제가 아직 남아있습니다.**
> 언리얼 엔진, 개발 관련 지식이 있으시다면 [제보 링크](https://docs.google.com/forms/d/e/1FAIpQLScaUi2sWcu3M973bb7nG7NqEid35ohaTijuy1Ly6Sx3946xEg/viewform?usp=sf_link)를 통해 연락주세요 :)

</br>

## 자주묻는 질문

**Q. 한국어 > 영어 변경 시 다른 언어가 선택됩니다.**
> Ready or Not 게임 자체 버그로 인해 언어 변경 시 다른 언어가 선택되는 경우가 가끔 발생합니다. 재시도하시면 해결됩니다.

**Q. 음성 및 자막이 나오지 않습니다.**
> 게임 내 `VO` 폴더 삭제 → 스팀 무결성 검사 → 패치 재적용 (덮어씌우기)

---

