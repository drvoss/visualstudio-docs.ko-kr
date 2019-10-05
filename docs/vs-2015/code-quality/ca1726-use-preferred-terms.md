---
title: 'CA1726: 기본 설정된 용어를 사용 하 여 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- UsePreferredTerms
- CA1726
helpviewer_keywords:
- UsePreferredTerms
ms.assetid: 642b2acd-3a33-4d1f-b0a7-67073ae73be2
caps.latest.revision: 24
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 67dab4c732faa04af44800f740d78c4ce4f9dc80
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68143156"
---
# <a name="ca1726-use-preferred-terms"></a>CA1726: 기본 설정 용어를 사용하세요.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio에서 최신 설명서를 참조 하세요. [CA1726: 기본 설정된 용어를 사용 하 여](https://docs.microsoft.com/visualstudio/code-quality/ca1726-use-preferred-terms)입니다.  
  
|||  
|-|-|  
|TypeName|UsePreferredTerms|  
|CheckId|CA1726|  
|범주|Microsoft.Naming|  
|변경 수준|주요-어셈블리에서 발생 한 경우<br /><br /> 아님-형식 매개 변수에서 발생 한 경우|  
  
## <a name="cause"></a>원인  
 외부에서 볼 수 있는 식별자의 이름에 특정 용어가 포함되어 있는데, 이 용어에는 기본 설정된 대체 용어가 있습니다. 또는 이름을 플래그 또는 플래그 용어를 포함합니다.  
  
## <a name="rule-description"></a>규칙 설명  
 이 규칙 식별자 토큰 구문 분석합니다. 각 토큰 및 각 연속 이중 토큰 조합 및 사용자 지정 사전의 사용 되지 않는 섹션에서 규칙에 기본 제공 되는 용어와 비교 됩니다. 다음 표에서 규칙 및 해당 기본 대안에 내장 된 용어를 보여 줍니다.  
  
|사용 되지 않는 용어|기본 용어|  
|-------------------|--------------------|  
|`Arent`|`AreNot`|
|`Cancelled`|`Canceled`|
|`Cant`|`Cannot`|
|`ComPlus`|`EnterpriseServices`|
|`Couldnt`|`CouldNot`|
|`Didnt`|`DidNot`|
|`Doesnt`|`DoesNot`|
|`Dont`|`DoNot`|
|`Flag` 또는 `Flags`|대체 용어가 없는 경우 사용하지 마십시오.|
|`Hadnt`|`HadNot`|
|`Hasnt`|`HasNot`|
|`Havent`|`HaveNot`|
|`Indices`|`Indexes`|
|`Isnt`|`IsNot`|
|`LogIn`|`LogOn`|
|`LogOut`|`LogOff`|
|`Shouldnt`|`ShouldNot`|
|`SignOn`|`SignIn`|
|`SignOff`|`SignOut`|
|`Wasnt`|`WasNot`|
|`Werent`|`WereNot`|
|`Wont`|`WillNot`|
|`Wouldnt`|`WouldNot`|
|`Writeable`|`Writable`|
  
## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법  
 이 규칙 위반 문제를 해결 하는 기본 대체 용어를 사용 하 여 용어를 대체 합니다.  
  
## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우  
 식별자의 이름을 의도적인 하는 기본 용어 대신 원래 용어와 특히 관련이 하는 경우에이 규칙에서 경고를 표시 합니다.  
  
## <a name="related-rules"></a>관련된 규칙  
 [이름 지정 경고](../code-quality/naming-warnings.md)
