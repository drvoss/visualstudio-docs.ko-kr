---
title: 마법사 (합니다. Vsz) 파일 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- .vsz files
- vsz files
- wizards, files
ms.assetid: 72e1d0f3-eef1-455e-b803-96827f030f50
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b4bbd69bc92ee96fcf93749aa6f700ad76ff72c8
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66309726"
---
# <a name="wizard-vsz-file"></a>마법사(.Vsz) 파일

통합된 개발 환경 (IDE) 마법사를 시작 하도록.vsz 파일을 사용 합니다. 이러한.vsz 파일 IDE를 호출 하는 마법사를 결정 하는 데 사용 하는 정보와 마법사 전달할 정보를 포함 합니다.

.Vsz 파일을 사용 하면 섹션이 없습니다.이 있는.ini 서식 있는 텍스트 파일의 버전이 있습니다. IDE에 알려진 정보 파일의 시작 부분에 저장 됩니다. 이 IDE를 호출 하는 마법사 및 IDE에 전달할.vsz 파일에 있는 매개 변수 간의 링크를 제공 합니다. 파일의 나머지 마법사 관련 되어 있으며 IDE에 의해 수집 되 고 특정 마법사에 전달 된 매개 변수를 제공 합니다.

다음 예제에서는.vsz 파일의 내용을 보여 줍니다.

```
VSWizard 8.0
Wizard=VsWizard.CBlankSiteWizard -or- {123-1234556-123334}
Param="WIZARDNAME = Wizard One"
Param="WIZARDUI = FALSE"
```

다음은.vsz 파일의 일부입니다.

|파트|설명|
|----------|-----------------|
|VSWizard|파일의 첫 번째 매개 변수는 템플릿 파일 형식의 버전입니다. 이 버전 번호는 6.0, 7.0, 7.1 또는 8.0 이어야 합니다. 다른 숫자를 시작할 수 없습니다 및 잘못 된 형식 오류가 발생 합니다.|
|마법사|이 필드에는 OLE의 ProgID 마법사 또는 IDE에서 공동으로 만들어집니다 되는 마법사의 CLSID의 GUID 문자열 표현을 포함 합니다.|
|Param|이러한 구성 요소는 선택 사항입니다. 필요한 개수 만큼 추가할 수 있습니다.|

매개 변수를 설정 하 여.vsz 파일 마법사 추가 사용자 지정 매개 변수를 전달 합니다. 각 값은 마법사에서 variant의 배열 문자열 요소로 전달 됩니다. 자세한 내용은 [사용자 지정 매개 변수](../../extensibility/internals/custom-parameters.md)합니다.

.Vsz 파일에 기본 로캘 ID를 추가 하려면 지정 `FALLBACK_LCID`= xxxx, 여기서 xxxx는 로캘 ID, 영어에 대 한 예를 들어 1033입니다. 때 `FALLBACK_LCID` 매개 변수를 정의 현재 ID를 찾을 수 없으면 마법사에서 제공 된 대체 (fallback) 로캘 ID를 사용 합니다.

## <a name="see-also"></a>참고자료

- [사용자 지정 매개 변수](../../extensibility/internals/custom-parameters.md)
- [마법사](../../extensibility/internals/wizards.md)
- [템플릿 디렉터리 설명(.Vsdir) 파일](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)