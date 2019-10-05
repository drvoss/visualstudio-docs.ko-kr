---
title: 리팩터링 (C#) 매개 변수 다시 정렬 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vs.csharp.refactoring.reorder
dev_langs:
- CSharp
helpviewer_keywords:
- refactoring [C#], Reorder Parameters
- Reorder Parameters refactoring [C#]
ms.assetid: 4dabf21a-a9f0-41e9-b11b-55760cf2bd90
caps.latest.revision: 26
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: daf77a60256e59cabd176990f3642a2206a7f0d8
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63444542"
---
# <a name="reorder-parameters-refactoring-c"></a>매개 변수 리팩터링 다시 정렬(C#)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

`Reorder Parameters` 메서드, 인덱서 및 대리자에 대 한 매개 변수의 순서를 변경 하는 쉬운 방법을 제공 하는 작업은 Visual C# 리팩터링 합니다. `Reorder Parameters` 선언을 변경 멤버가 호출 되는 모든 위치에서 매개 변수를 새 순서를 반영 하도록 다시 정렬 됩니다.  
  
 수행 하는 `Reorder Parameters` 작업 또는 메서드, 인덱서 또는 대리자 옆에 커서를 놓습니다. 커서 위치에 있을 때 호출 된 `Reorder Parameters` 바로 가기 키를 눌러 또는 바로 가기 메뉴에서 명령을 클릭 하 여 작업 합니다.  
  
> [!NOTE]
> 확장 메서드의 첫 번째 매개 변수를 변경할 수 없습니다.  
  
### <a name="to-reorder-parameters"></a>매개 변수 순서를 변경 하려면  
  
1. 라는 클래스 라이브러리를 만듭니다 `ReorderParameters`, 하 고 다음 대체 `Class1` 다음 예제 코드를 사용 합니다.  
  
    ```csharp  
    class ProtoClassA  
    {  
        // Invoke on 'MethodB'.  
        public void MethodB(int i, bool b) { }  
    }  
  
    class ProtoClassC  
    {  
        void D()  
        {  
            ProtoClassA MyClassA = new ProtoClassA();  
  
            // Invoke on 'MethodB'.  
            MyClassA.MethodB(0, false);  
        }  
    }  
    ```  
  
2. 커서를 놓고 `MethodB`를 메서드 선언 또는 메서드 호출 합니다.  
  
3. 에 **리팩터링** 메뉴에서 클릭 **매개 변수 다시 정렬**합니다.  
  
     합니다 **매개 변수 다시 정렬** 대화 상자가 나타납니다.  
  
4. 에 **매개 변수 다시 정렬** 대화 상자에서 `int i` 에 **매개 변수** 목록 및 아래쪽 단추를 클릭 합니다.  
  
     또는 끌 수 있습니다 `int i` 한 후 `bool b` 에 **매개 변수** 목록입니다.  
  
5. 에 **매개 변수 다시 정렬** 대화 상자, 클릭 **확인**합니다.  
  
     경우는 **참조 변경 미리 보기** 옵션을 선택한 합니다 **매개 변수 다시 정렬** 대화 상자를 **변경 내용 미리 보기-매개 변수 다시 정렬** 대화 상자가 표시 됩니다. 에 대 한 매개 변수 목록에서 변경 내용을 미리 볼 `MethodB` 시그니처 및 메서드 호출에서.  
  
    1. 경우는 **변경 내용 미리 보기-매개 변수 다시 정렬** 대화 상자가 나타나면 **적용**합니다.  
  
         이 예제에서는 메서드 선언 및 모든 메서드 호출에 대 한 사이트 `MethodB` 업데이트 됩니다.  
  
## <a name="remarks"></a>설명  
 메서드 선언 또는 메서드 호출에서 매개 변수를 다시 정렬할 수 있습니다. 또는 메서드 또는 대리자 선언을 옆에 있는 있지만 본문에는 없는 커서를 놓습니다.  
  
## <a name="see-also"></a>참고 항목  
 [리팩터링(C#)](../csharp-ide/refactoring-csharp.md)