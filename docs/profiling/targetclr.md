---
title: TargetCLR | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: f9732480-287f-40f1-a4ff-b112e143b940
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 479f7e1cbd85c0421497020ae1fc108154ca639a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62968316"
---
# <a name="targetclr"></a>TargetCLR
**TargetCLR** 옵션은 한 애플리케이션에 두 개 이상의 CLR 버전이 로드된 경우 프로파일링할 CLR(공용 언어 런타임) 버전을 지정합니다.

 기본적으로 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 프로파일링 도구는 애플리케이션에서 로드된 CLR의 첫 번째 버전을 대상으로 합니다.

## <a name="syntax"></a>구문

```cmd
VSPerfCmd.exe {/Launch:AppName | /Attach:PID} /TargetCLR[:ClrVersion] [Options]
```

#### <a name="parameters"></a>매개 변수
 `ClrVersion` CLR의 버전 번호입니다. 버전 형식 **vN.N.NNNNN**을 사용합니다.

## <a name="required-options"></a>필수 옵션
 **TargetCLR** 옵션은 **Launch** 또는 **Attach** 옵션에만 사용할 수 있습니다.

 **시작:** `AppName` 지정한 애플리케이션을 시작하고 프로파일링을 시작합니다.

 **연결:** `PID` 지정된 프로세스 프로파일링을 시작합니다.

## <a name="example"></a>예제
 이 예제에서 TargetCLR 옵션은 CLR 버전 4.0.11003이 프로파일링되고 있는지 확인하는 데 사용됩니다.

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp
VSPerfCmd.exe /Launch:TestApp.exe /TargetCLR:v4.0.11003
```