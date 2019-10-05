---
title: 도메인 역할의 속성 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
ms.assetid: 5a7bb18c-638e-45e8-9d79-9aa6a9e14b0e
caps.latest.revision: 11
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: b78c409a761a98439cbbbfdf088e052eca745f32
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63444473"
---
# <a name="properties-of-domain-roles"></a>도메인 역할의 속성
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

다음 표의 속성이 도메인 역할 연관 됩니다. 도메인 역할에 대 한 자세한 내용은 [모델, 클래스 및 관계 이해](../modeling/understanding-models-classes-and-relationships.md)합니다. 이러한 속성을 사용 하는 방법에 대 한 자세한 내용은 참조 하세요. [사용자 지정 및 도메인 특정 언어 확장](../modeling/customizing-and-extending-a-domain-specific-language.md)합니다.  
  
|속성|설명|기본|  
|--------------|-----------------|-------------|  
|컬렉션 형식|이 역할에 복합성 0.. * 또는 1.. \*,이 속성을 사용자 지정 링크의 집합을 저장 하는 데 사용 되는 제네릭 형식입니다.|`(none)` - <xref:Microsoft.VisualStudio.Modeling.LinkedElementCollection%601> 는|  
|사용자 지정 특성|여기서 지정 하는 특성이 생성 된 코드 클래스에 특성으로 추가 됩니다.|\<없음 >|  
|속성을 검색할 수는|하는 경우 `True`, 관계의 복합성이 0..1 또는 1.. 1 인 경우 역할 속성에서 사용자가 탐색할 수 있습니다 합니다 **속성** 창입니다. 속성 관계 링크의 다른 끝에 요소 이름을 표시합니다.|`True`|  
|속성 생성기|경우 `True`, 프로그램 코드에서 관계를 트래버스하는 데 사용할 수 있는이 역할에 대 한 역할 속성이 생성 됩니다. 이 false를 설정한 경우 도메인 관계의 정적 메서드를 사용 하 여 비효율적인 방식으로 관계를 이동할 수 있습니다.|`True`|  
|속성 Getter 액세스 한정자|생성된 된 속성의 getter의 액세스 한정자 (`public`, `internal`를 `private`합니다 `protected`, 또는 `protected internal`).|`public`|  
|속성 Setter 액세스 한정자|생성된 된 속성의 setter 액세스 한정자 (`public`, `internal`를 `private`합니다 `protected`, 또는 `protected internal`).|`public`|  
|복합성|반대쪽 역할을 재생할 수 있는 모델 요소의 수 (`0..1`, `1..1`를 `0..*`, 또는 `1..*`). 복합성이 1 인 경우 `0..*` 또는 `1..*`, 그런 다음 생성된 된 속성 컬렉션을 나타냅니다; 그렇지 않으면, 생성된 된 속성 단일 모델 요소를 나타냅니다.|관계 종류에 따라 달라 집니다, 그리고이 관계의 원본 또는 대상 역할입니다.|  
|이름|도메인 역할의 이름입니다. 이 속성에 공백을 포함할 수 없습니다.|이 역할에 대 한 역할 수행자의 도메인 클래스의 이름입니다.|  
|복사를 전파합니다.|`DoNotPropagateCopy` -복사 된 역할 수행자 복사본이 없는이 링크 해야 합니다.<br /><br /> `PropagateCopyToLinkOnly` 링크 복사 됨된-기존 반대 역할 수행자를 가리킵니다.<br /><br /> `PropagateCopyToLinkAndOppositeRolePlayer` -복사한 링크 반대 역할 수행자의 복사본을 가리킵니다.|`PropagateCopyToLinkAndOppositeRolePlayer` 포함의 소스 역할입니다.<br /><br /> `DoNotPropagateCopy` 다른 역할입니다.<br /><br /> 자세한 내용은 참조 하세요. [복사 동작 사용자 지정](../modeling/customizing-copy-behavior.md)|  
|삭제 전파|`True` 연결 된 링크가 삭제 되 면이 역할을 담당 하는 요소를 삭제 합니다.|`True` 포함 역할의 대상입니다.<br /><br /> `False` 다른 역할입니다.<br /><br /> 자세한 내용은 [삭제 동작 사용자 지정](../modeling/customizing-deletion-behavior.md)합니다.|  
|속성 이름|역할 수행자의 코드에서 생성 된 속성의 이름입니다. 이 이름은 공백을 포함할 수 없습니다.|이 역할에는 0-1에 있는 경우 반대쪽 역할의 이름 또는 한 일 다중성입니다. 그렇지 않으면 반대쪽 역할의 이름을 복수화 합니다.|  
|역할 수행자|도메인 클래스 관계에서이 역할을 수행할 수 있는 요소입니다. 이 속성은 읽기 전용입니다.|이 역할에 대 한 역할 수행자의 도메인 클래스입니다.|  
|노트|도메인 역할을 사용 하 여 연결 된 비공식 메모입니다.|\<없음 >|  
|범주|생성된 된 속성에서 표시 되는 범주는 **속성** 생성된 된 디자이너에서 창입니다. 이 속성이 비어 있으면 생성된 된 속성 아래에 표시 됩니다는 **기타** 범주|\<없음 >|  
|설명|코드를 문서화 하는 데 사용 되 고 생성된 된 디자이너의 UI에 사용 되는 설명입니다.<br /><br /> 역할 수행자 클래스에서 생성된 된 속성에 대 한 Intellisense 도구 설명에 표시 됩니다.|`Description for` *역할의 전체 이름*|  
|표시 이름|도메인 역할에 대해 생성된 된 디자이너에 표시 되는 이름입니다.|이름 속성은 조정 된 값입니다.|  
|Help Keyword|도메인 역할에 대 한 F1 도움말을 인덱싱하는 데는 선택적 키워드입니다.|\<없음 >|  
|속성 표시 이름|생성 된 역할 속성에 대해 생성된 된 디자이너에 표시 되는 이름입니다.|속성 이름 속성은 조정 된 값입니다.|  
  
> [!NOTE]
> 표시 이름의 기본값은 각 대문자 문자는 소문자 문자 앞에 및 다른 대문자가 나오지 않습니다 앞에 공백을 삽입 하 여 연결된 된 속성 값을 기반으로 합니다.  
  
## <a name="see-also"></a>참고 항목  
 [도메인 관계의 속성](../modeling/properties-of-domain-relationships.md)
