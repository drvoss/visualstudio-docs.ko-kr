---
title: 도메인 경로 구문 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, domain path
ms.assetid: 945994f9-72b9-42e0-81b2-e5fb3d0e282d
caps.latest.revision: 27
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 2c115e8fff6cddbc1b08c697b72c7bda3a970ed4
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68203447"
---
# <a name="domain-path-syntax"></a>도메인 경로 구문
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

DSL 정의는 XPath 유형 구문을 사용하여 모델에서 특정 요소를 찾습니다.  
  
 일반적으로는 이 구문을 직접 사용할 필요가 없습니다. DSL 정보 또는 속성 창에서 이 구문이 표시되면 아래쪽 화살표를 클릭하고 경로 편집기를 사용할 수 있습니다. 그러나 경로는 편집기를 사용하고 나면 이 폼의 필드에 표시됩니다.  
  
 도메인 경로의 형식은 다음과 같습니다.  
  
 *RelationshipName.PropertyName/!Role*  
  
 ![CommentReferencesSubjects 참조 관계](../modeling/media/dsl-reference.png "dsl_reference")  
  
 구문은 모델 트리를 트래버스합니다. 예를 들어, 도메인 관계 **CommentReferencesSubjects** 위의 그림에는 **주제** 역할입니다. 경로 세그먼트 **/! Subjectt** 경로 통해 액세스 하는 요소에 완료 되는지 지정 합니다 **주제** 역할입니다.  
  
 각 세그먼트는 도메인 관계의 이름으로 시작됩니다. 경로 세그먼트 요소로 순회 인 경우 요소에서 관계로 *Relationship.PropertyName*합니다. 경로 세그먼트 요소로 홉 인 경우 링크에서 요소로 *관계 /! RoleName*합니다.  
  
 경로 구문은 슬래시로 구분됩니다. 각 경로 세그먼트는 요소에서 링크(관계 인스턴스) 또는 링크에서 요소로의 홉입니다. 경로 세그먼트는 쌍으로 나타나는 경우가 많습니다. 이 쌍의 경로 세그먼트 하나는 요소에서 링크로의 홉을 나타내고 다음 세그먼트는 링크에서 반대쪽 요소로의 홉을 나타냅니다. 모든 링크는 관계 자체의 소스나 대상일 수도 있습니다.  
  
 요소에서 링크로의 홉에 사용하는 이름은 역할의 `Property Name` 값입니다. 링크에서 요소로의 홉에 사용하는 이름은 대상 역할 이름입니다.  
  
## <a name="see-also"></a>참고 항목  
 [모델, 클래스 및 관계 이해](../modeling/understanding-models-classes-and-relationships.md)
