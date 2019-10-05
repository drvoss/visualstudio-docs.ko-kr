---
title: 생성된 클래스 재정의 및 확장
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, providing overridable classes
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9aa4f39fb54617ae1dbf048a1e13f009c8df5185
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62814239"
---
# <a name="override-and-extend-the-generated-classes"></a>재정의 하 고 생성된 된 클래스를 확장 합니다.

DSL 정의 플랫폼은 강력한 도메인 특정 언어를 기반으로 하는 도구 집합을 작성할 수 있습니다. 많은 확장과 adaptation DSL 정의에서 생성 된 클래스 재정의 및 확장 하 여 만들 수 있습니다. 이러한 클래스는 DSL 정의 다이어그램에서 명시적으로 정의한 도메인 클래스 뿐 아니라 뿐만 아니라 도구 상자, 탐색기, serialization 및 등을 정의 하는 다른 클래스를 포함 합니다.

## <a name="extensibility-mechanisms"></a>확장성 메커니즘

몇 가지 메커니즘은 생성 된 코드를 확장할 수 있도록 제공 됩니다.

### <a name="override-methods-in-a-partial-class"></a>Partial 클래스에서 메서드를 재정의

Partial 클래스 정의 둘 이상의 위치에서 정의 하는 클래스를 허용 합니다. 이 옵션을 사용 하면 직접 작성 하는 코드에서 생성된 된 코드를 분리할 수 있습니다. 수동으로 작성 된 코드에서 생성 된 코드의 상속 된 클래스를 재정의할 수 있습니다.

예를 들어 라는 도메인 클래스를 정의 하면 DSL 정의에서 `Book`, 재정의 메서드를 추가 하는 사용자 지정 코드를 작성할 수 있습니다.

```csharp
public partial class Book
{
   protected override void OnDeleting()
   {
      MessageBox.Show("Deleting book " + this.Title);
      base.OnDeleting();
   }
}
```

> [!NOTE]
> 생성된 된 클래스의 메서드를 재정의 하려면 항상 생성된 된 파일에서 분리 된 파일에 코드를 작성 합니다. 일반적으로 파일 CustomCode 라는 폴더에 포함 됩니다. 생성된 된 코드를 변경한 경우 DSL 정의에서 코드를 다시 생성 하면 손실 됩니다.

재정의할 수 있는 메서드를 검색 하려면 입력 **재정의** 클래스에서 뒤에 공백이 있습니다. IntelliSense 도구 설명이 알려줍니다 어떤 메서드를 재정의할 수 있습니다.

### <a name="double-derived-classes"></a>Double에서 파생 된 클래스

생성 된 클래스의 메서드 중 대부분은 고정된 집합이 모델링 네임 스페이스의 클래스에서 상속 됩니다. 그러나 일부 메서드는 생성된 된 코드에서 정의 됩니다. 일반적으로이 의미 하며 재정의할 수 없습니다. 동일한 클래스의 다른 부분 정의에 정의 된 메서드 하나의 partial 클래스에서 재정의할 수 없습니다.

그럼에도 불구 하 고 설정 하 여 이러한 메서드를 재정의할 수 있습니다 합니다 **Generates Double Derived** 도메인 클래스에 대 한 플래그입니다. 이 원인은 두 가지 클래스를 생성할 수, 다른 추상 기본 클래스 중 하나입니다. 모든 메서드 및 속성 정의 기본 클래스를 파생된 클래스에서 생성자만 합니다.

예를 들어, 예제의 Library.dsl, 합니다 `CirculationBook` 도메인 클래스에는 `Generates``Double Derived` 속성이로 설정 `true`. 해당 도메인 클래스에 대해 생성된 된 코드에는 두 개의 클래스가 들어 있습니다.

- `CirculationBookBase`에 추상 이며 모든 속성과 메서드를 포함 하는 합니다.

- `CirculationBook`에서 파생 된 `CirculationBookBase`합니다. 빈 생성자를 제외 하 고는 것입니다.

모든 메서드를 재정의 하는 파생된 클래스의 부분 정의 같은 만들 `CirculationBook`합니다. 생성된 된 메서드와 모델링 프레임 워크에서 상속 된 메서드를 재정의할 수 있습니다.

모든 유형의 모델 요소, 관계, 모양, 다이어그램 및 커넥터를 포함 하 여 요소를 사용 하 여이 메서드를 사용할 수 있습니다. 또한 다른 생성 된 클래스의 메서드를 재정의할 수 있습니다. 일부 같은 ToolboxHelper는 항상 double에서 파생 된 클래스 생성 됩니다.

### <a name="custom-constructors"></a>사용자 지정 생성자

생성자를 재정의할 수 없습니다. Double에서 파생 된 클래스 에서도 파생된 클래스에서 생성자 여야 합니다.

고유한 생성자를 제공 하려는 경우 있습니다 이렇게 설정 하 여 `Has Custom Constructor` DSL 정의에서 도메인 클래스에 대 한 합니다. 클릭 하면 **모든 템플릿 변환**, 생성 된 코드를 해당 클래스의 생성자를 포함 하지 것입니다. 누락 된 생성자를 호출을 포함 됩니다. 이렇게 하면 솔루션을 빌드할 때 오류 보고서. 오류 보고서를 제공 해야 할 내용을 설명 하는 생성된 된 코드에서 주석을 참조를 두 번 클릭 합니다.

Partial 클래스 정의 생성된 된 파일을 별개의 파일을 작성 하 고 생성자를 제공 합니다.

### <a name="flagged-extension-points"></a>플래그가 지정 된 확장 지점

플래그가 지정 된 확장 지점에는 속성 또는 사용자 지정 메서드를 문자로 입력할 것임을 나타내기 위해 확인란을 설정할 수 있는 DSL 정의에서 위치입니다. 사용자 지정 생성자는 한 가지 예입니다. 다른 예로 설정 합니다 `Kind` Calculated 또는 사용자 지정 저장소 설정을 도메인 속성의는 **는 사용자 지정** 연결 작성기의 플래그입니다.

플래그를 설정 하 고 코드를 다시 생성 하는 경우에 각각의 경우에서 빌드 오류가 발생 합니다. 오류를 제공 해야 할 일을 설명 하는 참조를 두 번 클릭 합니다.

### <a name="rules"></a>규칙

트랜잭션 관리자를 사용 하는 지정 된 이벤트를 발생 속성 변경과 같은 트랜잭션의 종료 되기 전에 실행 되는 규칙을 정의할 수 있습니다. 규칙은 저장소의 다른 요소 간에 synchronism 유지 하기 위해 일반적으로 사용 됩니다. 예를 들어 다이어그램에 모델의 현재 상태를 표시는 되도록 규칙이 사용 됩니다.

규칙 클래스 별로에 정의 된, 각 개체에 대 한 규칙을 등록 하는 코드를 할 필요가 없도록 합니다. 자세한 내용은 [규칙이 전파 변경 내용을 내에서 모델](../modeling/rules-propagate-changes-within-the-model.md)합니다.

### <a name="store-events"></a>이벤트를 저장 합니다.

모델링 저장소 등 및 특정 유형의 요소를 속성 값이 변경의 추가 및 삭제를 포함 하 여 저장소에 대 한 변경에 대 한 수신 대기 하는 데 사용할 수 있는 이벤트 메커니즘을 제공 합니다. 이벤트 처리기는 변경 내용이 트랜잭션의 종료 된 이후에 호출 됩니다. 일반적으로 이러한 이벤트는 store 외부의 리소스를 업데이트 하는 데 사용 됩니다.

### <a name="net-events"></a>.NET 이벤트

도형 일부 이벤트를 구독할 수 있습니다. 예를 들어 마우스 클릭에 수신 대기할 수 있습니다. 각 개체에 대 한 이벤트를 구독 하는 코드를 작성 해야 합니다. InitializeInstanceResources() 재정의에서이 코드를 작성할 수 있습니다.

일부 이벤트에 데코레이터를 그리는 데 사용 되는 ShapeFields에 생성 됩니다. 예는 [방법: 모양 또는 데코레이터 클릭 가로채기](../modeling/how-to-intercept-a-click-on-a-shape-or-decorator.md)합니다.

이러한 이벤트 일반적으로 발생 하지 않습니다는 트랜잭션 내에서. 저장소에서 변경 하려는 경우 트랜잭션을 만들어야 합니다.