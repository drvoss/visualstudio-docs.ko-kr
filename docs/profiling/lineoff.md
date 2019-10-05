---
title: LineOff | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 76082063-20ef-47ae-ad64-81b43b654865
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b4de8aa278adab0127f3a39d9adcf105f906e152
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62995335"
---
# <a name="lineoff"></a>LineOff
기본적으로 프로파일러는 샘플링 프로파일링 방법을 사용하는 경우 소스 코드 줄 번호 및 줄 번호 오프셋 데이터를 수집합니다. VSPerfCmd **LineOff** 옵션은 애플리케이션을 시작하는 데 VSPerfCmd를 사용하는 경우 줄 번호 데이터 수집을 비활성화합니다. **LineOff**가 지정될 때 프로파일링 데이터는 함수 수준에 수집됩니다.

 **LineOff**를 **Launch** 옵션 및 프로파일러가 **Start**:**Sample** 옵션을 사용하여 샘플링으로 초기화된 경우에만 사용할 수 있습니다.

## <a name="syntax"></a>구문

```cmd
VSPerfCmd.exe /Launch:AppName /LineOff [Options]
```

#### <a name="parameters"></a>매개 변수
 없음

## <a name="required-options"></a>필수 옵션
 **LineOff** 옵션은 **Launch** 옵션을 포함하는 명령줄에서만 사용할 수 있습니다.

 **시작:** `AppName` 지정된 애플리케이션을 시작하고 샘플링 방법으로 프로파일링을 시작합니다.

## <a name="example"></a>예제
 이 예제에서는 애플리케이션 및 프로파일러를 시작하고 줄 수준 샘플링을 비활성화합니다.

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp
VSPerfCmd.exe /Launch:TestApp.exe /LineOff
```

## <a name="see-also"></a>참고 항목
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [독립 실행형 애플리케이션 프로파일링](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [ASP.NET 웹 애플리케이션 프로파일링](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [서비스 프로파일링](../profiling/command-line-profiling-of-services.md)