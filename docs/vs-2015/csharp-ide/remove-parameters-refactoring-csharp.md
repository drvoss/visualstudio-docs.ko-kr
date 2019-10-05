---
title: 제거 매개 변수 리팩터링 (C#) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vs.csharp.refactoring.remove
dev_langs:
- CSharp
helpviewer_keywords:
- parameters [C#], removing
- refactoring [C#], Remove Parameters
- Remove Parameters refactoring [C#]
ms.assetid: f4fc3265-0ef8-4398-a691-c338178697a6
caps.latest.revision: 24
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 40a884fe2ae6aaf73256d8edbcbd083a193b0342
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63444625"
---
# <a name="remove-parameters-refactoring-c"></a>리팩터링 매개 변수 제거(C#)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

`Remove Parameters` 메서드, 인덱서 또는 대리자에서 매개 변수를 제거 하는 쉬운 방법을 제공 하는 리팩터링 작업이입니다. 선언을; 매개 변수 변경 내용 제거 멤버가 호출 되는 모든 위치에서 매개 변수는 새 선언을 반영 하기 위해 제거 됩니다.  
  
 첫 번째 메서드, 인덱서 또는 대리자에서 커서를 놓고 매개 변수 제거 작업을 수행 합니다. 커서가 제거를 호출할 위치에 있는 동안 `Parameters` 작업을 클릭 합니다 **리팩터링** 메뉴 바로 가기 키를 누르거나 바로 가기 메뉴에서 명령을 선택 합니다.  
  
> [!NOTE]
> 확장 메서드의 첫 번째 매개 변수를 제거할 수 없습니다.  
  
### <a name="to-remove-parameters"></a>매개 변수를 제거 하려면  
  
1. 라는 콘솔 응용 프로그램을 만듭니다 `RemoveParameters`, 하 고 다음 대체 `Program` 다음 코드를 사용 하 여 합니다.  
  
    ```csharp  
    class A  
    {  
        // Invoke on 'A'.  
        public A(string s, int i) { }  
    }  
  
    class B  
    {  
        void C()  
        {  
            // Invoke on 'A'.  
            A a = new A("a", 2);  
        }  
    }  
    ```  
  
2. 메서드에 커서를 놓고 `A`를 메서드 선언 또는 메서드 호출 합니다.  
  
3. **리팩터링** 메뉴에서 **매개 변수 제거** 표시 하는 **매개 변수 제거** 대화 상자.  
  
     바로 가기 키 CTRL + R, V 표시를 입력할 수도 있습니다는 **매개 변수 제거** 대화 상자.  
  
     커서를 마우스 오른쪽 단추로 클릭 가리킵니다 **리팩터링**를 클릭 하 고 **매개 변수 제거** 표시 하는 **매개 변수 제거** 대화 상자.  
  
4. 사용 하 여는 **매개 변수** 필드에에 커서를 놓고 `int i`를 클릭 하 고 **제거**합니다.  
  
5. **확인**을 클릭합니다.  
  
6. 에 **변경 내용 미리 보기-매개 변수 제거** 대화 상자, 클릭 **적용**합니다.  
  
## <a name="remarks"></a>설명  
 메서드 선언 또는 메서드 호출에서 매개 변수를 제거할 수 있습니다. 메서드 선언 또는 대리자 이름에 커서를 놓고 제거 매개 변수를 호출 합니다.  
  
> [!CAUTION]
> 메서드 본문의 해당 매개 변수에 대 한 참조 제거 되지 않습니다 하지만 멤버를 본문에서 참조 되는 매개 변수를 제거 하는 매개 변수 사용을 제거 합니다. 코드에 빌드 오류가 발생할 수 있습니다. 사용할 수 있습니다 합니다 **변경 내용 미리 보기** 대화 상자 리팩터링 작업을 실행 하기 전에 코드를 검토 합니다.  
  
 제거할 매개 변수는 메서드를 호출 하는 동안 수정 되 면 매개 변수 제거 수정도 제거 됩니다. 메서드를 호출 하는 경우 변경 되는 예를 들어,  
  
```csharp  
MyMethod(param1++, param2);  
```  
  
 다음으로 변경:  
  
```csharp  
MyMethod(param2);  
```  
  
 리팩터링 작업을 통해 `param1` 증가 하지 않게 됩니다.  
  
## <a name="see-also"></a>참고 항목  
 [리팩터링(C#)](../csharp-ide/refactoring-csharp.md)