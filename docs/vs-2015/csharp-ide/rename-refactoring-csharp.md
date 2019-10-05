---
title: 이름 바꾸기 리팩터링 (C#) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vs.csharp.refactoring.rename
dev_langs:
- CSharp
helpviewer_keywords:
- refactoring [C#], Rename
- Rename refactoring [C#]
ms.assetid: 268942fc-b142-4dfa-8d90-bedd548c2e4f
caps.latest.revision: 45
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 3f1c31d858fbe7a5183456bfc7fcc1e602d4e051
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65686033"
---
# <a name="rename-refactoring-c"></a>이름 바꾸기 리팩터링(C#)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**이름 바꾸기** 필드, 지역 변수, 메서드, 네임 스페이스, 속성 및 형식 같은 코드 기호의 식별자 이름을 변경 하는 쉬운 방법을 제공 하는 Visual Studio 통합된 개발 환경 (IDE)의 리팩터링 기능입니다. **이름 바꾸기** 주석에서 문자열의 이름을 변경 하 고 선언 및 호출 식별자를 변경 하려면 사용할 수 있습니다.  
  
> [!NOTE]
> Visual Studio에 대 한 소스 제어를 사용 하는 경우 이름 바꾸기 리팩터링을 수행 하려고 하기 전에 최신 버전을의 소스를 가져옵니다.  
  
 이름 바꾸기 리팩터링 하는 것은 다음 Visual Studio 기능에서 사용할 수 있습니다.  
  
|기능|IDE에서의 리팩터링의 동작|  
|-------------|----------------------------------------|  
|코드 편집기|코드 편집기에서 이름 바꾸기 리팩터링 경우 사용할 수 있는 특정 형식의 코드 기호에서 커서를 놓습니다. 커서가이 위치에 있는 경우 호출할 수 있습니다 합니다 **이름 바꾸기** 바로 가기 키 (CTRL + R, CTRL + R)를 입력 하거나 선택 하 여 명령을 합니다 **이름 바꾸기** 명령을 스마트 태그, 바로 가기 메뉴 또는 합니다  **리팩터링** 메뉴.|  
|클래스 뷰|이름 바꾸기 리팩터링 하는 바로 가기 메뉴에서 사용할 수 있는 클래스 뷰에서 식별자를 선택 하는 경우 및 **리팩터링** 메뉴.|  
|개체 브라우저|개체 브라우저에서 식별자를 선택 하면 이름 바꾸기 리팩터링은 에서만 사용할 수는 **리팩터링** 메뉴.|  
|Windows Forms 디자이너의 속성 표|에 **속성 표에서** Windows Forms 디자이너의 컨트롤의 이름을 변경 작업이 시작 됩니다 이름 바꾸기는 컨트롤에 대 한 합니다. 합니다 **이름 바꾸기** 대화 상자가 나타나지 것입니다.|  
|솔루션 탐색기|**솔루션 탐색기**, **이름 바꾸기** 바로 가기 메뉴에서 사용할 수 있는 명령입니다. 선택한 소스 파일 클래스 이름이 파일 이름을 동일 클래스에 있으면 동시에 소스 파일 이름 바꾸기 및 이름 바꾸기 리팩터링 실행이 명령을 사용할 수 있습니다.<br /><br /> 예를 들어, 기본 Windows 기반 응용 프로그램을 만들고 Form1.cs TestForm.cs의 이름을 소스 파일 이름을 Form1.cs TestForm.cs를 Form1 클래스 바뀝니다 및 대 한 모든 참조 클래스 TestForm로 변경 됩니다. **참고:**  합니다 **실행 취소** 명령 (CTRL + Z)만 코드에서 이름 바꾸기 리팩터링을 취소 되며 파일 이름을 원래 이름으로 다시 변경 하지는 것입니다. <br /><br /> 선택한 소스 파일에 클래스 파일 이름으로 동일한 이름이 없는 경우는 **이름 바꾸기** 명령을 **솔루션 탐색기** 소스 파일의 이름만 바꿀 됩니다 및 이름 바꾸기는 실행 되지 것입니다 리팩터링 합니다.|  
  
## <a name="rename-operations"></a>이름 바꾸기 작업  
 실행할 때 **이름 바꾸기**, 리팩터링 엔진은 다음 표에 설명 된 대로 각 코드 기호에 관련 된 이름 바꾸기 작업을 수행 합니다.  
  
|코드 기호|작업 이름 바꾸기|  
|-----------------|----------------------|  
|필드|새 이름으로 선언 및 필드의 용도 변경합니다.|  
|지역 변수|선언과 변수 사용을 새 이름으로 변경합니다.|  
|메서드|메서드 및 해당 메서드에 대 한 모든 참조의 이름을 새 이름으로 변경합니다. **참고:**  확장 메서드를 바꾸면 메서드의 확장 메서드가 정적 메서드 또는 인스턴스 메서드로 되 여부에 관계 없이 범위에 있는 모든 인스턴스 이름 바꾸기 작업 전파 됩니다. 자세한 내용은 [확장 메서드](https://msdn.microsoft.com/library/175ce3ff-9bbf-4e64-8421-faeb81a0bb51)를 참조하세요.|  
|네임스페이스|선언에서 새 이름으로 네임 스페이스의 이름을 변경 모든 `using` 문 및 정규화 된 이름입니다. **참고:**  네임 스페이스의 이름을 바꾸면 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 도 업데이트를 **Default Namespace** 속성에는 **응용 프로그램** 페이지를 **프로젝트 디자이너**. 이 속성을 선택 하 여 다시 설정할 수 없습니다 **실행 취소** 에서 합니다 **편집** 메뉴. 다시 설정 하는 **Default Namespace** 속성 값에서 속성을 수정 해야 합니다 **프로젝트 디자이너**합니다. 자세한 내용은 [응용 프로그램 페이지](../ide/reference/application-page-project-designer-csharp.md)합니다.|  
|속성|선언 및 사용 된 속성의 새 이름으로 변경합니다.|  
|형식|생성자 및 소멸자를 포함 하 여 새 이름에 모든 선언 및 형식의 모든 용도 변경 합니다. 부분 형식에 대 한 이름 바꾸기 작업은 모든 부분에 전파 됩니다.|  
  
#### <a name="to-rename-an-identifier"></a>식별자의 이름을 바꾸려면  
  
1. `RenameIdentifier`이라는 콘솔 애플리케이션을 만들고 `Program`을 다음 예제 코드로 바꿉니다.  
  
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
  
3. **리팩터링** 메뉴에서 **이름 바꾸기**합니다. 합니다 **이름 바꾸기** 대화 상자가 나타납니다.  
  
     커서를 마우스 오른쪽 단추로 클릭 가리킵니다 **리팩터링** 상황에 맞는 메뉴를 클릭 한 다음 **이름 바꾸기** 표시 하는 **이름 바꾸기** 대화 상자.  
  
4. 에 **새 이름을** 필드에 입력 `MethodC`합니다.  
  
5. 선택 된 **주석에서 검색** 확인란 합니다.  
  
6. **확인**을 클릭합니다.  
  
7. 에 **변경 내용 미리 보기** 대화 상자, 클릭 **적용**합니다.  
  
#### <a name="to-rename-an-identifier-using-smart-tags"></a>스마트 태그를 사용 하 여 식별자 이름을 바꾸려면  
  
1. `RenameIdentifier`이라는 콘솔 애플리케이션을 만들고 `Program`을 다음 예제 코드로 바꿉니다.  
  
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
  
2. 선언에 `MethodB`, 형식 또는 메서드 식별자 백스페이스 키입니다. 이 식별자 아래에 스마트 태그 프롬프트가 표시 됩니다.  
  
    > [!NOTE]
    > 이름 바꾸기 리팩터링 스마트 태그를 사용 하 여 한 식별자 선언에만 호출할 수 있습니다.  
  
3. SHIFT + ALT + F10 바로 가기 키를 입력 하 고 스마트 태그 메뉴에 표시할 아래쪽 화살표를 누릅니다.  
  
     또는  
  
     스마트 태그를 표시 하는 스마트 태그 메시지 위로 마우스 포인터를 이동 합니다. 스마트 태그 위에 마우스 포인터를 이동 하 고 스마트 태그 메뉴에 표시할 아래쪽 화살표를 클릭 합니다.  
  
4. 선택 된 **이름 바꾸기 '\<identifer1 >'를 '\<identifier2 >'** 메뉴 항목 이름 바꾸기 리팩터링 코드의 변경 내용 미리 보기 없이 호출을 합니다. 에 대 한 모든 참조가  **\<identifer1 >** 으로 자동 업데이트 됩니다  **\<identifier2 >** 합니다.  
  
     또는  
  
     선택 합니다 **미리 보기를 사용 하 여 이름 바꾸기** 메뉴 항목을 코드의 변경 내용 미리 보기를 사용 하 여 이름 바꾸기 리팩터링을 호출 합니다. 합니다 **변경 내용 미리 보기** 대화 상자가 표시 됩니다.  
  
## <a name="remarks"></a>설명  
  
## <a name="renaming-implemented-or-overridden-members"></a>구현 또는 재정의 된 멤버 이름 바꾸기  
 경우 있습니다 **이름 바꾸기** 구현/재정의 하거나 멤버를 다른 형식에 의해 구현 된/재정의 되는 멤버 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 이름 바꾸기 작업 연속 업데이트 하면 라는 대화 상자가 표시 됩니다. 클릭 하면 **계속**, 리팩터링 엔진 재귀적으로 찾아 자료의 모든 멤버의 이름을 바꿉니다 및 파생된 형식의 구현/재정의 관계 이름이 되 고 멤버를 사용 하 여 합니다.  
  
 다음 코드 예제에서는 구현/재정의 관계를 사용 하 여 멤버를 포함합니다.  
  
 [!code-csharp[CsUsingCsIDERefactor#1](../snippets/csharp/VS_Snippets_VBCSharp/CsUsingCsIDERefactor/CS/Class1.cs#1)]  
  
 이전 예제에서는 이름 바꾸기 `C.Method()` 도 이름을 바꿉니다 `Ibase.Method()` 있으므로 `C.Method()` 구현 `Ibase.Method()`합니다. 다음으로, 리팩터링 엔진 재귀적으로 않는지 `Ibase.Method()` 에 의해 구현 됩니다 `Derived.Method()` 바꿉니다 `Derived.Method()`합니다. 리팩터링 엔진은 바뀌지 않습니다 `Base.Method()`이므로 `Derived.Method()` 덮어쓰지 않습니다 `Base.Method()`합니다. 리팩터링 엔진 중지 여기 없다면 **오버 로드를 이름 바꾸기** 체크 인 합니다 **이름 바꾸기** 대화 상자.  
  
 하는 경우 **오버 로드를 이름 바꾸기** 을 선택 하면 리팩터링 엔진의 이름을 바꿉니다 `Derived.Method(int i)` 오버 로드 하므로 `Derived.Method()`를 `Base.Method(int i)` 에 의해 재정의 됩니다 `Derived.Method(int i)`, 및 `Base.Method()` 오버 로드 이므로 `Base.Method(int i)`.  
  
> [!NOTE]
> 참조 된 어셈블리에 정의 된 멤버의 이름을 바꾸면 이름을 변경 하면 빌드 오류가 발생 됩니다 대화 상자를 설명 합니다.  
  
## <a name="renaming-properties-of-anonymous-types"></a>익명 형식의 속성 이름 바꾸기  
 익명 형식에서 속성의 이름을 바꾸면 이름 바꾸기 작업은 동일한 속성이 있는 다른 익명 형식의 속성에 전파 됩니다. 다음 예제에서는이 동작을 보여 줍니다.  
  
```csharp  
var a = new { ID = 1};  
var b = new { ID = 2};  
```  
  
 위의 코드에서 이름 바꾸기 `ID` 바뀝니다 `ID` 문 모두에서 동일한 기본 익명 형식을 가지 지 않으므로 합니다.  
  
```csharp  
var companyIDs =  
    from c in companylist  
    select new { ID = c.ID, Name = c.Name};  
  
var orderIDs =  
    from o in orderlist  
    select new { ID = o.ID, Item = o.Name};  
```  
  
 위의 코드에서 이름 바꾸기 `ID` 인스턴스의 이름을 `ID` 있으므로 `companyIDs` 및 `orderIDs` 동일한 속성을 포함 하지.  
  
## <a name="see-also"></a>참고 항목  
 [리팩터링(C#)](../csharp-ide/refactoring-csharp.md)   
 [익명 형식](https://msdn.microsoft.com/library/59c9d7a4-3b0e-475e-b620-0ab86c088e9b)