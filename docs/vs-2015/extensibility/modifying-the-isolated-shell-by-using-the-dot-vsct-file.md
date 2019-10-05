---
title: 사용 하 여 격리 셸 수정 합니다. Vsct 파일 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio shell, isolated mode%2C .vsct file
ms.assetid: 6d147c2d-10e9-400e-b8ce-5566287b41ba
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8c106a04e809e772ac3b8a77192fb2f101161e9c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68194225"
---
# <a name="modifying-the-isolated-shell-by-using-the-vsct-file"></a>사용 하 여 격리 셸 수정 합니다. Vsct 파일
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio 격리 셸 프로젝트에 대 한 UI 프로젝트는 응용 프로그램에서 사용할 수 있는 응용 프로그램 그룹 및 개별 명령을 지정할 수 있는.vsct 파일을 포함 합니다. 다음은 수정 되지 않은.vsct 파일에서 발췌입니다.  
  
```  
<!-- <Define name="No_WindowListCommand"/> -->  
<!-- <Define name="No_MoreWindowsCommand"/> -->  
<!-- <Define name="No_PaneNextPaneCommand"/> -->  
<!-- <Define name="No_PanePrevPaneCommand"/> -->  
```  
  
 기본적으로 대부분의 명령 및 명령 그룹 포함 됩니다. 명령 또는 명령 그룹을 제외 하려면 단순히 해당 명령 또는 그룹 주석입니다.  
  
 예를 들어, 다음 창 및 이전 창 명령을 제거 하려면 주석 처리를 제거 합니다 `No_PaneNextPaneCommand` 고 `No_PanePrevPaneCommand` 항목:  
  
```  
  
<Define name="No_PaneNextPaneCommand"/> <Define name="No_PanePrevPaneCommand"/>  
  
```  
  
 자세한 예제에서는 이러한 사용자 지정, 참조 [연습: 격리 셸 응용 프로그램을 만드는 기본](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)입니다.  
  
## <a name="referenced-files"></a>참조 된 파일  
 응용 프로그램에 대 한 기본.vsct 파일에는 다음 파일을 참조 합니다. 이러한 파일은 Visual Studio SDK 설치 디렉터리의 \VisualStudioIntegration\Common\Inc\ 하위 디렉터리에 있습니다.  
  
|파일|Description|  
|----------|-----------------|  
|wbids.h|웹 검색 패키지에 대 한 UI id입니다.|  
|AppIDCmdUsed.vsct|기본 Visual Studio UI 요소에 대 한 명령 테이블입니다.|  
|EmulatorCmdUsed.vsct|Emacs 및 Brief 편집기 에뮬레이션 UI 요소에 대 한 명령 테이블입니다.|  
|Vsdebugguids.h|명령, 옵션 페이지 및 기타 기능에서 Visual Studio 디버거의 Guid를 정의합니다.|  
|VsDbgCmdUsed.vsct|디버거에 대 한 명령 테이블입니다.|  
  
 AppIDCmdUsed.vsct 파일에는 응용 프로그램.vsct 파일에서 정의 된 기호에 따라 Visual Studio UI 요소가 포함 됩니다.  
  
 자세한 내용은 참조 하세요. [XML 명령 테이블 디자인 (합니다. Vsct) 파일](../extensibility/internals/designing-xml-command-table-dot-vsct-files.md) 하며 [VSCT XML 스키마 참조](../extensibility/vsct-xml-schema-reference.md)합니다.  
  
## <a name="see-also"></a>참고 항목  
 [Visual Studio Shell(격리)](../extensibility/visual-studio-isolated-shell.md)
