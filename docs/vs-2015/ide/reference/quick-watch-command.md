---
title: 간략한 조사식 명령 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.quickwatch
helpviewer_keywords:
- Quick Watch command
- Debug.Quickwatch command
ms.assetid: 9670ac3a-8f2f-4874-974d-cb87d3b0cde1
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: c9ac805ebea19604343d561bf553448fff2ca575
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MTE95
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65701745"
---
# <a name="quick-watch-command"></a>간략한 조사식 명령
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[간략한 조사식](https://msdn.microsoft.com/library/ffaee1dd-e5ce-4ef2-9401-d28329398867) 대화 상자의 [식] 필드에 선택한 텍스트 또는 지정한 텍스트를 표시합니다. 이 대화 상자를 사용하여 디버거에서 인식되는 변수 또는 식의 현재 값이나 레지스터의 콘텐츠를 계산할 수 있습니다. 또한 비const 변수 값 또는 레지스터 콘텐츠를 변경할 수 있습니다.  
  
## <a name="syntax"></a>구문  
  
```  
Debug.QuickWatchq [text]  
```  
  
## <a name="arguments"></a>인수  
 `text`  
 선택 사항입니다. **간략한 조사식** 대화 상자에 추가할 텍스트입니다.  
  
## <a name="remarks"></a>주의  
 `text`가 생략되면 커서에서 현재 선택된 텍스트 또는 단어가 조사식 창에 추가됩니다.  
  
## <a name="example"></a>예제  
  
```  
>Debug.QuickWatch  
```  
  
## <a name="see-also"></a>참고 항목  
 [방법: 간략한 조사식 대화 상자 사용](https://msdn.microsoft.com/library/ffaee1dd-e5ce-4ef2-9401-d28329398867)   
 [Visual Studio 명령](../../ide/reference/visual-studio-commands.md)   
 [명령 창](../../ide/reference/command-window.md)   
 [찾기/명령 상자](../../ide/find-command-box.md)   
 [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)
