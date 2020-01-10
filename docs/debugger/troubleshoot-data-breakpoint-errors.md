---
title: '오류: 데이터 중단점을 설정할 수 없습니다. | Microsoft Docs'
ms.date: 12/3/2019
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.unable_to_set_data_breakpoint
dev_langs:
- CSharp
helpviewer_keywords:
- debugging [Visual Studio], managed
- debugging managed code, data breakpoint
ms.assetid: b06b5d65-424b-490f-bf58-97583cd7006a
author: wardengnaw
ms.author: waan
manager: caslan
ms.workload:
- multiple
ms.openlocfilehash: 18fa63f2a6f4b6d789bad6f813cb3956a636a2d2
ms.sourcegitcommit: 8e123bcb21279f2770b28696995450270b4ec0e9
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75404080"
---
# <a name="troubleshooting-data-breakpoint-errors"></a>데이터 중단점 오류 문제 해결
이 페이지에서는 "값이 변경 될 때 중단"을 사용할 때 표시 되는 일반적인 오류를 해결 하는 과정을 안내 합니다.

## <a name="diagnosing-unable-to-set-data-breakpoint-errors"></a>"데이터 중단점을 설정할 수 없습니다." 오류 진단
> [!IMPORTANT]
> 관리 되는 데이터 중단점은 .NET Core 3.0 이상에서 지원 됩니다. [여기](https://dotnet.microsoft.com/download)에서 최신 버전을 다운로드할 수 있습니다.

다음은 관리 되는 데이터 중단점을 사용할 때 발생할 수 있는 오류 목록입니다. 여기에는 오류가 발생 하는 이유에 대 한 추가 설명과 오류를 해결 하는 데 가능한 해결 방법이 포함 되어 있습니다.

- *"대상 프로세스에서 사용 하는 .NET 버전이 데이터 중단점을 지원 하지 않습니다. 데이터 중단점에는 x86 또는 x 64에서 실행 되는 .NET Core 3.0 이상이 필요 합니다. "*

    - 관리 되는 데이터 중단점에 대 한 지원은 .NET Core 3.0에서 시작 됩니다. 3\.0의 .NET Core .NET Framework 또는 버전에서는 현재 지원 되지 않습니다. 
    
    - **해결**방법:이에 대 한 해결 방법은 프로젝트를 .net Core 3.0로 업그레이드 하는 것입니다.

- *"관리 되는 힙에서 값을 찾을 수 없으므로 추적할 수 없습니다."*
    - 스택에서 선언 된 변수입니다.
        - 함수가 종료 되 면이 변수는 유효 하지 않으므로 스택에 생성 된 변수에 대 한 데이터 중단점 설정은 지원 하지 않습니다.
        - **해결 방법**: 변수가 사용 되는 줄에 중단점을 설정 합니다.

    - 드롭다운에서 확장 되지 않은 변수에 대해 "값이 변경 되 면 중단"
        - 디버거는 내부적으로 추적 하려는 필드가 포함 된 개체를 알고 있어야 합니다. 가비지 수집기는 힙에서 개체를 이동할 수 있으므로 디버거에서 추적 하려는 변수를 보유 하 고 있는 개체를 알고 있어야 합니다. 
        - **해결 방법**: 데이터 중단점을 설정 하려는 개체 내의 메서드에 있는 경우 하나의 프레임으로 이동 하 고 `locals/autos/watch` 창을 사용 하 여 개체를 확장 하 고 원하는 필드에 데이터 중단점을 설정 합니다.

- *"정적 필드 또는 정적 속성에는 데이터 중단점이 지원 되지 않습니다."*
    
    - 정적 필드 및 속성은 현재 지원 되지 않습니다. 이 기능에 관심이 있는 경우 [피드백](#provide-feedback)을 제공 해 주세요.

- *"구조체의 필드 및 속성을 추적할 수 없습니다."*

    - 현재 구조체의 필드와 속성은 지원 되지 않습니다. 이 기능에 관심이 있는 경우 [피드백](#provide-feedback)을 제공 해 주세요.

- *"속성 값이 변경 되었으며 더 이상 추적할 수 없습니다."*

    - 속성은 런타임 중에 계산 되는 방식을 변경할 수 있으며,이 경우 속성이 의존 하는 변수의 수가 늘어나고 하드웨어 제한을 초과할 수 있습니다. 자세한 내용은 아래의 `"The property is dependent on more memory than can be tracked by the hardware."` 섹션을 참조하십시오.

- *"속성이 하드웨어에서 추적할 수 있는 것 보다 많은 메모리에 종속 되어 있습니다."*
    
    - 각 아키텍처에는 지원할 수 있는 바이트 수와 하드웨어 데이터 중단점 및 데이터 중단점을 설정 하려는 속성이 해당 제한을 초과 했습니다. 사용 중인 아키텍처에 대해 사용할 수 있는 하드웨어 지원 데이터 중단점과 바이트 수를 확인 하려면 [데이터 중단점 하드웨어 제한](#data-breakpoint-hardware-limitations) 표를 참조 하세요. 
    - **해결 방법**: 속성 내에서 변경 될 수 있는 값에 대 한 데이터 중단점을 설정 합니다.

- *"레거시 C# 식 계산기를 사용 하는 경우에는 데이터 중단점이 지원 되지 않습니다."*

    - 데이터 중단점은 레거시 C# 가 아닌 식 계산기 에서만 지원 됩니다. 
    - **해결**방법: `Debug -> Options`로 이동 C# 하 `Debugging -> General` `"Use the legacy C# and VB expression evaluators"`을 선택 취소 하 여 레거시 식 계산기를 사용 하지 않도록 설정 합니다.

## <a name="data-breakpoint-hardware-limitations"></a>데이터 중단점 하드웨어 제한 사항

프로그램이 실행 되는 아키텍처 (플랫폼 구성)에는 사용할 수 있는 하드웨어 데이터 중단점 수가 제한 되어 있습니다. 아래 표에서는 아키텍처에 따라 사용할 수 있는 레지스터 수를 나타냅니다.

| 아키텍처 | 하드웨어 지원 데이터 중단점 수 | 최대 바이트 크기|
| :-------------: |:-------------:| :-------------:|
| x86 | 4 | 4 |
| x64 | 4 | 8 |
| ARM | 1 | 4 |
| ARM64 | 2 | 8 |

## <a name="provide-feedback"></a>피드백 제공
이 기능에 대 한 문제 또는 제안 사항은 IDE 또는 [개발자 커뮤니티](https://developercommunity.visualstudio.com/)에서 [문제를 보고 하는](../ide/how-to-report-a-problem-with-visual-studio.md) 데 도움이 되는 > 사용자 > 의견을 보내 알려주세요.

## <a name="see-also"></a>참조
- [.Net Core 3.0의 "값 변경 시 중단"을 사용](using-breakpoints.md#BKMK_set_a_data_breakpoint_native_cplusplus)합니다.
- [DevBlog: 값 변경 시 중단: Visual Studio 2019의 .NET Core에 대 한 데이터 중단점](https://devblogs.microsoft.com/visualstudio/break-when-value-changes-data-breakpoints-for-net-core-in-visual-studio-2019/)
