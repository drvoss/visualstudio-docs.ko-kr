---
title: '방법: 사용 하 여 편집 하며 계속 하기 (C#) | Microsoft Docs'
ms.date: 10/04/2018
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Edit and Continue [C#], about Edit and Continue
ms.assetid: 40e136d8-a08c-43bd-b313-fb821c55eb3c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 515068f29045ef92ee7d2323f752ba2185f28cac
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62906273"
---
# <a name="how-to-use-edit-and-continue-c"></a>방법: 편집하며 계속하기 사용(C#)
편집 하며 계속 하기를 사용 하 여를 중지 하 고 디버깅 세션을 다시 시작 하지 않고도 디버깅 하는 동안 중단 모드에서 코드 변경 내용을 적용 합니다.

편집 하며 계속 하기 C# 중단 모드에서 코드를 변경한 다음 사용 하 여 디버깅을 계속할 때 자동으로 이루어짐 **계속**합니다 **단계**, 또는 **다음 문 설정**, 또는 디버거 창에서 함수를 계산 합니다.

자세한 내용은 [편집 하며 계속 하기 (Visual C#)](../debugger/edit-and-continue-visual-csharp.md)합니다.

>[!NOTE]
>편집 하며 계속 액세스에 최적화 된, 지원 되지 않습니다 혼합 또는 SQL Server 공용 언어 런타임 (CLR) 통합 코드입니다. 다른 지원 되지 않는 시나리오에 대 한 자세한 내용은 [코드 변경 내용을 지원 (C# 및 Visual Basic)](../debugger/supported-code-changes-csharp.md)합니다. 편집 하 고 이러한 시나리오 중 하나를 사용 하 여 계속 하려는 경우 편집 하며 계속 하기가 지원 되지 않음을 알리는 메시지 상자가 나타납니다.

**편집 하며 계속 하기를 사용할지 설정 합니다.**

1. 디버깅 세션의 경우 디버깅을 중지 (**디버깅할** > **디버깅 중지** 하거나 **Shift**+**F5**) .

1. **도구가** > **옵션** (또는 **디버그** > **옵션**) > **디버깅**  >  **일반**을 선택 하거나 선택을 취소 합니다 **편집을 사용 하도록 설정 하 고 계속** 확인란 합니다.

설정 하거나 디버깅 세션을 다시 시작할 때 적용이 됩니다.

**편집 하며 계속 하기:**

1. 중단 모드에서 디버깅 하는 동안 소스 코드 변경 내용을 확인 합니다.

1. **디버그** 메뉴에서 클릭 **계속**를 **단계**, 또는 **다음 문 설정**, 디버거 창에서 함수 또는 합니다.

   새, 컴파일된 코드를 사용 하 여 계속 디버깅 합니다.

몇 가지 유형의 코드 변경은 편집 하며 계속 하기에서 지원 되지 않습니다. 자세한 내용은 [코드 변경 내용을 지원 (C# 및 Visual Basic)](../debugger/supported-code-changes-csharp.md)합니다.
