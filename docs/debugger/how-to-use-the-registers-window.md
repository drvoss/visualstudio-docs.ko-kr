---
title: Visual Studio 디버거에서 레지스터 값 보기 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.registers
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- registers, debugging
- register contents
- flags, Registers window
- register groups
- debugging [Visual Studio], Registers window
- Registers window
ms.assetid: 2918ffa2-562f-40d6-9053-ef321bbeb767
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5f236bf43d3667cd4263d205c4588593a973824d
ms.sourcegitcommit: a7de99f36e9ead7ea9e9bac23c88d05ddfc38b00
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/20/2018
ms.locfileid: "52257171"
---
# <a name="view-register-values-and-use-the-registers-window-in-the-visual-studio-debugger-c-c-visual-basic-f"></a>등록 값을 확인 하 고 Visual Studio 디버거에서 레지스터 창 사용 (C#, c + +, Visual Basic의 경우 F#)
레지스터 창에서 주소 수준 디버깅을 설정한 경우에 가능 합니다 **옵션** 대화 상자에서 **디버깅** 노드를 **일반** 범주.  
  
 합니다 **등록** 레지스터 내용이 창이 표시 됩니다. 유지 하는 경우는 **등록** 보시 창이 열려 프로그램 한 단계씩 코드 실행에 따라 레지스터 값이 변경 합니다. 최근에 변경된 값은 빨간색으로 표시됩니다. 레지스터 값은 편집할 수 있습니다. 자세한 내용은 [방법: 레지스터 값 편집](../debugger/how-to-edit-a-register-value.md)합니다.  
  
 간단 하 게 표시 합니다 **등록** 플랫폼 및 프로세서에 따라 달라 지는 그룹으로 레지스터를 구성 하는 창 유형입니다. 레지스터 그룹은 사용자에게 맞게 표시하거나 숨길 수 있습니다. 자세한 내용은 [방법: 레지스터 그룹 숨기기 및 표시](../debugger/how-to-display-and-hide-register-groups.md)합니다.  
  
 레지스터 및 레지스터 창의 개념에 대 한 높은 수준의 소개를 참조 하세요 [디버깅 기본 사항: 레지스터 창](../debugger/debugging-basics-registers-window.md)합니다.  
  
> [!NOTE]
>  표시되는 대화 상자와 메뉴 명령은 활성 설정이나 버전에 따라 도움말에서 설명하는 것과 다를 수 있습니다. 설정을 변경하려면 **도구** 메뉴에서 **설정 가져오기 및 내보내기** 를 선택합니다. 자세한 내용은 [Visual Studio IDE 개인 설정](../ide/personalizing-the-visual-studio-ide.md)을 참조하세요.  
  
### <a name="to-display-the-registers-window"></a>레지스터 창을 표시하려면  
  
-   에 **디버그** 메뉴 선택 **Windows**를 선택한 후 **등록** (선택 하거나 **Ctrl** + **Alt**   +  **G**).  
  
     디버거는 실행 중이거나 중단 모드에 있어야 합니다.  
  
    > [!NOTE]
    >  스크립트나 SQL 응용 프로그램의 경우에는 레지스터 정보를 사용할 수 없습니다.  
  
## <a name="see-also"></a>참고 항목  
 [디버깅 기본 사항: 레지스터 창](../debugger/debugging-basics-registers-window.md)   
 [디버거에서 데이터 보기](../debugger/viewing-data-in-the-debugger.md)   
 [디버깅 기본 사항: 레지스터 창](../debugger/debugging-basics-registers-window.md)