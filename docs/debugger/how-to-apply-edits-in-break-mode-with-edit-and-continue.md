---
title: '방법: 편집을 사용 하 여 중단 모드에서 편집을 적용 하 고 계속 | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.variables.failededit
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Edit and Continue [Visual Basic], applying edits in break mode
- break mode, applying code changes
- Edit and Continue, applying edits in break mode
- editing, break mode
- coding, editing in break mode
- code, editing in break mode
ms.assetid: 1eef7498-6a1f-4fba-8146-510adc6375c9
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f45b2a64e7602d038a12f436019a8f99e352aa26
ms.sourcegitcommit: a7de99f36e9ead7ea9e9bac23c88d05ddfc38b00
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/20/2018
ms.locfileid: "52257074"
---
# <a name="how-to-apply-edits-in-break-mode-with-edit-and-continue-visual-basic"></a>방법: 편집을 사용 하 여 중단 모드에서 편집을 적용 하 고 계속 하기 (Visual Basic)
편집하며 계속하기를 사용하면 실행을 중지한 후에 다시 시작하지 않고도 중단 모드에서 코드를 편집한 다음 계속 진행할 수 있습니다.  
  
편집 하며 계속 하기를 사용 하 여 디버깅 하는 동안 자세한 내용은 [지원 되는 코드 변경 (C# 및 Visual Basic](../debugger/supported-code-changes-csharp.md)]
  
### <a name="to-edit-code-in-break-mode"></a>중단 모드에서 코드를 편집하려면  
  
1.  다음 중 한 가지 방법으로 중단 모드를 시작합니다.  
  
    -   선택한 코드에서 중단점을 설정 **디버깅 시작** 에서 합니다 **디버그** 메뉴와 응용 프로그램이 중단점에 도달할 때까지 기다립니다.  
  
         또는  
  
    -   디버깅을 시작 하 고 선택한 **모두 중단** 에서 합니다 **디버그** 메뉴.  
  
         또는  
  
    -   예외가 발생 하는 경우 선택할 **편집 사용** 에 **예외 도우미**합니다.  
  
2.  원하는 및 지원 되는 코드를 변경 합니다.  
  
     자세한 내용은 [지원 되는 코드 변경 (C# 및 Visual Basic](../debugger/supported-code-changes-csharp.md)합니다.  
  
    > [!NOTE]
    >  편집하며 계속하기에서 허용되지 않는 코드 변경 작업을 수행하면 자주색 물결선이 편집 내용 아래에 밑줄로 표시되고 해당 작업이 작업 목록에 나타납니다. 잘못된 코드 변경 내용을 취소하지 않으면 코드 실행을 계속 진행할 수 없습니다.  
  
3.  에 **디버그** 메뉴에서 클릭 **계속** 실행을 다시 시작 합니다.  
  
     적용한 편집 내용이 프로젝트에 통합된 상태로 코드가 실행됩니다.  
  
## <a name="see-also"></a>참고 항목  
 [코드 변경 내용을 지원 (C# 및 Visual Basic](../debugger/supported-code-changes-csharp.md)   
 [편집하며 계속하기(Visual Basic)](../debugger/edit-and-continue-visual-basic.md)