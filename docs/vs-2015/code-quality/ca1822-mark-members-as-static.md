---
title: 'CA1822: 멤버를 static으로 표시 합니다. | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- MarkMembersAsStatic
- CA1822
helpviewer_keywords:
- MarkMembersAsStatic
- CA1822
ms.assetid: 743f0af7-41d1-4852-8d97-af0688b31118
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 42c6f0d333d1f7ee3f657b9c57c4154e9f824128
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68201674"
---
# <a name="ca1822-mark-members-as-static"></a>CA1822: 멤버를 static으로 표시하세요.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio에서 최신 설명서를 참조 하세요. [CA1822: 멤버를 static으로 표시할](https://docs.microsoft.com/visualstudio/code-quality/ca1822-mark-members-as-static)합니다.  
  
|||  
|-|-|  
|TypeName|MarkMembersAsStatic|  
|CheckId|CA1822|  
|범주|Microsoft.Performance|  
|변경 수준|아님-멤버 어셈블리 외부에서 표시 되지 않으면 변경에 관계 없이 하면 됩니다.<br /><br /> 아님-멤버와 인스턴스 멤버를 변경 하는 경우는 `this` 키워드입니다.<br /><br /> 주요-정적 멤버에 인스턴스 멤버에서 멤버를 변경 하 고 어셈블리 외부에 표시 됩니다.|  
  
## <a name="cause"></a>원인  
 인스턴스 데이터에 액세스 하지 않습니다 하는 멤버를 정적으로 표시 됩니다 (공유 [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]).  
  
## <a name="rule-description"></a>규칙 설명  
 인스턴스 데이터에 액세스하지 않거나 인스턴스 메서드를 호출하지 않는 멤버는 static([!INCLUDE[vbprvb](../includes/vbprvb-md.md)]의 경우 Shared)으로 표시할 수 있습니다. 메서드를 static으로 표시하면 컴파일러는 이러한 멤버에 대한 비가상 호출 사이트를 내보냅니다. 비가상 호출 사이트를 표시 하 고 현재 개체 포인터가 null 인지 하는 각 호출에 대해 런타임에 검사가 수행 되지 것입니다. 이 성능에 민감한 코드에 대 한 성능이 크게 향상을 얻을 수 있습니다. 일부 경우에는 현재 개체 인스턴스에 액세스 하는 데 실패 정확성 문제를 나타냅니다.  
  
## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법  
 정적 멤버 표시 (공유 또는 [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]) 또는 'this '/' Me' 메서드의 본문에 해당 하는 경우.  
  
## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우  
 이전에 제공 된 코드는 수정 프로그램은 주요 변경 내용에 대 한이 규칙에서 경고를 표시 하지 않아도 안전 합니다.  
  
## <a name="related-rules"></a>관련된 규칙  
 [CA1811: 호출 되지 않는 전용 코드를 방지 합니다.](../code-quality/ca1811-avoid-uncalled-private-code.md)  
  
 [CA1812: 인스턴스화되지 않은 내부 클래스를 방지 합니다.](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)  
  
 [CA1804: 사용 되지 않는 로컬 항목을 제거](../code-quality/ca1804-remove-unused-locals.md)
