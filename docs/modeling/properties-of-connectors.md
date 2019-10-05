---
title: 연결선의 속성
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Domain-Specific Language, connectors
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 754f479b99eef44159994425ddd7a0d812bcf2ee
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62970811"
---
# <a name="properties-of-connectors"></a>연결선의 속성
연결선은 생성된 된 디자이너의 도메인 관계를 나타냅니다.

 자세한 내용은 [도메인별 언어 정의 방법](../modeling/how-to-define-a-domain-specific-language.md)합니다. 이러한 속성을 사용 하는 방법에 대 한 자세한 내용은 참조 하세요. [사용자 지정 및 도메인 특정 언어 확장](../modeling/customizing-and-extending-a-domain-specific-language.md)합니다.

 커넥터는 다음 표에 나열 된 속성을 가집니다.

|속성|설명|기본|
|-|-|-|
|색|이 연결선의 색입니다.|검정|
|대시 스타일|(단색, 대시, 점, DashDot, 이점 쇄선, 또는 사용자 지정)이이 커넥터에 대 한 줄에 대 한 대시 스타일입니다.|단색|
|소스 끝 스타일|(HollowArrow, EmptyArrow, FilledArrow, EmptyDiamond, FilledDiamond, 또는 없음)이이 커넥터에 대 한 소스 끝 스타일입니다.|없음|
|대상 끝 스타일입니다.|(HollowArrow, EmptyArrow, FilledArrow, EmptyDiamond, FilledDiamond, 또는 없음)이이 커넥터에 대 한 대상 끝 스타일입니다.|없음|
|텍스트 색|이 커넥터를 사용 하 여 연결 된 텍스트 데코레이터에 사용 되는 색입니다.|검정|
|Thickness|이 연결선의 선 두께 인치 단위로 지정 합니다.|0.03125|
|액세스 한정자|클래스의 액세스 수준 (`public` 또는 `internal`).|Public|
|사용자 지정 특성|이 커넥터에서 생성 되는 소스 코드 클래스에 특성을 추가 하는 데 사용 합니다.|\<없음 >|
|이중 생성 파생|경우 `True`, 기본 클래스와 지원 사용자 지정 재정의 통해) 하는 것 (하는 partial 클래스를 생성 됩니다. 자세한 내용은 [생성 된 클래스 재정의 및 확장](../modeling/overriding-and-extending-the-generated-classes.md)합니다.|False|
|사용자 지정 생성자|경우 `True`, 소스 코드에서 사용자 지정 생성자를 제공 됩니다. 자세한 내용은 [생성 된 클래스 재정의 및 확장](../modeling/overriding-and-extending-the-generated-classes.md)합니다.|False|
|상속 한정자|커넥터에서 생성 되는 소스 코드 클래스의 상속의 종류에 설명 합니다 (`none`하십시오 `abstract` 또는 `sealed`).|없음|
|기본 연결선|이 연결선의 기본 클래스입니다.|(없음)|
|이름|이 연결선의 이름입니다.|현재 이름|
|네임스페이스|이 커넥터를 사용 하 여 관련 되는 네임 스페이스입니다.|현재 네임 스페이스|
|Tooltip 형식|도구 설명 (고정, 변수 또는 없음) 정의 되는 방식입니다. 다음 값을 고정 하는 경우는 `Fixed Tooltip Text` 변수인 경우 다음 도구 설명 코드에 정의 된 사용자 지정; 속성은 도구 설명으로 사용 됩니다.|\<없음 >|
|노트|이 커넥터를 사용 하 여 연결 된 비공식 메모입니다.|\<없음 >|
|라우팅 스타일|커넥터를 라우팅에 사용 되는 스타일입니다. A `Rectilinear` 커넥터를 사용 하면; 필요에 따라 직각 회전을 `Straight` 커넥터 하지 않습니다.|직각선|
|속성으로 노출 된 색<br /><br /> 속성으로 노출 된 대시 스타일<br /><br /> 속성으로 노출 된 두께<br /><br /> 텍스트 색을 표시합니다.|경우 `True`, 사용자는 도형의 명시 된 속성을 설정할 수 있습니다. 이 설정 하려면 셰이프 정의 마우스 오른쪽 단추로 클릭 하 고 클릭 **Add Exposed**합니다.|False|
|설명|생성된 된 디자이너를 문서화 하는 데 사용 합니다.|\<없음 >|
|표시 이름|이 커넥터에 대 한 생성된 된 디자이너에서 표시 되는 이름입니다.|\<없음 >|
|고정된 도구 설명 텍스트|고정된 도구 설명에 사용 되는 텍스트입니다.|\<없음 >|
|Help Keyword|이 요소에 대 한 F1 도움말을 인덱싱하는 데는 키워드입니다.|\<없음 >|

## <a name="see-also"></a>참고 항목

- [도메인 특정 언어 도구 용어집](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)