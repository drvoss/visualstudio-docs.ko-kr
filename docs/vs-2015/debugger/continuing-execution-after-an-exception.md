---
title: 예외 후 실행 계속 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- managed exceptions, continuing execution after
- exceptions, continuing execution after
- debugger, exceptions
- managed code, exception handling
- exception handling, continuing execution after
- execution, continuing after an exception
- program execution
- threading [Visual Studio], continuing execution after exceptions
- Exceptions dialog box
- programs, executing
ms.assetid: 6fe97aac-2131-4615-bd92-d3afee741558
caps.latest.revision: 30
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6ae74c51f0f738bc596fbe5c789011630927707c
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65702263"
---
# <a name="continuing-execution-after-an-exception"></a>예외 후 실행 계속
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

예외로 인해 디버거에서 실행이 중단되면 대화 상자가 나타납니다. Visual Basic 또는 C#에 대해 확인할 수 있습니다 합니다 [예외 도우미](https://msdn.microsoft.com/library/992892ac-9d52-44cc-bf09-b44bfc5befeb) 기본적으로 대화 상자. 에 대 한 C++를 이전 나타납니다 **예외** 대화 상자. Visual Basic 또는 C#을 사용 하는 경우 있지만 사용 하지 않도록 설정한 합니다 **예외 도우미** 에 **옵션** 대화 상자에서 표시 됩니다는 **예외** 대화 상자.  
  
 경우는 **예외 도우미** 하거나 **예외** 대화 상자가 나타나면 예외를 발생 시킨 문제를 해결 하는 데 할 수 있습니다.  
  
## <a name="managed-code"></a>관리 코드  
 관리 코드에서는 처리되지 않은 예외가 발생한 후 같은 스레드에서 실행을 계속할 수 있습니다. 합니다 **예외 도우미** 예외가 throw 된 지점에 대 한 호출 스택을 합니다.  
  
## <a name="native-code"></a>네이티브 코드  
 네이티브 C/C++에서는 두 가지 옵션이 있습니다.  
  
- 클릭할 수 **중단** 문제를 해결 하려고 합니다. 중단 모드에 있는 동안에 프레임을 마우스 오른쪽 단추로 클릭 하 여 호출 스택을 해제할 수 있습니다 합니다 **호출 스택** 창과 선택 **이 프레임으로 해제** 바로 가기 메뉴. 디버깅을 계속할 때 합니다 **예외** 문제가 해결 되지 않은 경우 대화 상자가 다시 나타납니다. 그렇지 않으면 합니다 **예외** 대화 상자가 나타나지 것입니다.  
  
- 클릭할 수 **계속** 문제를 해결 하려고 하지 않고도 계속 실행 합니다. 합니다 **예외** 대화 상자가 다시 나타납니다.  
  
## <a name="mixed-code"></a>혼합 코드  
 네이티브 및 관리 코드가 혼합된 코드를 디버깅하는 동안 처리되지 않은 예외가 발생하면 운영 체제 제한에 따라 호출 스택을 해제할 수 없습니다. 바로 가기 메뉴를 사용하여 호출 스택을 해제하려고 하면 혼합 코드 디버깅 중에 처리되지 않은 예외가 발생하면 디버거가 호출 스택을 해제할 수 없다는 내용의 오류 메시지가 나타납니다.  
  
## <a name="see-also"></a>참고 항목  
 [디버거를 사용한 예외 관리](../debugger/managing-exceptions-with-the-debugger.md)
