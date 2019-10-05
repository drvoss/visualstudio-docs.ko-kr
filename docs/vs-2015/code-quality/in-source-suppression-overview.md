---
title: 소스 비 표시 개요에서 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- source suppression, code analysis
- code analysis, source suppression
ms.assetid: f1a2dc6a-a9eb-408c-9078-2571e57d207d
caps.latest.revision: 42
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: cb2b23dcc01d90bc4365c7d5673e6232229b8d3e
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67826000"
---
# <a name="in-source-suppression-overview"></a>ISS 개요
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

소스에서 추가 하 여 관리 코드에서 코드 분석 위반을 무시 또는 표시 하지 않을 수 있다는 합니다 **SuppressMessage** 위반을 일으키는 코드 세그먼트에는 특성입니다. 합니다 **SuppressMessage** CODE_ANALYSIS 컴파일 기호는 컴파일 타임에 정의 된 경우에 관리 코드 어셈블리의 IL 메타 데이터에 포함 된 조건부 특성입니다.  
  
 C++/CLI에서 CA_SUPPRESS_MESSAGE 또는 CA_GLOBAL_SUPPRESS_MESSAGE 매크로를 헤더 파일에 사용하여 특성을 추가합니다.  
  
 소스에서 메타 데이터를 실수로 전달 하지 않으려면-소스 비 표시 오류 릴리스 빌드에 하지 사용 해야 합니다. 소스에서의 처리 비용으로 인해도 소스에서 메타 데이터를 포함 하 여 대 응용 프로그램의 성능이 저하 될 수 있습니다.  
  
> [!NOTE]
> 전달 하는 데 코드가 없는 이러한 특성 직접. 자세한 내용은 [방법: 메뉴 항목을 사용 하 여 경고 표시 안 함](../code-quality/how-to-suppress-warnings-by-using-the-menu-item.md)합니다. 메뉴 항목을 사용할 수 없는 C++ 코드입니다.  
  
## <a name="suppressmessage-attribute"></a>SuppressMessage 특성  
 코드 분석 경고를 마우스 오른쪽 단추로 클릭할 때 합니다 **오류 목록** 을 클릭 한 다음 **메시지 표시 안 함**, **SuppressMessage** 에 또는 코드에서 특성이 추가 됩니다는 프로젝트의 전역 비 표시 오류 파일입니다.  
  
 합니다 **SuppressMessage** 특성 형식은 다음과 같습니다.  
  
```vb  
<Scope:SuppressMessage("Rule Category", "Rule Id", Justification = "Justification", MessageId = "MessageId", Scope = "Scope", Target = "Target")>  
```  
  
```csharp  
[Scope:SuppressMessage("Rule Category", "Rule Id", Justification = "Justification", MessageId = "MessageId", Scope = "Scope", Target = "Target")]  
  
```  
  
 [C++]  
  
```  
CA_SUPPRESS_MESSAGE("Rule Category", "Rule Id", Justification = "Justification", MessageId = "MessageId", Scope = "Scope", Target = "Target")  
  
```  
  
 각 항목이 나타내는 의미는 다음과 같습니다.  
  
- **규칙 범주** -규칙이 정의 된 범주입니다. 코드 분석 규칙 범주에 대 한 자세한 내용은 참조 하세요. [관리 코드 경고에 대 한 코드 분석](../code-quality/code-analysis-for-managed-code-warnings.md)합니다.  
  
- **규칙 Id** -규칙의 식별자입니다. 지원 규칙 식별자에 대 한 단기 및 장기 이름을 둘 다 포함 됩니다. 짧은 이름은 CAXXXX; 긴 이름은 CAXXXX:FriendlyTypeName입니다.  
  
- **근거** -메시지를 표시 하지 않는 이유를 문서화 하는 데 사용 되는 텍스트입니다.  
  
- **메시지 Id** -각 메시지에 대 한 문제의 고유 식별자입니다.  
  
- **범위** -경고가 표시 되는 대상입니다. 대상 지정 하지 않으면, 대상 특성으로 설정 됩니다. 지원 되는 범위는 다음과 같습니다.  
  
  - Module  

  - 네임스페이스  

  - 리소스  

  - 형식  

  - 멤버  
  
- **대상** -경고가 표시 되는 대상을 지정 하는 데 사용 되는 식별자입니다. 항목 정규화 된 이름을 포함 해야 합니다.  
  
## <a name="suppressmessage-usage"></a>SuppressMessage 사용  
 코드 분석 경고는 수준에 표시 되지 않습니다의 인스턴스를 **SuppressMessage** 특성이 적용 된 합니다. 이 목적은 위반이 발생 하는 코드에 표시 안 함 정보를 하는 것입니다.  
  
 비 표시의 일반적인 형식은 규칙 범주 및 규칙 이름의 선택적 읽을 표현을 포함 하는 규칙 식별자를 포함 합니다. 예를 들면 다음과 같습니다.  
  
 `[SuppressMessage("Microsoft.Design", "CA1039:ListsAreStrongTyped")]`  
  
 소스에서 메타 데이터를 최소화 하기 위한 엄격한 성능상의 이유로 경우 규칙 이름 자체를 생략할 수 있습니다. 규칙 범주 및 해당 규칙 ID 만으로도 충분히 고유 규칙 식별자가 있습니다. 예를 들면 다음과 같습니다.  
  
 `[SuppressMessage("Microsoft.Design", "CA1039")]`  
  
 이 형식은 유지 관리 문제로 인해 권장 되지 않습니다.  
  
## <a name="suppressing-multiple-violations-within-a-method-body"></a>메서드 본문 내에서 여러 위반 표시 안 함  
 특성을 메서드에만 적용할 수 및 메서드 본문 안에 포함할 수 없습니다. 그러나 여러 개 메서드 내에서 위반을 구분 하기 위해 메시지 ID와 식별자를 지정할 수 있습니다.  
  
 [!code-cpp[InSourceSuppression#1](../snippets/cpp/VS_Snippets_CodeAnalysis/InSourceSuppression/cpp/insourcesuppression.cpp#1)]
 [!code-csharp[InSourceSuppression#1](../snippets/csharp/VS_Snippets_CodeAnalysis/InSourceSuppression/cs/InSourceSuppression.cs#1)]
 [!code-vb[InSourceSuppression#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/InSourceSuppression/vb/InSourceSuppression.vb#1)]  
  
## <a name="generated-code"></a>생성된 코드  
 관리 코드 컴파일러 및 일부 타사 도구는 신속한 코드 개발을 용이 하 게 코드를 생성 합니다. 소스 파일에 표시 되는 컴파일러에서 생성 된 코드는 일반적으로 표시 합니다 **GeneratedCodeAttribute** 특성입니다.  
  
 코드 분석 경고 및 생성 된 코드에 대 한 오류를 표시 하지 않을 것인지를 선택할 수 있습니다. 이러한 경고 및 오류를 표시 하지 않는 방법에 대 한 정보를 참조 하세요. [방법: 생성 된 코드에 대 한 경고를 표시 하지 않으려면](../code-quality/how-to-suppress-code-analysis-warnings-for-generated-code.md)합니다.  
  
 코드 분석에서 무시 하는 참고 **GeneratedCodeAttribute** 전체 어셈블리 또는 단일 매개 변수 중 하나에 적용 됩니다. 이러한 상황은 거의 발생 하지 않습니다.  
  
## <a name="global-level-suppressions"></a>전역 수준 비 표시 오류  
 관리 코드 분석 도구를 사용 하는 검사 **SuppressMessage** 어셈블리, 모듈, 형식, 멤버 또는 매개 변수 수준에서 적용 되는 특성입니다. 리소스 및 네임 스페이스에 대 한 위반을 발생 시킵니다. 이러한 위반은 전역 수준에서 적용 해야 합니다는 범위 및 대상으로 합니다. 예를 들어, 다음과 같은 메시지가 표시는 네임 스페이스 위반을 하지 않습니다.  
  
 `[module: SuppressMessage("Microsoft.Design", "CA1020:AvoidNamespacesWithFewTypes", Scope = "namespace", Target = "MyNamespace")]`  
  
> [!NOTE]
> 네임 스페이스 범위를 사용 하 여 경고를 표시 하지 않으려면 자체 네임 스페이스에 대 한 경고를 표시 하지 않습니다. 네임 스페이스 내의 형식에 대 한 경고를 표시 하지 않습니다.  
  
 명시적 범위를 지정 하 여 모든 비 표시 오류를 나타낼 수 있습니다. 이러한 비 표시이 오류 전역 수준에 있어야 합니다. 멤버 수준 비 표시 오류 형식을 데코 레이트 하 여 지정할 수 없습니다.  
  
 전역 수준 비 표시 오류는 유일한 방법은 명시적으로 제공 되는 사용자 소스에 매핑되지 않는 컴파일러에서 생성 된 코드를 참조 하는 메시지가 표시 되지 않습니다. 예를 들어, 다음 코드는 컴파일러에서 내보낸 생성자에 대 한 위반을 표시 하지 않습니다.  
  
 `[module: SuppressMessage("Microsoft.Design", "CA1055:AbstractTypesDoNotHavePublicConstructors", Scope="member", Target="Microsoft.Tools.FxCop.Type..ctor()")]`  
  
> [!NOTE]
> 대상에는 항상 정규화 항목 이름을 포함합니다.  
  
## <a name="global-suppression-file"></a>전역 비 표시 오류 파일  
 전역 비 표시 오류 파일에 비 표시 오류는 전역 수준 비 표시 오류 또는 대상을 지정 하지 않는 비 표시 오류는 유지 관리 합니다. 예를 들어, 어셈블리 수준 위반에 대해가이 파일에 저장 됩니다. 또한 일부 ASP.NET 비 표시 오류는 프로젝트 수준 설정 양식 뒤에 있는 코드에 사용할 수 없기 때문에이 파일에 저장 됩니다. 전역 비 표시 만들어지고 선택 하는 처음으로 프로젝트에 추가 합니다 **프로젝트 비 표시 오류 파일의** 옵션을는 **메시지 표시 안 함** 오류 목록 창에서 명령을 합니다. 자세한 내용은 [방법: 메뉴 항목을 사용 하 여 경고 표시 안 함](../code-quality/how-to-suppress-warnings-by-using-the-menu-item.md)합니다.  
  
## <a name="see-also"></a>참고 항목  
 <xref:System.Diagnostics.CodeAnalysis>
