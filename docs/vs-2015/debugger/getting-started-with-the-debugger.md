---
title: 디버거를 시작 하기 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: c763d706-3213-494f-b4d2-990b6e1ec456
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e093abd5e836bcb7ee236979c00d574a07ecfd3d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68202351"
---
# <a name="getting-started-with-the-debugger"></a>디버거 시작
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio 디버거는 모든 언어에서 쉽게 사용할 수 있습니다. 여기서는 간단한 C# 프로그램을 디버그하는 방법을 보여 주겠지만 C++ 및 JavaScript와 같은 다른 언어의 코드에 동일한 단계를 적용할 수 있습니다.  
  
## <a name="BKMK_Start_debugging_a_VS_project"></a> 기본 C# 프로젝트 디버그  
 간단한 C# 콘솔 응용 프로그램부터 시작 하겠습니다 (**파일 / 새로 만들기 / 프로젝트**을 선택한 후 **Visual C#** 선택한 후 **콘솔 응용 프로그램**). Visual Studio를 사용 하 여 적 경우 [연습: 간단한 응용 프로그램](../ide/walkthrough-create-a-simple-application-with-visual-csharp-or-visual-basic.md)합니다. 합니다 **Main** 메서드 방금 10 번을 정수 변수에 1을 추가 하 고 결과를 콘솔에 출력 합니다.  
  
```csharp  
static void Main(string[] args)  
{  
    int testInt = 0;  
    for (int i = 1; i <= 10; i++)  
    {  
        testInt += 1;  
    }  
    Console.WriteLine(testInt);  
}  
```  
  
 이 코드를 작성 합니다 **디버그** 구성 합니다. 이 구성은 기본적으로 설정되어 있습니다. 구성에 대 한 자세한 내용은 참조 하세요. [빌드 구성 이해](../ide/understanding-build-configurations.md)합니다.  
  
 클릭 하 여 디버거에서이 코드를 실행할 **디버그 / 디버깅 시작** (또는 **시작** 도구 모음에서 나 **F5**). 애플리케이션이 거의 즉시 종료되므로 콘솔 창에 무엇인가 인쇄되었는지 여부는 사실 알 수 없습니다.  
  
 중단점을 설정한 다음 미리 단계별로 실행하면 콘솔 창을 보기에 충분한 시간 동안 실행을 중지할 수 있습니다. 중단점을 설정 하려면에 커서를 놓습니다 합니다 `Console.WriteLine` 줄을 클릭 **디버그 / 새 중단점 / 함수 중단점**, 하거나 같은 줄에서 왼쪽 여백을 클릭 하면 됩니다. 중단점은 다음과 같은 모습입니다.  
  
 ![중단점을 설정](../debugger/media/getstartedbreakpoint.png "GetStartedBreakpoint")  
  
 중단점에 대 한 자세한 내용은 참조 하세요. [중단점 사용](../debugger/using-breakpoints.md)합니다.  
  
## <a name="BKMK_Inspect_Variables"></a> 변수 검사  
 종종 디버깅 특정 지점에서 예상한 값을 포함 하지 않는 변수를 찾는 포함 됩니다. 에서는 일부의 변수를 검사할 수 있는 방법을 보여줍니다.  
  
 다시 디버그를 시작합니다. `Console.WriteLine` 코드가 실행되기 전에 실행이 중지됩니다. 미리 단계별로 실행 되도록 하 여 실행 되도록 할 수 있습니다 (클릭 **디버그 / 단계 Over** 하거나 **F10**). 이 경우 선택 했을 것 **단계씩** (**F11**) 동일한 결과; 및 차이 나중에 설명 합니다. 메서드의 마지막 중괄호로 묶인 선이 노란색으로 변해야 합니다. 콘솔 창을 봅니다. 나타납니다 **10**합니다.  
  
 마우스로 가리키면 합니다 **testInt** 값을 보려면 현재 데이터 팁에서 변수입니다.  
  
 ![DBG&#95;Basics&#95;Data&#95;Tips](../debugger/media/dbg-basics-data-tips.png "DBG_Basics_Data_Tips")  
  
 코드 창 바로 아래 표시 된 **자동**, **지역**, 및 **조사식** windows. 이러한 창에는 실행 당시의 변수에 대한 현재 값이 표시됩니다. 모두를 **자동** 하며 **지역** windows 표시 **testInt** 값을 사용 하 여 **10**합니다.  
  
 ![디버깅할 때 자동 창](../debugger/media/getstartedwindows.png "GetStartedWindows")  
  
 이러한 창에 대 한 자세한 내용은 참조 하세요. [자동 및 지역 Windows](../debugger/autos-and-locals-windows.md)합니다.  
  
 프로그램을 진행함에 따라 변수 값이 어떻게 변경되는지 살펴보겠습니다. 에 중단점을 설정 합니다 `testInt += 1;` 줄 및 디버깅을 다시 시작 합니다. 것을 확인할 수 **testInt** 에 **지역** 및 **자동** windows **0**, 및 **합니까** 는**1**합니다. 디버깅을 계속할 경우 (**디버그 / 계속**, 또는 **계속** 도구 모음에서 또는 **F5**)를 볼 수 있습니다 변수의 **testInt** 변경 내용 **1**, 한 다음 **2**등. 이러한 변경 내용을 볼 수 있는 힘들 면 중단점을 제거 합니다. (**디버그 / 설정/해제 중단점**, 여백을 클릭 하거나)을 하 고 계속 디버깅 합니다. 모든 중단점을 제거 하려면 클릭 **디버그 / 모든 중단점 삭제**, 또는 **CTRL + SHIFT + F9**를 클릭 하 고 **예** 묻는 대화 상자에서 **수행 모든 중단점을 제거 하 시겠습니까?** .  
  
## <a name="stepping-into-and-over-function-calls"></a>함수 호출을 한 단계씩 코드 실행 및 프로시저 단위 실행  
 문에서 디버거 문이-에서-코드를 실행할 수 있습니다 (**단계씩**) 하거나 디버거에서 함수를 생략 하는 동안 코드를 실행할 수 있습니다 (**단계씩**) (에 더 관심이 있다고 하는 코드를 신속 하 게 함수 코드는 여전히 실행). 두 방법 모두에 같은 디버깅 세션 간에 전환할 수 있습니다.  
  
 간의 차이 보려면 **한 단계씩 코드 실행** 하 고 **프로시저 단위 실행**, 다른 메서드에 의해 호출 되는 메서드를 추가 해야 합니다. C# 애플리케이션에 메서드를 추가하고 Main 메서드에서 호출합니다. 코드는 다음과 비슷합니다.  
  
```csharp  
static void Main(string[] args)  
{  
    Method1();  
    Console.WriteLine("end");  
}  
  
private static void Method1()  
{  
    Console.WriteLine("in Method1");  
}  
```  
  
 Main 메서드에서 `Method1();` 호출에 중단점을 설정하고 디버그를 시작합니다. 실행이 중단 되 면 클릭 **디버그 / 한 단계씩 코드 실행** (또는 **단계씩** 도구 모음에서 나 **F11**). Method1()의 첫 번째 중괄호에서 실행이 다시 중단됩니다.  
  
 ![코드를 한 단계씩](../debugger/media/getstartedstepinto.png "GetStartedStepInto")  
  
 디버깅을 중지 및 다시 시작 및 실행이 중단점에서 중단 하는 경우 클릭 **디버그 / 단계 Over** (또는 **단계씩** 도구 모음에서 또는 **F10**). 실행이 `Console.WriteLine("end");`에서 다시 중단됩니다.  
  
 디버거로 코드 탐색에 대 한 자세한 내용은 않으려면 [디버거로 코드 탐색](../debugger/navigating-through-code-with-the-debugger.md)합니다.
