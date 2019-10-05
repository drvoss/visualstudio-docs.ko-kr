---
title: 성능 경고 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.performancerules
helpviewer_keywords:
- warnings, performance
- performance warnings
- performance, warnings
- managed code analysis warnings, performance warnings
ms.assetid: e014ac3a-02e6-46d9-942c-3491dd63782f
caps.latest.revision: 24
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 3f942a83754828888232091cf9b0c2c48566ce15
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68201240"
---
# <a name="performance-warnings"></a>성능 경고
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

성능 경고는 고성능 라이브러리 및 응용 프로그램을 지원합니다.  
  
## <a name="in-this-section"></a>섹션 내용  
  
|규칙|설명|  
|----------|-----------------|  
|[CA1800: 불필요 하 게 캐스팅 하지 마십시오](../code-quality/ca1800-do-not-cast-unnecessarily.md)|중복 캐스팅을 수행하면 성능이 저하됩니다. 특히 간단한 반복 문에서 캐스팅이 수행될 때 더욱 그러합니다.|  
|[CA1801: 사용 되지 않는 매개 변수를 검토](../code-quality/ca1801-review-unused-parameters.md)|메서드 시그니처에 메서드 본문에서 사용되지 않는 매개 변수가 있습니다.|  
|[CA1802: 리터럴을 사용 하십시오.](../code-quality/ca1802-use-literals-where-appropriate.md)|정적 및 읽기 전용 필드가 선언 되었습니다 (Shared 및 ReadOnly에서 [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]), 컴파일 시간에 계산할 수 있는 값으로 초기화 됩니다. 컴파일 시간에 대상된 필드에 할당 되는 값을 계산할 이기 때문에 const 선언을 변경 (에서 Const [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]) 필드 값을 런타임 대신 컴파일 시간에 계산 되도록 합니다.|  
|[CA1804: 사용 되지 않는 로컬 항목을 제거](../code-quality/ca1804-remove-unused-locals.md)|사용되지 않는 지역 변수와 불필요한 할당으로 어셈블리의 크기가 증가하고 성능이 저하될 수 있습니다.|  
|[CA1806: 메서드 결과 무시 하지 마십시오](../code-quality/ca1806-do-not-ignore-method-results.md)|새 개체가 만들어지지만 사용 되지 않거나, 만들고 새 문자열을 반환 하는 메서드를 호출 하 고 새 문자열은 사용 되지 않거나, 또는 구성 요소 개체 모델 (COM) 또는 P/Invoke 메서드를 사용 되지 않는 HRESULT 또는 오류 코드를 반환 합니다.|  
|[CA1809: 과도 한 지역 변수를 방지 합니다.](../code-quality/ca1809-avoid-excessive-locals.md)|값을 메모리가 아닌 프로세서 레지스터에 저장하는 방법은 성능 최적화에 많이 사용되는 방법이며 "값의 레지스터 등록"이라고도 합니다.  모든 지역 변수에 레지스터는 가능성을 늘리려면 64 로컬 변수 수를 제한 합니다.|  
|[CA1810: 참조 형식 정적 필드를 인라인으로 초기화](../code-quality/ca1810-initialize-reference-type-static-fields-inline.md)|형식이 명시적인 정적 생성자를 선언하면 JIT(Just-in-Time) 컴파일러는 형식의 각 정적 메서드와 인스턴스 생성자에 검사를 추가하여 정적 생성자를 이전에 호출했는지 확인합니다. 정적 생성자 검사로 인해 성능이 저하될 수 있습니다.|  
|[CA1811: 호출 되지 않는 전용 코드를 방지 합니다.](../code-quality/ca1811-avoid-uncalled-private-code.md)|Private 또는 internal (어셈블리 수준) 멤버는 어셈블리의 호출자가 없는, 공용 언어 런타임에 의해 호출 되지 않습니다 및 대리자에 의해 호출 되지 않습니다.|  
|[CA1812: 인스턴스화되지 않은 내부 클래스를 방지 합니다.](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)|어셈블리 수준 형식의 인스턴스가 어셈블리에서 코드에 의해 만들어지지 않습니다.|  
|[CA1813: 봉인 되지 않은 특성](../code-quality/ca1813-avoid-unsealed-attributes.md)|[!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 클래스 라이브러리는 사용자 지정 특성을 검색하는 메서드를 제공합니다. 기본적으로 이러한 메서드는 특성 상속 계층을 검색합니다. 특성을 봉인하면 상속 계층을 검색하지 않으므로 성능이 향상될 수 있습니다.|  
|[CA1814: 다차원 보다 가변 배열을 사용합니다](../code-quality/ca1814-prefer-jagged-arrays-over-multidimensional.md)|가변 배열의 요소에는 배열이 사용됩니다. 요소를 구성 하는 배열의 일부 데이터 집합에는 발생할 수 있는 다양 한 일 수 있습니다.|  
|[CA1815: 값 형식에서 Equals 또는 같음 연산자 재정의](../code-quality/ca1815-override-equals-and-operator-equals-on-value-types.md)를 참조하세요.|값 형식의 경우 Equals의 상속된 구현에서 Reflection 라이브러리를 사용하며 모든 필드의 내용을 비교합니다. Reflection에는 많은 계산이 요구되며 모든 필드의 일치 여부를 비교하는 것이 불필요할 수 있습니다. 사용자가 인스턴스를 비교 또는 정렬하거나 인스턴스를 해시 테이블 키로 사용할 것으로 예측되는 경우에는 값 형식에서 Equals를 구현해야 합니다.|  
|[CA1816: GC를 호출 합니다. SuppressFinalize 올바르게](../code-quality/ca1816-call-gc-suppressfinalize-correctly.md)|Dispose 구현인 메서드가 GC를 호출 하지 않습니다. Dispose 구현이 아닌 메서드나 SuppressFinalize, GC를 호출 합니다. GC SuppressFinalize, 또는 메서드를 호출합니다. SuppressFinalize이 이외의 값을 전달 하 고 (Me in [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]).|  
|[CA1819: 속성은 배열을 반환 해서는](../code-quality/ca1819-properties-should-not-return-arrays.md)|속성에 의해 반환 된 배열은 속성이 읽기 전용인 경우에는 읽기 전용인 지 않습니다. 배열을 무단으로 변경하지 못하도록 하려면 속성에서 배열의 복사본을 반환해야 합니다. 일반적으로 사용자는 이러한 속성을 호출할 경우 성능에 부정적인 영향을 준다는 것을 인식하지 못합니다.|  
|[CA1820: 문자열 길이 사용 하 여 문자열이 비었는지 테스트](../code-quality/ca1820-test-for-empty-strings-using-string-length.md)|String.Length 속성이나 String.IsNullOrEmpty 메서드를 사용하여 문자열을 비교하는 것이 Equals를 사용하는 것보다 훨씬 더 빠릅니다.|  
|[CA1821: 빈 종료자를 제거하십시오.](../code-quality/ca1821-remove-empty-finalizers.md)|개체 수명을 추적할 때에는 추가로 성능 오버헤드가 발생하므로 가능한 경우 종료자를 사용하지 마십시오. 빈 종료자 발생 아무런 장점 없이 오버 헤드를 추가 합니다.|  
|[CA1822: 멤버를 static으로 표시](../code-quality/ca1822-mark-members-as-static.md)|인스턴스 데이터에 액세스하지 않거나 인스턴스 메서드를 호출하지 않는 멤버는 static([!INCLUDE[vbprvb](../includes/vbprvb-md.md)]의 경우 Shared)으로 표시할 수 있습니다. 메서드를 static으로 표시하면 컴파일러는 이러한 멤버에 대한 비가상 호출 사이트를 내보냅니다. 이 경우 성능이 중요한 코드에서 성능이 크게 향상될 수 있습니다.|  
|[CA1823: 사용 되지 않는 전용 필드를 방지 합니다.](../code-quality/ca1823-avoid-unused-private-fields.md)|어셈블리에서 액세스되지 않는 것으로 보이는 전용 필드가 발견되었습니다.|  
|[CA1824: NeutralResourcesLanguageAttribute로 어셈블리 표시](../code-quality/ca1824-mark-assemblies-with-neutralresourceslanguageattribute.md)|NeutralResourcesLanguage 특성을 사용하여 어셈블리에 대한 중립 문화권의 리소스를 표시하는 데 사용된 언어를 ResourceManager에 알릴 수 있습니다. 이렇게 하면 로드한 첫 리소스에 대한 찾기 성능을 향상시킬 수 있으며 작업이 간단해집니다.|
