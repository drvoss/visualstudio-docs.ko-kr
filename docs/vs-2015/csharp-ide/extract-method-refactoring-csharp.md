---
title: 메서드 추출 리팩터링 (C#) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vs.csharp.refactoring.extractmethod
dev_langs:
- CSharp
helpviewer_keywords:
- refactoring [C#], Extract Method
- Extract Method refactoring operation [C#]
ms.assetid: eeba11df-a815-4bec-9c21-8a831891b783
caps.latest.revision: 29
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 5a889250e641e004bdb0d89f6965c43c3d6b8e2a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68155247"
---
# <a name="extract-method-refactoring-c"></a>메서드 추출 리팩터링(C#)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**메서드 추출** 리팩터링 작업 손쉽게 기존 멤버의 코드 조각에서 새 메서드를 만들 수입니다.  
  
 사용 하 여 **메서드 추출**, 선택 된 기존 멤버의 코드 블록 내에서 코드를 추출 하 여 새 메서드를 만들 수 있습니다. 새, 추출 된 메서드는 선택한 코드를 포함 하 고 기존 멤버의 선택 된 코드는 새 메서드를 호출 하 여 대체 됩니다. 코드 조각을 고유한 메서드로 설정 하 고 있습니다 신속 하 게 정확 하 게 재사용 성과 가독성을 향상 시키기 위해 코드를 다시 구성 합니다.  
  
 **메서드 추출** 다음과 같은 이점이 있습니다.  
  
- 불연속, 다시 사용할 수 있는 방법을 강조 하 여 최적의 코딩 방식을 권장 합니다.  
  
- 자체 좋은 구성을 통해 코드를 문서화 하는 것이 좋습니다.  
  
     수 설명이 포함 된 이름을 사용 하는, 높은 수준의 메서드 경우 자세히 같은 일련의 주석입니다.  
  
- 정밀 메서드 재정의 간소화 하기 위해 만드는 것이 좋습니다.  
  
- 코드 중복을 줄입니다.  
  
### <a name="to-use-extract-method"></a>추출 메서드를 사용 하려면  
  
1. `ExtractMethod`이라는 콘솔 애플리케이션을 만들고 `Program`을 다음 예제 코드로 바꿉니다.  
  
    ```csharp  
    class A  
    {  
        const double PI = 3.141592;  
  
        double CalculatePaintNeeded(double paintPerUnit, double radius)  
        {  
            // Select any of the following:  
            // 1. The entire next line of code.  
            // 2. The right-hand side of the next line of code.  
            // 3. Just "PI *" of the right-hand side of the next line  
            //    of code (to see the prompt for selection expansion).  
            // 4.  All code within the method body.  
            // ...Then invoke Extract Method.  
  
            double area = PI * radius * radius;  
  
            return area / paintPerUnit;  
        }  
    }  
    ```  
  
2. 추출 하려는 코드 조각을 선택 합니다.  
  
    ```csharp  
    double area = PI * radius * radius;  
    ```  
  
3. 에 **리팩터링** 메뉴에서 클릭 **메서드 추출**합니다.  
  
     합니다 **메서드 추출** 대화 상자가 나타납니다.  
  
     또는 입력할 수도 있습니다 바로 가기 키 CTRL + R, M을 표시 합니다 **메서드 추출** 대화 상자.  
  
     선택한 스키마 코드를 가리킵니다 **리팩터링**를 클릭 하 고 **메서드 추출** 표시 하는 **메서드 추출** 대화 상자.  
  
4. 와 같이 새 메서드의 이름을 지정 `CircleArea`를 **새 메서드 이름을** 상자입니다.  
  
     새 메서드 서명 미리 보기가 표시 됩니다 **메서드 서명 미리 보기**합니다.  
  
5. **확인**을 클릭합니다.  
  
## <a name="remarks"></a>설명  
 사용 하는 경우는 **메서드 추출** 명령을 새 메서드를 동일한 클래스의 소스 멤버 뒤에 삽입 됩니다.  
  
## <a name="partial-types"></a>부분 형식(Partial Type)  
 클래스 형식인 경우 부분에 다음 **메서드 추출** 원본 멤버 바로 뒤에 새 메서드를 생성 합니다. **메서드 추출** 인스턴스 데이터가 없는 새 메서드의 코드에서 참조 될 때 정적 메서드를 만드는 새 메서드 시그니처를 확인 합니다.  
  
## <a name="generic-type-parameters"></a>제네릭 형식 매개 변수  
 제한 되지 않은 제네릭 형식 매개 변수가 있는 메서드를 추출 하는 경우 생성 된 코드를 추가 하지 것입니다는 `ref` 해당 매개 변수에 한정자 값을 할당 하지 않으면. 추출된 된 메서드의 제네릭 형식 인수로 참조 형식을 지원할 경우 수동으로 추가 해야 합니다 `ref` 메서드 시그니처에서 매개 변수에 한정자입니다.  
  
## <a name="anonymous-methods"></a>무명 메서드  
 선언 되거나 무명 메서드에서 외부에서 참조 되는 로컬 변수에 대 한 참조를 포함 하는 무명 메서드의 부분을 추출 하려는 경우 다음 Visual Studio는 경고를 표시 잠재적인 의미 변경 사항에 대 한 합니다.  
  
 무명 메서드는 로컬 변수의 값을 사용 하는 값은 익명 메서드가 실행 될 시점 가져옵니다. 무명 메서드를 다른 메서드로 추출할 때 지역 변수 값은 추출 된 메서드를 호출 하는 시점에 가져옵니다.  
  
 다음 예제에서는이 의미 체계 변경 합니다. 그런 다음이 코드가 실행 될 경우 **11** 콘솔에 표시 됩니다. 사용 하는 경우 **메서드 추출** 영역의 고유한 메서드로 코드 주석으로 표시 되는 코드를 추출 하 고 다음 리팩터링된 코드를 실행 하려면 **10** 콘솔에 표시 됩니다.  
  
```csharp  
class Program  
{  
    delegate void D();  
    D d;  
    static void Main(string[] args)  
    {  
        Program p = new Program();  
        int i = 10;  
        /*begin extraction*/  
            p.d = delegate { Console.WriteLine(i++); };  
        /*end extraction*/  
        i++;  
        p.d();  
    }  
}  
```  
  
 이 문제를 해결 하려면 클래스의 무명 메서드 필드에 사용 되는 지역 변수를 확인 합니다.  
  
## <a name="see-also"></a>관련 항목  
 [리팩터링(C#)](../csharp-ide/refactoring-csharp.md)