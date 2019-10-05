---
title: 스윔 레인의 속성 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
f1_keywords:
- vs.dsltools.dsldesigner.swimlane
helpviewer_keywords:
- Domain-Specific Language, swimlane
ms.assetid: 47edbc2d-09e4-48ac-b4d1-5268a06a27e6
caps.latest.revision: 26
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: dd4435ed0930a920cd36e741ac7461e6f95ba815
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65701509"
---
# <a name="properties-of-swimlanes"></a>스윔 레인의 속성
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

다이어그램에 스윔 레인을 추가할 수 있습니다. 스윔 레인은 다이어그램을 세로 또는 가로 영역 나눕니다. 스윔 레인 내에서 표시할 다른 셰이프를 정의할 수 있습니다. 자세한 내용은 [도메인별 언어 정의 방법](../modeling/how-to-define-a-domain-specific-language.md)합니다. 이러한 속성을 사용 하는 방법에 대 한 자세한 내용은 참조 하세요. [사용자 지정 및 도메인 특정 언어 확장](../modeling/customizing-and-extending-a-domain-specific-language.md)합니다.  
  
 스윔 레인 다음 표에 나열 된 속성을 가집니다.  
  
|속성|설명|기본|  
|--------------|-----------------|-------------|  
|본문 채우기 색|스윔 레인의 본문에 대 한 채우기 색입니다.|하얀|  
|헤더 채우기 색|스윔 레인의 헤더에 대 한 채우기 색입니다.|DarkGray|  
|구분 기호 색|구분선의 색입니다.|LightGray|  
|구분 기호 선 스타일|구분선의 스타일 (`Solid`, `Dash`, `Dot`, `DashDot`합니다 `DashDotDot`, 또는 `Custom`).|`Dash`|  
|구분 기호 두께|인치에서 구분선의 두께입니다.|0.03125|  
|텍스트 색|이 스윔 레인에 연관 된 텍스트 데코레이터에 사용 되는 색입니다.|검정|  
|액세스 한정자|클래스의 액세스 수준 (`public` 또는 `internal`).|Public|  
|사용자 지정 특성|이 스윔 레인에서 생성 되는 코드 클래스에 특성을 추가 하는 데 사용 합니다.|\<없음 >|  
|이중 생성 파생|경우 `True`, 기본 클래스와 지원 사용자 지정 재정의 통해) 하는 것 (하는 partial 클래스를 생성 됩니다. 자세한 내용은 [생성 된 클래스 재정의 및 확장](../modeling/overriding-and-extending-the-generated-classes.md)합니다.|False|  
|사용자 지정 생성자|경우 `True`, 소스 코드에서 사용자 지정 생성자를 제공 됩니다. 자세한 내용은 [생성 된 클래스 재정의 및 확장](../modeling/overriding-and-extending-the-generated-classes.md)합니다.|False|  
|상속 한정자|스윔 레인에서 생성 되는 소스 코드 클래스의 상속의 종류에 설명 합니다 (`none`하십시오 `abstract` 또는 `sealed`).|없음|  
|기본 스윔 레인|이 스윔 레인의 기본 클래스입니다.|(없음)|  
|이름|이 스윔 레인의 이름입니다.|현재 이름|  
|네임스페이스|이 스윔 레인을 사용 하 여 관련 되는 네임 스페이스입니다.|현재 네임 스페이스|  
|Tooltip 형식|도구 설명을 정의 하는 방법 (`fixed`하십시오 `variable`, 또는 `none`). 하는 경우 `fixed`의 값을 `Fixed Tooltip Text` 경우; 속성을 사용 `variable`, 도구 설명 사용자 지정 코드에 정의 된 다음입니다.|\<없음 >|  
|노트|이 스윔 레인을 사용 하 여 연결 된 비공식 메모입니다.|\<없음 >|  
|맞춤|가로 또는 세로 맞춤입니다.|세로|  
|초기 높이|인치에서이 스윔 레인의 초기 높이입니다. 가로 스윔 레인에만 적용 됩니다.|0|  
|초기 너비|인치에서이 스윔 레인의 초기 너비입니다. 세로 스윔 레인에만 적용 됩니다.|0|  
|텍스트 색을 표시합니다.|경우 `True`, 사용자 생성된 된 디자이너에서 스윔 레인의 색을 설정할 수 있습니다. 이 설정 하려면 스윔 레인 셰이프를 마우스 오른쪽 단추로 클릭 하 고 클릭 **Add Exposed**합니다.|False|  
|설명|생성된 된 디자이너를 문서화 하는 데 사용 합니다.|\<없음 >|  
|표시 이름|이 스윔 레인 클래스를 가리키도록 생성된 된 디자이너에서 표시 되는 이름입니다.|\<없음 >|  
|고정된 도구 설명 텍스트|고정된 도구 설명에 사용 되는 텍스트입니다.|\<없음 >|  
|Help Keyword|이 스윔 레인에 대 한 F1 도움말을 인덱싱하는 데는 키워드입니다.|\<없음 >|  
  
## <a name="see-also"></a>참고 항목  
 [도메인 특정 언어 도구 용어집](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
