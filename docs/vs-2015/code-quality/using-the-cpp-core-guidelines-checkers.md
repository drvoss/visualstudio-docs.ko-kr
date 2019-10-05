---
title: C++ Core Guidelines를 이용한 코드검사 사용 | Microsoft Docs
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.date: 11/15/2016
ms.topic: conceptual
ms.assetid: a2098fd9-8334-4e95-9b8d-bc3da689d9e3
caps.latest.revision: 11
author: mikeblome
ms.author: mblome
manager: jillfra
ms.openlocfilehash: c0fb306cb7326464af847f09b319e8e702c76831
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68142080"
---
# <a name="using-the-c-core-guidelines-checkers"></a>C++ Core Guidelines를 이용한 코드검사 사용
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

C++ Core Guidelines는 이식 가능한 집합 지침, 규칙 및 C++ 전문가가 및 디자이너에서 생성 하는 C++에서 코딩 하는 방법에 대 한 모범 사례입니다.  Visual Studio는 이제 C++ Core Guidelines의 준수에 대 한 코드를 확인 하 고 개선 사항을 제안 받을 분석 도구가 코드에 대 한 추가 규칙을 만드는 추가 패키지를 지원 합니다.  
  
## <a name="the-c-core-guidelines-project"></a>C++ Core Guidelines 프로젝트  
 C++ Core Guidelines를 안전 하 게 하 고 효과적으로 최신 C++를 사용 하는 데는 Bjarne Stroustrup 등에서 생성 합니다. 지침에는 정적 형식 안전성 및 리소스 보안 강조합니다. 제거 하거나 언어의 가장 오류가 발생 하기 쉬운 부분을 최소화 하는 방법을 식별 하며 신뢰할 수 있는 방식으로 코드를 간단 하 게 하는 방법 및 성능이 향상 하는 것이 좋습니다. 이러한 지침 표준 C++ Foundation에서 유지 됩니다. 자세한 내용은 설명서를 참조 [C++ Core Guidelines](http://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines), C++ Core Guidelines 설명서 프로젝트 파일에 액세스 하 고 [GitHub](https://github.com/isocpp/CppCoreGuidelines)합니다.  
  
 Microsoft C++ Core Check 코드 분석 규칙에서 설정 하는 Nuget 패키지를 사용 하 여 프로젝트에 추가할 수 있도록 하 여 C++ Core Guidelines 노력을 지원 합니다. 패키지의 이름은 Microsoft.CppCoreCheck, 및에서 사용할 수 있습니다 [ http://www.nuget.org/packages/Microsoft.CppCoreCheck ](http://www.nuget.org/packages/Microsoft.CppCoreCheck)합니다. 이 패키지는 최신 Visual Studio 2015 업데이트 1을 사용 하 여 설치 해야 해야 합니다.  
  
 또한 패키지는 헤더만 지침 지원 라이브러리 (GSL) 종속성으로 다른 패키지를 설치합니다. GSL에서 GitHub에서 사용할 수 있는 이기도 [ https://github.com/Microsoft/GSL ](https://github.com/Microsoft/GSL)합니다.  
  
## <a name="enable-the-c-core-check-guidelines-in-code-analysis"></a>코드 분석에서 C++ Core Check 지침을 사용 하도록 설정  
 C++ Core Check 코드 분석 도구를 사용 하려면 Visual Studio 내에서 확인 하려는 각 C++ 프로젝트로 Microsoft.CppCoreCheck NuGet 패키지를 설치 합니다.  
  
#### <a name="to-add-the-microsoftcppcorecheck-package-to-your-project"></a>Microsoft.CppCoreCheck 패키지 프로젝트를 추가 하려면  
  
1. **솔루션 탐색기**, 패키지를 추가 하려면 솔루션에서 프로젝트의 상황에 맞는 메뉴를 열려면 마우스 오른쪽 단추로 클릭 합니다. 선택할 **NuGet 패키지 관리** 열려는 합니다 **NuGet 패키지 관리자**합니다.  
  
2. 에 **NuGet 패키지 관리자** 창, Microsoft.CppCoreCheck 검색 합니다.  
  
    ![Nuget 패키지 관리자 창을 CppCoreCheck 패키지를 보여 줍니다](../code-quality/media/cppcorecheck-nuget-window.PNG "CPPCoreCheck_Nuget_Window")  
  
3. Microsoft.CppCoreCheck 패키지를 선택 하 고 다음을 선택 합니다 **설치** 프로젝트에 규칙을 추가 하려면 단추입니다.  
  
   NuGet 패키지를 프로젝트에서 코드 분석을 활성화할 때 호출 되는 프로젝트에 추가 MSBuild.targets 파일을 추가 합니다. .Targets 파일을이 Visual Studio 코드 분석 도구에 추가 확장으로 C++ Core Check 규칙을 추가합니다.  
  
   선택 하 여 프로젝트에서 코드 분석을 사용할 수 있습니다를 **빌드에 코드 분석 사용** 에서 확인란을 선택 합니다 **코드 분석** 섹션을 **속성 페이지** 대화 상자 프로젝트입니다.  
  
   ![코드 분석 일반 설정에 대 한 속성 페이지](../code-quality/media/cppcorecheck-codeanalysis-general.png "CPPCoreCheck_CodeAnalysis_General")  
  
   C++ Core Check 규칙을 사용 하면 코드 분석을 사용 하는 경우 실행 되는 기본 규칙 집합의 일부가 됩니다. 개발 중인 C++ Core Check 규칙 이기 때문에 일부 규칙 모든 코드에 대 한 사용할 준비가 되지 않을 수 있지만 개발 하는 동안 정보를 제공 되지 않을 수 있습니다. 이러한 규칙은 실험적으로 해제 됩니다. 프로젝트 속성에서 해제 또는 실험적 규칙을 실행할 것인지를 선택할 수 있습니다.  
  
   ![코드 분석 확장 설정에 대 한 속성 페이지](../code-quality/media/cppcorecheck-codeanalysis-extensions.png "CPPCoreCheck_CodeAnalysis_Extensions")  
  
   C++ Core Check 규칙 집합을 사용 하지 않도록 설정 하거나, 엽니다는 **속성 페이지** 프로젝트 대화 상자. 아래 **구성 속성**를 확장 하 고 **코드 분석**를 **확장**합니다. 드롭다운 목록 옆에 제어할 **사용 C++ Core Check (릴리스)** 또는 **사용 C++ Core Check (실험적)** , 선택 **예** 또는 **아니요**합니다. **확인**이나 **적용**을 선택하여 변경 내용을 저장합니다.  
  
## <a name="check-types-bounds-and-lifetimes"></a>형식, 범위 및 수명 확인  
 C++ Core Check 패키지에는 현재 검사기에 대 한 포함 합니다 [형식 안전성](http://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines#SS-type), [보안 경계](http://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines#SS-bounds), 및 [수명 안전](http://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines#SS-lifetime) 프로필.  
  
 C++ Core Check 규칙을 찾을 수 있는 문제의 종류의 예는 다음과 같습니다.  
  
```cpp  
// CoreCheckExample.cpp  
// Add CppCoreCheck package and enable code analysis in build for warnings.  
  
int main()  
{  
    int arr[10];           // warning C26494  
    int* p = arr;          // warning C26485  
  
    [[gsl::suppress(bounds.1)]] // This attribute suppresses Bounds rule #1  
    {  
        int* q = p + 1;    // warning C26481 (suppressed)  
        p = q++;           // warning C26481 (suppressed)  
    }  
  
    return 0;  
}  
```  
  
 이 예제에서는 C++ Core Check 규칙을 찾을 수 있는 경고의 일부를 보여 줍니다.  
  
- C26494 규칙 하세요 (type.5 같습니다. 항상 개체를 초기화 합니다.  
  
- C26485 규칙 Bounds.3 같습니다. 배열-포인터 decay 없습니다.  
  
- C26481 규칙 합니다 (bounds.1 같습니다. 포인터 산술 연산을 사용 하지 마세요. 대신 `span`를 사용하세요.  
  
  C++ Core Check 코드 분석 규칙 집합은를 설치 하 고이 코드를 컴파일할 때 사용 하도록 설정 하는 경우 처음 두 개의 경고를 출력 하지만 세 번째 표시 되지 않습니다. 빌드 출력에서 예제 코드는 다음과 같습니다.  
  
  **1 >---빌드 시작: 프로젝트: CoreCheckExample를 구성 합니다. Win32-디버그**  
**----**  
**1 > CoreCheckExample.cpp**  
**1>  CoreCheckExample.vcxproj -> C:\Users\username\documents\visual studio 2015\P**  
**rojects\CoreCheckExample\Debug\CoreCheckExample.exe**  
**1>  CoreCheckExample.vcxproj -> C:\Users\username\documents\visual studio 2015\P**  
**rojects\CoreCheckExample\Debug\CoreCheckExample.pdb (전체 PDB)**  
**c:\users\username\documents\visual studio 2015\projects\corecheckexample\coreche**  
**ckexample\corecheckexample.cpp(6): C26494 경고: 'Arr' 변수가 uninitializ**  
**ed. 항상 개체를 초기화 합니다. (type.5: http://go.microsoft.com/fwlink/p/?Link**  
**ID=620421)**  
**c:\users\username\documents\visual studio 2015\projects\corecheckexample\coreche**  
**ckexample\corecheckexample.cpp(7): C26485 경고: 'Arr' 식: 배열**  
 **포인터 감소 합니다. (bounds.3: http://go.microsoft.com/fwlink/p/?LinkID=620415)**  
**=== 빌드: 1 개 성공, 실패 0, 최신 0, 0 개 건너뜀 ===** 는 C++ Core Guidelines 사항이 향상 하 고 안전한 코드를 작성할 수 있도록 합니다. 그러나 규칙 또는 프로필을 적용 하지 않아야 되는 인스턴스가 있을 경우 쉽습니다 표시 하지 않으려면 코드에서 직접. 사용할 수는 `gsl::suppress` 특성을 검색 하 고 다음 코드 블록에서 규칙의 위반을 보고에서 C++ Core Check를 유지 합니다. 특정 규칙을 표시 하지 않으려면 개별 문을 표시할 수 있습니다. 작성하여 전체 범위 프로필도 억제할 수 있습니다 `[[gsl::suppress(bounds)]]` 특정 규칙 수를 포함 하지 않고 있습니다.  
  
## <a name="use-the-guideline-support-library"></a>지침 지원 라이브러리를 사용 합니다.  
 Microsoft.CppCoreCheck NuGet 패키지는 또한 Microsoft에서 구현한 지침 지원 라이브러리 (GSL)의 포함 된 패키지를 설치 합니다. GSL에서 독립 실행형으로에서 사용할 수도 있습니다 [ http://www.nuget.org/packages/Microsoft.Gsl ](http://www.nuget.org/packages/Microsoft.Gsl)합니다. 이 라이브러리는 핵심 지침을 따라 하려는 경우에 유용 합니다. GSL 오류가 구문 보다 안전한 대체 항목으로 대체할 수 있도록 정의 포함 합니다. 예를 들어 바꿀 수 있습니다는 `T*, length` 쌍을 사용 하 여 매개 변수는 `span<T>` 형식입니다. GSL 이므로 오픈 소스 라이브러리 소스, 주석 또는 문서 작성에 참여를 확인 하려는 경우 프로젝트에서 찾을 수 있습니다 [ https://github.com/Microsoft/GSL ](https://github.com/Microsoft/GSL)합니다.
