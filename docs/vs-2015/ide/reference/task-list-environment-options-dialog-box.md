---
title: 옵션 대화 상자, 환경, 작업 목록 | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VS.ToolsOptionsPages.Environment.Task_List
- VS.ToolsOptionsPag.Environment.Task_List
- VS.ToolsOptionsPages.Environment.TaskList
- VS.Environment.Task List
helpviewer_keywords:
- Token List
- tokens
- icons, in Task List
- Task List, customizing environment
- Options dialog box, Task List environment
- exclamation points
- comments, comment tasks in Task List
- tokens, and the Task List
- Task List, comment tasks
ms.assetid: 88327e04-fa3e-48db-995b-ad89e0dc4ed2
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 17404838fc567d37f23c683f6b8f83b7529a3dc8
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49252540"
---
# <a name="task-list-environment-options-dialog-box"></a>옵션 대화 상자, 환경, 작업 목록
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
이 옵션 페이지에서는 **작업 목록** 미리 알림을 생성하는 주석 토큰을 추가, 삭제 및 변경할 수 있습니다. 이러한 설정을 표시하려면 **도구** 메뉴에서 **옵션**을 선택하고 **환경** 폴더를 확장한 후 **작업 목록**을 선택합니다.  
  
## <a name="task-list-options"></a>작업 목록 옵션  
 작업 삭제 확인  
 이 옵션을 선택하면 **작업 목록**에서 사용자 작업을 삭제할 때마다 삭제를 확인하도록 하는 메시지 상자가 표시됩니다. 이 옵션은 기본적으로 선택됩니다.  
  
> [!NOTE]
>  작업 주석을 삭제하려면 링크를 사용하여 주석을 찾은 다음 코드에서 이 주석을 제거합니다.  
  
 파일 이름만 표시  
 이 옵션을 선택하면 **작업 목록**의 **파일** 열에 전체 경로가 아니라 편집할 파일의 이름만 표시됩니다.  
  
## <a name="tokens"></a>토큰  
 텍스트가 **토큰 목록**에 있는 토큰으로 시작되는 주석을 코드에 삽입하는 경우 해당 파일이 편집용으로 열릴 때마다 **작업 목록**에 주석이 새 항목으로 표시됩니다. 이 **작업 목록** 항목을 클릭하여 코드에서 해당 주석 줄로 바로 이동할 수 있습니다. 자세한 내용은 [작업 목록 사용](../../ide/using-the-task-list.md)을 참조하세요.  
  
 토큰 목록  
 토큰의 목록을 표시하고 사용자 지정 토큰을 추가하거나 제거할 수 있게 합니다. 주석 토큰은 Visual C# 및 Visual C++에서 대/소문자를 구분하지만 Visual Basic에서는 그렇지 않습니다.  
  
> [!NOTE]
>  원하는 토큰을 **토큰 목록**에서 표시된 대로 정확히 입력하지 않으면 **작업 목록**에 주석 작업이 표시되지 않습니다.  
  
 우선 순위  
 선택한 토큰을 사용하는 작업의 우선 순위를 설정합니다. 이 토큰으로 시작되는 작업 주석에 **작업 목록**에 지정된 우선 순위가 자동으로 할당됩니다.  
  
 이름  
 토큰 문자열을 입력합니다. 이렇게 하면 **추가** 단추를 사용할 수 있게 됩니다. **추가**하면 이 문자열이 **토큰 목록**에 포함되고 이 이름으로 시작되는 주석이 **작업 목록**에 표시됩니다.  
  
 추가  
 새 **이름**을 입력하면 사용할 수 있게 됩니다. **이름** 및 **우선 순위** 필드에 입력된 값을 사용하여 새로운 토큰 문자열을 추가하려면 이 옵션을 클릭합니다.  
  
 삭제  
 **토큰 목록**에서 선택한 토큰을 삭제하려면 이 옵션을 클릭합니다. 기본 주석 토큰은 삭제할 수 없습니다.  
  
 변경  
 **이름** 및 **우선 순위** 필드에 입력된 값을 사용하여 기존 토큰을 변경하려면 이 옵션을 클릭합니다.  
  
> [!NOTE]
>  기본 주석 토큰을 삭제하거나 그 이름을 바꿀 수는 없지만 해당 우선 순위 수준은 변경할 수 있습니다.  
  
## <a name="see-also"></a>참고 항목  
 [작업 목록 사용](../../ide/using-the-task-list.md)   
 [코드에 책갈피 설정](../../ide/setting-bookmarks-in-code.md)   
 [옵션 대화 상자, 환경](../../ide/reference/environment-options-dialog-box.md)



