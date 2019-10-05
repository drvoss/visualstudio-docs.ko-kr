---
title: '방법: 사용 하 여 편집 하며 계속 하기 (C#) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- Edit and Continue [C#], about Edit and Continue
ms.assetid: 40e136d8-a08c-43bd-b313-fb821c55eb3c
caps.latest.revision: 22
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 39137d5fe60a3c91c8fd3904e797eb83420a8f5d
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63384021"
---
# <a name="how-to-use-edit-and-continue-c"></a>방법: 편집하며 계속하기 사용(C#)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

C#에서 편집하며 계속하기를 사용하면 디버깅하는 동안 중단 모드에서 코드를 변경할 수 있습니다. 디버깅 세션을 중지하고 다시 시작하지 않고도 변경 내용을 적용할 수 있습니다.  
  
 편집 하며 계속 하기는 자동으로 호출 중단 모드에서 변경한 다음 디버거 실행을 선택 하는 경우와 같은 명령을 **계속**하십시오 **단계**, 또는 **다음 문 설정**, 또는 디버거 창에서 함수를 계산 합니다.  
  
> [!NOTE]
> Compact Framework, 최적화된 코드, 혼합된 네이티브/관리 코드 또는 SQL Server CLR(공용 언어 런타임) 통합 코드를 디버깅할 때는 편집하며 계속하기가 지원되지 않습니다. 이러한 시나리오 중 하나에서 코드 변경 내용을 적용 하려고 하면 디버거는 편집 하며 계속 하기가 지원 되지 않음을 설명 대화 상자를 배치 합니다.  
  
### <a name="to-invoke-edit-and-continue-automatically"></a>편집을 호출 하 고 자동으로 계속  
  
1. 중단 모드에서 소스 코드 변경 내용을 확인 합니다.  
  
2. **디버그** 메뉴에서 클릭 **계속**를 **단계**, 또는 **다음 문 설정** 디버거 창에서 함수 또는 합니다.  
  
     새 코드를 컴파일하고 새 코드를 사용 하 여 계속 디버깅 합니다. 일부 변경 내용이 편집 하며 계속 하기에서 지원 되지 않습니다. 자세한 내용은 [지원 되는 코드 변경 (C#)](../debugger/supported-code-changes-csharp.md)합니다.  
  
### <a name="to-enabledisable-edit-and-continue"></a>편집하며 계속하기를 사용하거나 사용하지 않도록 설정하려면  
  
1. **도구** 메뉴에서 **옵션**을 클릭합니다.  
  
2. 에 **옵션** 대화 상자에서 합니다 **디버깅** 노드를 선택한 **편집 하며 계속 하기**합니다.  
  
3. 에 **옵션** 대화 상자 **편집 하며 계속 하기** 페이지에서 선택 하거나 선택을 취소 합니다 **사용 하도록 설정 편집 하며 계속 하기** 확인란 합니다.  
  
     이 설정은 디버깅 세션을 다시 시작 하면 적용이 됩니다.  
  
## <a name="see-also"></a>참고 항목  
 [편집하며 계속하기(Visual C#)](../debugger/edit-and-continue-visual-csharp.md)   
 [지원 되는 코드 변경 (C#)](../debugger/supported-code-changes-csharp.md)   
 [편집하며 계속하기의 오류 및 경고(C#)](../misc/edit-and-continue-errors-and-warnings-csharp.md)
