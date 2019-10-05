---
title: 도메인 관계의 속성 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
helpviewer_keywords:
- Domain-Specific Language, domain relationships
ms.assetid: 9ccb3dc2-b80c-4585-932f-3c5f87bafbcd
caps.latest.revision: 22
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 6e30843b0a60ed4183491c16ff9992df8773fd1a
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65701883"
---
# <a name="properties-of-domain-relationships"></a>도메인 관계의 속성
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

다음 표에 속성은 도메인 관계와 연결 합니다. 도메인 관계에 대 한 자세한 내용은 [모델, 클래스 및 관계 이해](../modeling/understanding-models-classes-and-relationships.md)합니다. 이러한 속성을 사용 하는 방법에 대 한 자세한 내용은 참조 하세요. [사용자 지정 및 도메인 특정 언어 확장](../modeling/customizing-and-extending-a-domain-specific-language.md)합니다.  
  
|속성|설명|기본|  
|--------------|-----------------|-------------|  
|액세스 한정자|도메인 관계의 액세스 수준 (`public` 또는 `internal`).|`public`|  
|사용자 지정 특성|도메인 관계에서 생성 되는 소스 코드 클래스에 특성을 추가 하는 데 사용 합니다.|\<없음 >|  
|이중 생성 파생|경우 `True`, 기본 클래스와 부분 클래스 (사용자 지정 재정의 통해 지원)이 생성 됩니다. 자세한 내용은 [생성 된 클래스 재정의 및 확장](../modeling/overriding-and-extending-the-generated-classes.md)합니다.|`False`|  
|사용자 지정 생성자|경우 `True`, 소스 코드에서 사용자 지정 생성자를 제공 됨을 나타냅니다. 자세한 내용은 [생성 된 클래스 재정의 및 확장](../modeling/overriding-and-extending-the-generated-classes.md)합니다.|`False`|  
|상속 한정자|도메인 관계에서 생성 되는 소스 코드 클래스의 상속의 종류에 설명 합니다 (`none`하십시오 `abstract` 또는 `sealed`).|\<없음 >|  
|중복 허용|경우 `True`, 동일한 두 요소 간에 도메인 관계의 중복 링크를 만들 수 있습니다.|`False`|  
|기본 관계|도메인 관계 파생 되는 경우 도메인 관계의 기본 관계입니다.|\<없음 >|  
|포함은|경우 `True`, 도메인 관계는 관계를 포함 합니다. 경우 `False`, 참조 관계입니다.|\<both>|  
|이름|도메인 관계의 이름입니다.|현재 이름|  
|네임스페이스|도메인 관계와 연결 되어 있는 네임 스페이스입니다.|현재 네임 스페이스|  
|노트|도메인 관계와 연결 된 비공식 메모입니다.|\<없음 >|  
|설명|코드를 문서화 하는 데 사용 되 고 생성된 된 디자이너의 UI에 사용 되는 설명입니다.|\<없음 >|  
|표시 이름|도메인 관계에 대해 생성된 된 디자이너에 표시 되는 이름입니다.|\<없음 >|  
|Help Keyword|도메인 관계에 대 한 F1 도움말을 인덱싱하는 데는 선택적 키워드입니다.|\<없음 >|  
  
## <a name="see-also"></a>참고 항목  
 [도메인 특정 언어 도구 용어집](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
