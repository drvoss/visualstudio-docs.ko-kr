---
title: 예외 후 실행 계속 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d557fc0ec056cac22603338f95920e5c721f67dd
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62564101"
---
# <a name="continuing-execution-after-an-exception"></a>예외 후 실행 계속
디버거 실행 예외로 인해 중단 될 때 표시 됩니다는 **예외 도우미**, 기본적으로 합니다. 사용 하지 않도록 설정한 경우 합니다 **예외 도우미** 에 **옵션** 대화 상자에서 표시 됩니다는 **예외 도우미** (C# 또는 Visual Basic) 또는  **예외** 대화 상자 (C++).

 경우는 **예외 도우미** 나타나면 예외를 발생 시킨 문제를 해결 하는 데 할 수 있습니다.

## <a name="managed-and-native-code"></a>관리 및 네이티브 코드
 관리 및 네이티브 코드에서 처리 되지 않은 예외가 발생 한 후 동일한 스레드에서 실행을 계속할 수 있습니다. 합니다 **예외 도우미** 예외가 throw 된 지점에 대 한 호출 스택을 합니다.

## <a name="mixed-code"></a>혼합 코드
 네이티브 및 관리 코드가 혼합된 코드를 디버깅하는 동안 처리되지 않은 예외가 발생하면 운영 체제 제한에 따라 호출 스택을 해제할 수 없습니다. 바로 가기 메뉴를 사용하여 호출 스택을 해제하려고 하면 혼합 코드 디버깅 중에 처리되지 않은 예외가 발생하면 디버거가 호출 스택을 해제할 수 없다는 내용의 오류 메시지가 나타납니다.

## <a name="see-also"></a>참고 항목

- [디버거를 사용한 예외 관리](../debugger/managing-exceptions-with-the-debugger.md)