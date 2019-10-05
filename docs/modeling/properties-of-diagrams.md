---
title: 다이어그램의 속성
ms.date: 10/31/2018
ms.topic: reference
f1_keywords:
- vs.dsltools.dsldesigner.dsldiagram
helpviewer_keywords:
- Domain-Specific Language, diagram
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 05c348edfa4665b138ac0f6069b0afaf6735da7a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62999260"
---
# <a name="properties-of-diagrams"></a>다이어그램의 속성
생성된 된 디자이너에서 다이어그램 모양을 지정 하는 속성을 설정할 수 있습니다. 예를 들어 다이어그램에 텍스트에 대 한 기본 색을 지정할 수 있습니다.

 자세한 내용은 [도메인별 언어 정의 방법](../modeling/how-to-define-a-domain-specific-language.md)합니다. 이러한 속성을 사용 하는 방법에 대 한 자세한 내용은 참조 하세요. [사용자 지정 도메인 특정 언어를 확장 하 고](../modeling/customizing-and-extending-a-domain-specific-language.md)입니다.

 다음 표에서 다이어그램의 속성을 나열 합니다.

|속성|설명|기본|
|-|-|-|
|채우기 색|다이어그램의 채우기 색입니다.|하얀|
|텍스트 색|다이어그램에 표시 되는 텍스트의 색입니다.|검정|
|액세스 한정자|(공용 또는 내부) 클래스의 액세스 한정자입니다.|Public|
|사용자 지정 특성|생성 된 코드 클래스에 특성을 추가 하는 데 사용 합니다.|\<없음 >|
|이중 생성 파생|경우 `True`, 기본 클래스와 지원 사용자 지정 재정의 통해) 하는 것 (하는 partial 클래스를 생성 됩니다. 자세한 내용은 [재정의 생성 된 클래스를 확장 하 고](../modeling/overriding-and-extending-the-generated-classes.md)입니다.|False|
|사용자 지정 생성자|경우 `True`, 소스 코드에서 사용자 지정 생성자를 제공 됩니다. 자세한 내용은 [재정의 생성 된 클래스를 확장 하 고](../modeling/overriding-and-extending-the-generated-classes.md)...|False|
|상속 한정자|다이어그램에서 생성 되는 소스 코드 클래스의 상속의 종류에 설명 합니다 (`none`하십시오 `abstract`, 또는 `sealed`).|없음|
|기본 다이어그램|이 다이어그램의 기본 클래스입니다.|(없음)|
|이름|이 다이어그램의 이름입니다.|현재 이름|
|네임스페이스|이 다이어그램을 사용 하 여 관련 되는 네임 스페이스입니다.|현재 네임 스페이스|
|나타내는 클래스|이 다이어그램을 나타내는 루트 도메인 클래스입니다.|해당 하는 경우 현재 루트 클래스|
|노트|이 요소와 연결 된 비공식 메모입니다.|\<없음 >|
|속성으로 노출 채우기 색|경우 `True`, 사용자는 생성된 된 디자이너의 다이어그램의 채우기 색을 설정할 수 있습니다. 이 속성을 설정 하려면 다이어그램 셰이프를 마우스 오른쪽 단추로 클릭 하 고 클릭 **Add Exposed**합니다.|False|
|속성으로 텍스트 색을 표시합니다.|경우 `True`, 사용자 생성된 된 디자이너에서 다이어그램의 텍스트 색을 설정할 수 있습니다. 이 속성을 설정 하려면 다이어그램 셰이프를 마우스 오른쪽 단추로 클릭 하 고 클릭 **Add Exposed**합니다.|False|
|설명|생성된 된 디자이너를 문서화 하는 데 사용 되는 설명입니다.|\<없음 >|
|표시 이름|이 다이어그램에 대해 생성된 된 디자이너에서 표시 되는 이름입니다.|\<없음 >|
|Help Keyword|이 다이어그램에 대 한 F1 도움말을 인덱싱하는 데는 키워드입니다.|\<없음 >|

## <a name="see-also"></a>참고자료

[도메인 특정 언어 도구 용어집](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
