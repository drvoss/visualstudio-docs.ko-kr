---
title: 조사식 명령 | Microsoft Docs
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
- debug.watch
helpviewer_keywords:
- Watch command
- Debug.Watch command
ms.assetid: aa02e647-d9f5-4905-a651-52a8df595795
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 9b1d5a1a1ffac1c67b5a3a1e1ad4a860c6b2ad4f
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49214359"
---
# <a name="watch-command"></a>조사식 명령
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
**조사식** 창의 지정된 인스턴스를 만들고 엽니다. **조사식** 창을 사용하여 변수, 식 및 레지스터의 값을 계산하고, 이러한 값을 편집하고, 결과를 저장할 수 있습니다.  
  
## <a name="syntax"></a>구문  
  
```  
Debug.Watch[index]  
```  
  
## <a name="arguments"></a>인수  
 `index`  
 필수. 조사식 창의 인스턴스 번호입니다.  
  
## <a name="remarks"></a>설명  
 `index`는 정수여야 합니다. 유효한 값은 1, 2, 3 또는 4입니다.  
  
## <a name="example"></a>예제  
  
```  
>Debug.Watch1  
```  
  
## <a name="see-also"></a>참고 항목  
 [자동 및 지역 창](../../debugger/autos-and-locals-windows.md)   
 [방법: 변수 창에서 값 편집](http://msdn.microsoft.com/library/36f464ab-c900-4c0b-9ab3-557b3d9cdab5)   
 [방법: 간략 한 조사식 대화 상자를 사용 합니다.](http://msdn.microsoft.com/library/ffaee1dd-e5ce-4ef2-9401-d28329398867)   
 [Visual Studio 명령](../../ide/reference/visual-studio-commands.md)   
 [명령 창](../../ide/reference/command-window.md)   
 [찾기/명령 상자](../../ide/find-command-box.md)   
 [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)



