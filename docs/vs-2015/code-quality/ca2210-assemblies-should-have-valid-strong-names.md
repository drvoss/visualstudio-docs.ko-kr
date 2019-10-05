---
title: 'CA2210: 어셈블리에는 올바른 강력한 이름을 사용 해야 합니다. | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- AssembliesShouldHaveValidStrongNames
- CA2210
helpviewer_keywords:
- AssembliesShouldHaveValidStrongNames
- CA2210
ms.assetid: 8ed33d1c-8ec6-4b47-a692-e22dc8693088
caps.latest.revision: 25
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: f94183c6051ed0c2603bbfe35484fabb83a2160f
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65697983"
---
# <a name="ca2210-assemblies-should-have-valid-strong-names"></a>CA2210: 어셈블리에는 올바른 강력한 이름을 사용해야 합니다.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|AssembliesShouldHaveValidStrongNames|
|CheckId|CA2210|
|범주|Microsoft.Design|
|변경 수준|주요 변경 아님|

## <a name="cause"></a>원인
 어셈블리에 강력한 이름의 서명 되지 강력한 이름을 확인할 수 없거나, 또는 강력한 이름을 컴퓨터의 현재 레지스트리 설정이 없는 유효 하지 않습니다.

## <a name="rule-description"></a>규칙 설명
 이 규칙을 검색 하 고 강력한 이름의 어셈블리를 확인 합니다. 위반에는 다음 중 하나라도 해당 하는 경우 발생 합니다.

- 어셈블리에 강력한 이름이 없습니다.

- 어셈블리 서명 후 변경 되었습니다.

- 어셈블리 서명이 연기 됩니다.

- 어셈블리를 잘못 서명 또는 서명에 실패 했습니다.

- 어셈블리 확인을 통과 하도록 레지스트리 설정이 필요 합니다. 예를 들어, 강력한 이름 도구 (Sn.exe) 어셈블리에 대 한 확인을 건너뛰려면 사용 되었습니다.

  강력한 이름은 클라이언트에서 무단으로 변경된 어셈블리를 모르는 사이에 로드하지 못하도록 보호합니다. 강력한 이름이 없는 어셈블리는 극히 제한된 시나리오 이외에는 배포하면 안 됩니다. 제대로 서명되지 않은 어셈블리를 공유하거나 배포하면 어셈블리가 무단으로 변경되거나, 공용 언어 런타임에서 어셈블리를 로드할 수 없거나, 사용자가 자신의 컴퓨터에서 확인을 사용하지 못하게 될 수 있습니다. 강력한 이름이 없는 어셈블리에 다음과 같은 단점이 있습니다.

- 해당 원본은 확인할 수 없습니다.

- 공용 언어 런타임 어셈블리의 내용이 변경 된 경우 사용자에 게 경고 수 없습니다.

- 전역 어셈블리 캐시로 로드할 수 없습니다.

  로드 하는 서명이 연기 된 어셈블리를 분석, 어셈블리에 대 한 확인을 해제 해야 합니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 **키 파일을 만들려면**

 다음 절차 중 하나를 사용 합니다.

- 제공 하는 어셈블리 링커 도구 (Al.exe)을 사용 하 여는 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] SDK.

- 에 대 한 합니다 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] v1.0 또는 v1.1을 사용 합니다 <xref:System.Reflection.AssemblyKeyFileAttribute?displayProperty=fullName> 또는 <xref:System.Reflection.AssemblyKeyNameAttribute?displayProperty=fullName> 특성입니다.

- 에 대 한 합니다 [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)]를 사용 하 여 합니다 `/keyfile` 또는 `/keycontainer` 컴파일러 옵션 [/KEYFILE (지정 서명할 키 또는 키 쌍을 어셈블리)](https://msdn.microsoft.com/library/9b71f8c0-541c-4fe5-a0c7-9364f42ecb06) 또는 [/KEYCONTAINER (어셈블리에 서명할 키 컨테이너 지정)](https://msdn.microsoft.com/library/94882d12-b77a-49c7-96d0-18a31aee001e) 링커 옵션 C++).

  **Visual Studio에서 강력한 이름의 어셈블리에 서명할**

1. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], 솔루션을 엽니다.

2. **솔루션 탐색기**프로젝트를 마우스 오른쪽 단추로 클릭 하 고 클릭 한 다음, **속성입니다.**

3. 클릭 합니다 **서명** 탭을 선택 합니다 **어셈블리에 서명 합니다** 확인란 합니다.

4. **강력한 이름 키 파일 선택**를 선택 **새로 만들기**합니다.

    합니다 **강력한 이름 키 만들기** 창에 표시 됩니다.

5. **키 파일 이름**, 강력한 이름 키의 이름을 입력 합니다.

6. 암호를 사용 하 여 키를 보호 하 고 클릭 여부를 선택할 **확인**합니다.

7. **솔루션 탐색기**프로젝트를 마우스 오른쪽 단추로 클릭 하 고 클릭 **빌드**합니다.

   **Visual Studio 외부에서 강력한 이름의 어셈블리에 서명할**

- 제공 하는 강력한 이름 도구 (Sn.exe)를 사용 하 여 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] SDK. 자세한 내용은 [Sn.exe(강력한 이름 도구)](https://msdn.microsoft.com/library/c1d2b532-1b8e-4c7a-8ac5-53b801135ec6)를 참조하세요.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 환경에서 어셈블리를 사용 하는 경우이 규칙에서 경고를 표시만 콘텐츠를 변조 하지 않아도 되는 경우.

## <a name="see-also"></a>참고 항목
 <xref:System.Reflection.AssemblyKeyFileAttribute?displayProperty=fullName> <xref:System.Reflection.AssemblyKeyNameAttribute?displayProperty=fullName>
 [방법: 강력한 이름의 어셈블리에 서명할](https://msdn.microsoft.com/library/2c30799a-a826-46b4-a25d-c584027a6c67) [Sn.exe (강력한 이름 도구)](https://msdn.microsoft.com/library/c1d2b532-1b8e-4c7a-8ac5-53b801135ec6)
