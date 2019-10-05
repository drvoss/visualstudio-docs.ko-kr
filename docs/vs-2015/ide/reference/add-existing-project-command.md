---
title: 기존 프로젝트 추가 명령 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- file.addexistingproject
helpviewer_keywords:
- Add Existing Project command
- File.AddExistingProject
ms.assetid: 71cf3e31-c76b-405b-ad6a-1b1bc654bd40
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 4778efc4a50ceb63e72d4283644537345510e833
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MTE95
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68194956"
---
# <a name="add-existing-project-command"></a>기존 프로젝트 추가 명령
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

현재 솔루션에 기존 프로젝트를 추가합니다.  
  
## <a name="syntax"></a>구문  
  
```  
File.AddExistingProject filename  
```  
  
## <a name="arguments"></a>인수  
 `filename`  
 선택 사항입니다. 솔루션에 추가할 프로젝트의 전체 경로 및 프로젝트 이름(확장명 포함)입니다.  
  
 `filename` 인수에 공백이 있는 경우 따옴표로 묶어야 합니다.  
  
 파일 이름을 지정하지 않은 경우 명령을 실행하면 사용자가 프로젝트를 선택할 수 있는 파일 대화 상자가 열립니다.  
  
## <a name="remarks"></a>설명  
 입력 시 자동 완성에서 올바른 경로와 파일 이름을 찾으려고 합니다.  
  
## <a name="example"></a>예  
 이 예제에서는 [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] 프로젝트인 TestProject1을 현재 솔루션에 추가합니다.  
  
```  
>File.AddExistingProject "c:\visual studio projects\TestProject1.vbproj"  
```  
  
## <a name="see-also"></a>참고 항목  
 [Visual Studio 명령](../../ide/reference/visual-studio-commands.md)   
 [명령 창](../../ide/reference/command-window.md)   
 [찾기/명령 상자](../../ide/find-command-box.md)   
 [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)
