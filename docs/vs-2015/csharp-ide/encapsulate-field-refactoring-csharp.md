---
title: 필드 캡슐화 리팩터링 (C#) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vs.csharp.refactoring.encapsulatefield
dev_langs:
- CSharp
helpviewer_keywords:
- Encapsulate Field refactoring operation [C#]
- refactoring [C#], Encapsulate Field
ms.assetid: bf714a04-ab1e-49ce-99ce-dda1ebb1a17f
caps.latest.revision: 26
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 0e2ad3b2d89db83d3b9fa38438abdbde61e72bfe
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65681382"
---
# <a name="encapsulate-field-refactoring-c"></a>필드 캡슐화 리팩터링(C#)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

합니다 **필드 캡슐화** 신속 하 게 속성에서 기존 필드를 만들고 다음 새 속성에 대 한 참조를 사용 하 여 코드를 원활 하 게 업데이트할 수 있습니다 리팩터링 작업 합니다.  
  
 경우는 [필드](https://msdn.microsoft.com/library/3cbb2f61-75f8-4cce-b4ef-f5d1b3de0db7) 됩니다 [공용](https://msdn.microsoft.com/library/0ae45d16-a551-4b74-9845-57208de1328e), 다른 개체 해당 필드에 직접 액세스할 수 있으며 수정할 수는 필드를 소유 하는 개체에 의해 감지 되지 않습니다. 사용 하 여 [속성](https://msdn.microsoft.com/library/e295a8a2-b357-4ee7-a12e-385a44146fa8) 해당 필드를 캡슐화 할 필드에 직접 액세스를 차단할 수 있습니다.  
  
 새 속성을 만들려면 합니다 **필드 캡슐화** 작업을 캡슐화 할 필드에 대 한 액세스 한정자 변경 [개인](https://msdn.microsoft.com/library/654c0bb8-e6ac-4086-bf96-7474fa6aa1c8), 한 다음 생성 [가져오기](https://msdn.microsoft.com/library/a52de048-fbe0-41b0-82ec-8e4ac04d3a71)하 고 [설정](https://msdn.microsoft.com/library/30d7e4e5-cc2e-4635-a597-14a724879619) 해당 필드에 대 한 접근자입니다. 필드가 읽기 전용으로 선언되는 경우와 같이 몇몇 경우에는 `get` 접근자만 생성됩니다.  
  
 리팩터링 엔진에서 지정 된 영역에 새 속성에 대 한 참조를 사용 하 여 코드를 업데이트 합니다 **참조 업데이트** 섹션을 **필드 캡슐화** 대화 상자.  
  
### <a name="to-create-a-property-from-a-field"></a>필드에서 속성을 만들려면  
  
1. `EncapsulateFieldExample`이라는 콘솔 애플리케이션을 만들고 `Program`을 다음 예제 코드로 바꿉니다.  
  
    ```csharp  
    class Square  
    {  
        // Select the word 'width' and then use Encapsulate Field.  
        public int width, height;  
    }  
    class MainClass  
    {  
        public static void Main()  
        {  
            Square mySquare = new Square();  
            mySquare.width = 110;  
            mySquare.height = 150;  
            // Output values for width and height.  
            Console.WriteLine("width = {0}", mySquare.width);  
            Console.WriteLine("height = {0}", mySquare.height);  
        }  
    }  
    ```  
  
2. 에 [코드 편집기](../ide/writing-code-in-the-code-and-text-editor.md)를 캡슐화 할 필드의 이름을 선언에 커서를 놓습니다. 아래 예제에서 커서를 단어 `width`에 배치합니다.  
  
    ```csharp  
    public int width, height;  
    ```  
  
3. 에 **리팩터링** 메뉴에서 클릭 **필드 캡슐화**합니다.  
  
     합니다 **필드 캡슐화** 대화 상자가 나타납니다.  
  
     바로 가기 키 CTRL + R, E 표시를 입력할 수도 있습니다는 **필드 캡슐화** 대화 상자.  
  
     커서를 마우스 오른쪽 단추로 클릭 가리킵니다 **리팩터링**를 클릭 하 고 **필드 캡슐화** 표시 하는 **필드 캡슐화** 대화 상자.  
  
4. 설정을 지정합니다.  
  
5. Enter 키를 누르거나 클릭 합니다 **확인** 단추입니다.  
  
6. 선택한 경우에 **참조 변경 미리 보기** 옵션을 해당 **참조 변경 미리 보기** 창이 열립니다. 클릭 합니다 **적용** 단추입니다.  
  
     다음 `get` 및 `set` 접근자 코드가 소스 파일에 표시됩니다.  
  
    ```csharp  
    public int Width  
    {  
        get { return width; }  
        set { width = value; }  
    }  
    ```  
  
     `Main` 메서드의 코드도 새 `Width` 속성 이름으로 업데이트됩니다.  
  
    ```csharp  
    Square mySquare = new Square();  
    mySquare.Width = 110;  
    mySquare.height = 150;  
    // Output values for width and height.  
    Console.WriteLine("width = {0}", mySquare.Width);  
    ```  
  
## <a name="remarks"></a>설명  
 합니다 **필드 캡슐화** 작업은 커서가 필드 선언과 같은 줄에 경우에 가능 합니다.  
  
 여러 필드를 선언 하는 선언의 **필드 캡슐화** 쉼표를 사용 하 여 필드를 구분 하 고 커서와 가장 가까이 있는 필드 및 커서와 같은 줄에서 리팩터링을 시작 합니다. 선언에서 필드 이름을 선택하여 캡슐화할 필드를 지정할 수도 있습니다.  
  
 이 리팩터링 작업으로 생성된 코드는 필드 캡슐화 코드 조각 기능을 통해 모델링됩니다. 코드 조각은 수정 가능합니다. 자세한 내용은 [코드 조각](../ide/code-snippets.md)을 참조하세요.  
  
## <a name="see-also"></a>참고 항목  
 [리팩터링(C#)](../csharp-ide/refactoring-csharp.md)   
 [Visual C# 코드 조각](../ide/visual-csharp-code-snippets.md)