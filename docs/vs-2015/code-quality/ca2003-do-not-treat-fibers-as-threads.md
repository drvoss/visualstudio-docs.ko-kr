---
title: 'CA2003: 파이버를 스레드로 취급 하지 마십시오 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2003
- DoNotTreatFibersAsThreads
helpviewer_keywords:
- CA2003
- DoNotTreatFibersAsThreads
ms.assetid: 15398fb1-f384-4bcc-ad93-00e1c0fa9ddf
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 0a1683c8cb9b9c6dc856f40ddbc7864d773f2101
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68189054"
---
# <a name="ca2003-do-not-treat-fibers-as-threads"></a>CA2003: 파이버를 스레드로 취급하지 마세요.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotTreatFibersAsThreads|
|CheckId|CA2003|
|범주|Microsoft.Reliability|
|변경 수준|주요 변경 아님|

## <a name="cause"></a>원인
 관리 되는 스레드가 Win32 스레드라고 취급 됩니다.

## <a name="rule-description"></a>규칙 설명
 관리 되는 스레드가 Win32 스레드라고 가정 하지 마십시오. 파이버는 것입니다. CLR (공용 언어 런타임) SQL에서 소유 하는 실제 스레드 컨텍스트에서 파이버로 관리 되는 스레드가 실행 됩니다. 이러한 스레드는 Appdomain 및에 데이터베이스에서 SQL Server 프로세스에서 공유할 수 있습니다. 관리 되는 스레드 로컬 저장소 작동을 사용 하지만 관리 되지 않는 스레드 로컬 저장소를 사용 하거나 코드 다시 현재 OS 스레드에서 실행 된다고 가정 수 있습니다. 스레드 로캘 등의 설정을 변경 하지 마세요. 이 잠금에 진입 하는 스레드는 잠금을 종료 해야 하므로 CreateCriticalSection 또는 P/Invoke를 통해 createmutex가 호출 하지 마세요. 파이버를 사용 하는 경우에 해당 수 없으므로이, Win32 중요 섹션과 뮤텍스 sql에서 쓸모 없게 됩니다. 안전 하 게 관리 되는 System.Thread 개체에서 대부분의 상태를 사용할 수 있습니다. 이 관리 되는 스레드 로컬 저장소 및 스레드의 현재 사용자 인터페이스 (UI) 문화권을 포함합니다. 그러나 프로그래밍 모델에 대 한 됩니다 SQL;를 사용 하는 경우 스레드의 현재 문화권을 변경. 이 새 사용 권한을 통해 적용 됩니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 스레드 사용량을 살펴보고 그에 따라 코드를 변경 합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 이 규칙을 억제 하면 안 됩니다.
