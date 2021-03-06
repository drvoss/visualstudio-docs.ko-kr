---
title: 빌드 이벤트 대화 상자(Visual Basic) | Microsoft Docs
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
- vb.ProjectPropertiesBuildEvents
helpviewer_keywords:
- build events
- build events, specifying
- pre-build events
- Build Events dialog box
- post-build events
ms.assetid: 3a81a7c7-39f9-47a8-ba5a-b351227f380e
caps.latest.revision: 8
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: e4d0ad4235a309fafd025c4c205b9fa150f47af5
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49189100"
---
# <a name="build-events-dialog-box-visual-basic"></a>빌드 이벤트 대화 상자(Visual Basic)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
**빌드 이벤트** 대화 상자를 사용하여 빌드 구성 지침을 지정합니다. 또한 빌드 전후 이벤트를 실행할 조건을 지정할 수 있습니다. 자세한 내용은 [방법: 빌드 이벤트 지정(Visual Basic)](../../ide/how-to-specify-build-events-visual-basic.md)을 참조하세요.  
  
 **빌드 전 이벤트 명령줄**  
 빌드를 시작하기 전에 실행할 명령을 지정합니다. 긴 명령을 입력하려면 **빌드 전 편집**을 클릭하여 [빌드 전 이벤트/빌드 후 이벤트 명령줄](../../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md) 대화 상자를 표시합니다.  
  
> [!NOTE]
>  프로젝트가 최신 상태이고 빌드가 트리거되지 않으면 빌드 전 이벤트가 실행되지 않습니다.  
  
 **빌드 후 이벤트 명령줄**  
 빌드가 끝난 후 실행할 명령을 지정합니다. 긴 명령을 입력하려면 **빌드 후 편집**을 클릭하여 **빌드 전 이벤트/빌드 후 이벤트 명령줄** 대화 상자를 표시합니다.  
  
> [!NOTE]
>  .bat 파일을 실행하는 모든 빌드 후 이벤트 명령 앞에 `call` 문을 추가합니다. 예를 들어 `call C:\MyFile.bat` 또는 `call C:\MyFile.bat call C:\MyFile2.bat`로 이름을 지정할 수 있습니다.  
  
 **빌드 후 이벤트 실행**  
 다음 표에 나와 있는 것처럼 실행할 빌드 후 이벤트에 대한 조건을 지정합니다.  
  
|옵션|결과|  
|------------|------------|  
|**항상**|빌드의 성공 여부에 관계 없이 빌드 후 이벤트가 실행됩니다.|  
|**빌드가 성공한 경우**|빌드에 성공하면 빌드 후 이벤트가 실행됩니다. 이벤트는 빌드가 성공하는 한 최신 프로젝트에도 실행됩니다. 이것이 기본 설정입니다.|  
|**빌드에서 프로젝트 출력을 업데이트한 경우**|컴파일러의 출력 파일(.exe 또는.dll)이 이전 컴파일러 출력 파일과 다른 경우에만 빌드 후 이벤트가 실행됩니다. 프로젝트가 최신 상태이면 빌드 후 이벤트가 실행되지 않습니다.|  
  
## <a name="see-also"></a>참고 항목  
 [프로젝트 디자이너, 컴파일 페이지(Visual Basic)](../../ide/reference/compile-page-project-designer-visual-basic.md)   
 [방법: 빌드 이벤트 지정(Visual Basic)](../../ide/how-to-specify-build-events-visual-basic.md)   
 [빌드 전 이벤트/빌드 후 이벤트 명령줄 대화 상자](../../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md)



