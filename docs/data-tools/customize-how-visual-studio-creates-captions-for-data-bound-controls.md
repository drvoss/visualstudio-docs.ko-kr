---
title: 데이터 바인딩된 컨트롤에 대 한 캡션 사용자 지정
ms.date: 11/03/2017
ms.topic: conceptual
helpviewer_keywords:
- Label captions, Data Sources window
- smart captions
- captions, data-bound
- Data Sources Window, label captions
ms.assetid: 6d4d15f8-4d78-42fd-af64-779ae98d62c8
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 1745aef29da9fc8efd49789f0112c903128f6f74
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62567587"
---
# <a name="customize-how-visual-studio-creates-captions-for-data-bound-controls"></a>Visual Studio에서 데이터 바인딩된 컨트롤에 대한 캡션을 만드는 방식 사용자 지정

항목을 끌면 합니다 [데이터 소스 창](add-new-data-sources.md#data-sources-window) 을 디자이너에 특별 한 고려 사항 고려해 야 합니다: 캡션 레이블이 열 이름은 두 개의 좀 더 읽기 쉬운 문자열로 변경 하거나 더 많은 단어 것으로 발견 된 서로 연결 됩니다.

::: moniker range="vs-2017"

이러한 레이블을 설정 하 여 생성 하는 방법을 사용자 지정할 수 있습니다는 **SmartCaptionExpression**하십시오 **SmartCaptionReplacement**, 및 **SmartCaptionSuffix** 값 합니다 **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\15.0\Data 디자이너** 레지스트리 키입니다.

::: moniker-end

::: moniker range=">=vs-2019"

이러한 레이블을 설정 하 여 생성 하는 방법을 사용자 지정할 수 있습니다는 **SmartCaptionExpression**하십시오 **SmartCaptionReplacement**, 및 **SmartCaptionSuffix** 값 합니다 **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\16.0\Data 디자이너** 레지스트리 키입니다.

::: moniker-end

> [!NOTE]
> 이 레지스트리 키는 만들 때까지 존재 하지 않습니다.

값에 입력 된 정규 식에 의해 제어 됩니다 스마트 캡션 합니다 **SmartCaptionExpression** 값입니다. 추가 된 **데이터 디자이너** 레지스트리 키 재정의 캡션 레이블을 제어 하는 기본 일반 식입니다. 정규식에 대 한 자세한 내용은 참조 하세요. [Visual Studio에서 정규식을 사용 하 여](../ide/using-regular-expressions-in-visual-studio.md)입니다.

다음 표에서 캡션 레이블을 제어 하는 레지스트리 값을 설명 합니다.

|레지스트리 항목|설명|
|-------------------|-----------------|
|**SmartCaptionExpression**|패턴을 일치 하는 데는 정규식입니다.|
|**SmartCaptionReplacement**|형식을 일치 하는 모든 그룹을 표시 합니다 **SmartCaptionExpression**합니다.|
|**SmartCaptionSuffix**|캡션의 끝에 추가 하는 선택적 문자열.|

다음 표에서 이러한 레지스트리 값에 대 한 내부 기본 설정을 나열합니다.

|레지스트리 항목|기본값|설명|
|-------------------|-------------------|-----------------|
|**SmartCaptionExpression**|**(\\\p{Ll})(\\\p{Lu})&#124;_+**|대문자 또는 밑줄 뒤에 소문자 문자를 찾습니다.|
|**SmartCaptionReplacement**|**$1 $2**|**$1** 식의 첫 번째 괄호로 일치 하는 문자를 나타내는 하며 **$2** 두 번째 괄호로 일치 하는 문자를 나타냅니다. 첫 번째 일치 하는, 공백 하나 및 두 번째 일치 항목이 바뀝니다.|
|**SmartCaptionSuffix**|**:**|반환된 된 문자열에 추가 되는 문자를 나타냅니다. 예를 들어, 캡션이 `Company Name`, 접미사를 사용 하면 `Company Name:`|

> [!CAUTION]
> 레지스트리 편집기에서 작업을 수행 하는 경우에 매우 주의 해야 합니다. 편집 하기 전에 레지스트리를 백업 합니다. 레지스트리 편집기를 잘못 사용 하면 운영 체제를 다시 설치 해야 할 수 있는 심각한 문제가 발생할 수 있습니다. Microsoft은 레지스트리 편집기를 잘못 사용 하 여 발생 하는 문제를 해결할 수 있음을 보장 하지 않습니다. 레지스트리 편집기 사용에 따른 결과는 사용자의 책임입니다.
>
> 백업에 대 한 정보를 편집 하 고 레지스트리를 복원 참조 [고급 사용자에 대 한 Windows 레지스트리 정보](https://support.microsoft.com/help/256986/windows-registry-information-for-advanced-users)합니다.

## <a name="modify-the-smart-captioning-behavior-of-the-data-sources-window"></a>데이터 소스 창에서의 스마트 캡션 동작을 수정

1. 클릭 하 여 명령 창을 열고 **시작** 차례로 **실행**합니다.

2. 형식 `regedit` 에 **실행** 대화 상자를 클릭 **확인**합니다.

3. 확장 된 **HKEY_CURRENT_USER** > **소프트웨어** > **Microsoft** > **VisualStudio**노드.

::: moniker range="vs-2017"

4. 마우스 오른쪽 단추로 클릭 합니다 **15.0** 노드를 새로 만들고 **키** 라는 `Data Designers`합니다.

::: moniker-end

::: moniker range=">=vs-2019"

4. 마우스 오른쪽 단추로 클릭 합니다 **16.0** 노드를 새로 만들고 **키** 라는 `Data Designers`합니다.

::: moniker-end

5. 마우스 오른쪽 단추로 클릭 합니다 **데이터 디자이너** 노드를 만들고 세 개의 새 문자열 값:

    - `SmartCaptionExpression`
    - `SmartCaptionReplacement`
    - `SmartCaptionSuffix`

6. 마우스 오른쪽 단추로 클릭 합니다 **SmartCaptionExpression** 값을 선택 **수정**합니다.

7. 원하는 정규식을 입력 합니다 **데이터 원본** 기간을 합니다.

8. 마우스 오른쪽 단추로 클릭 합니다 **SmartCaptionReplacement** 값을 선택 **수정**합니다.

9. 대체 입력 정규식에서 일치 하는 패턴을 원하는 방식으로 형식이 지정 된 문자열입니다.

10. 마우스 오른쪽 단추로 클릭 합니다 **SmartCaptionSuffix** 값을 선택 **수정**합니다.

11. 캡션의 끝에 표시할 모든 문자를 입력 합니다.

    항목을 끌면 다음에 **데이터 원본** 창 캡션 레이블이 만들어집니다 제공 되는 새 레지스트리 값을 사용 합니다.

## <a name="turn-off-the-smart-captioning-feature"></a>스마트 캡션 기능 해제

1. 클릭 하 여 명령 창을 열고 **시작** 차례로 **실행**합니다.

2. 형식 `regedit` 에 **실행** 대화 상자를 클릭 **확인**합니다.

3. 확장 된 **HKEY_CURRENT_USER** > **소프트웨어** > **Microsoft** > **VisualStudio**노드.

::: moniker range="vs-2017"

4. 마우스 오른쪽 단추로 클릭 합니다 **15.0** 노드를 새로 만들고 **키** 라는 `Data Designers`합니다.

::: moniker-end

::: moniker range=">=vs-2019"

4. 마우스 오른쪽 단추로 클릭 합니다 **16.0** 노드를 새로 만들고 **키** 라는 `Data Designers`합니다.

::: moniker-end

5. 마우스 오른쪽 단추로 클릭 합니다 **데이터 디자이너** 노드를 만들고 세 개의 새 문자열 값:

    - `SmartCaptionExpression`
    - `SmartCaptionReplacement`
    - `SmartCaptionSuffix`

6. 마우스 오른쪽 단추로 클릭 합니다 **SmartCaptionExpression** 선택한 항목을 **수정**합니다.

7. 입력 `(.*)` 값입니다. 이 전체 문자열을 일치 합니다.

8. 마우스 오른쪽 단추로 클릭 합니다 **SmartCaptionReplacement** 선택한 항목을 **수정**합니다.

9. 입력 `$1` 값입니다. 이 문자열을 변경 되지 않은 상태로 남아 있도록 전체 문자열 일치 하는 값을 바꿉니다.

    항목을 끌면 다음에 **데이터 원본** 창 캡션 레이블이 수정 되지 않은 캡션을 사용 하 여 만들어집니다.

## <a name="see-also"></a>참고자료

- [Visual Studio에서 데이터에 컨트롤 바인딩](../data-tools/bind-controls-to-data-in-visual-studio.md)