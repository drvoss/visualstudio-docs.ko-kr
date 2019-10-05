---
title: DSL 정의의 속성 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
helpviewer_keywords:
- Domain-Specific Language, definition file
ms.assetid: 38debcfe-e1a6-4a3f-9d69-3ab07520f2b6
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 77f0a384797217440600d1ba5db0f190f4bdafa3
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65685358"
---
# <a name="properties-of-a-dsl-definition"></a>DSL 정의의 속성
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

DslDefinition 속성 정의 *도메인별 언어* 버전 번호와 같은 정의 속성입니다. DslDefinition 속성에 표시 합니다 **속성** 창에서 다이어그램의 빈 영역을 클릭할 때 합니다 *도메인별 언어 디자이너*.  
  
 자세한 내용은 [도메인별 언어 정의 방법](../modeling/how-to-define-a-domain-specific-language.md)합니다. 이러한 속성을 사용 하는 방법에 대 한 자세한 내용은 참조 하세요. [사용자 지정 및 도메인 특정 언어 확장](../modeling/customizing-and-extending-a-domain-specific-language.md)합니다.  
  
 DslDefinition 다음 표의 속성이 있습니다.  
  
|속성|설명|기본|  
|--------------|-----------------|-------------|  
|액세스 한정자|도메인 클래스에 대 한 액세스 한정자가 public 또는 internal 인지를 결정 합니다.|public|  
|사용자 지정 특성|사용자 지정 도메인 클래스에 대 한 특성을 정의 합니다.<br /><br /> **참고** 특성을 추가 하려면 찾아보기 단추를 사용 합니다.|\<없음 >|  
|회사 이름|시스템 레지스트리에 현재 회사 이름의 이름입니다.|현재 회사 이름|  
|이름|이 도메인 클래스의 이름입니다.|현재 이름|  
|네임스페이스|이 도메인 클래스를 사용 하 여 연결 된 네임 스페이스입니다.|현재 네임 스페이스|  
|패키지 Guid|에 대 한 guid를 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 이 DSL에 대해 생성 된 패키지입니다.|\<없음 >|  
|패키지 Namespace|에 대 한 네임 스페이스는 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 이 DSL에 대해 생성 된 패키지입니다.|\<없음 >|  
|제품 이름|에 등록할 제품의 이름을 합니다 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 이 DSL에 대해 생성 된 패키지입니다.|\<없음 >|  
|노트|이 도메인 클래스와 관련 된 정보입니다.|\<없음 >|  
|설명|이 도메인 클래스에 대 한 설명입니다.|\<없음 >|  
|표시 이름|이 도메인 클래스에 대해 생성된 된 디자이너에서 표시 되는 이름입니다.|\<없음 >|  
|Help Keyword|이 도메인 클래스와 연결 된 도움말 키워드입니다.|\<없음 >|  
|빌드|이 도메인별 언어 정의 대 한 증분 빌드 번호입니다.|0|  
|주 버전|이 도메인별 언어 정의 증분 주 빌드 번호입니다.|1|  
|부 버전|이 도메인별 언어 정의 대 한 증분 부 빌드 번호입니다.|0|  
|Revision|증분 수정 빌드이 도메인별 언어 정의 대 한 번호입니다.|0|  
  
## <a name="see-also"></a>참고 항목  
 [도메인 특정 언어 도구 용어집](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
