---
title: 도메인별 언어 사용자 지정 및 확장
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language Tools, creating solutions
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ebbb18e37356c1ef6ccc47f18afe4736a418c0c3
ms.sourcegitcommit: 6a19c5ece38a70731496a38f2ef20676ff18f8a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/09/2019
ms.locfileid: "65476574"
---
# <a name="customize-and-extend-a-domain-specific-language"></a>사용자 지정 및 도메인 특정 언어를 확장 합니다.

Visual Studio 모델링 및 시각화 SDK (VMSDK)는 모델링 도구를 정의할 수 있습니다 여러 수준을 제공 합니다.

1. DSL 정의 다이어그램을 사용 하 여 도메인 특정 언어 (DSL)를 정의 합니다. 신속 하 게 사용 되는 다이어그램 표기법, 읽을 수 있는 XML 양식 및 코드 및 기타 아티팩트를 생성 하는 데 필요한 기본 도구를 사용 하 여 DSL을 만들 수 있습니다. 자세한 내용은 [도메인별 언어 정의 방법](../modeling/how-to-define-a-domain-specific-language.md)합니다.

2. DSL 정의의 고급 기능을 사용 하 여 DSL을 미세 조정 합니다. 예를 들어 사용자가 요소를 만들 때 표시 되는 추가 링크를 만들 수 있습니다. 이러한 기술은 대부분 DSL 정의 구현 된다는 및 일부 프로그램 코드 몇 줄이 필요 합니다.

3. 프로그램 코드를 사용 하 여 모델링 도구를 확장 합니다. VMSDK는 DSL 정의에서 생성된 코드를 사용하여 확장을 쉽게 통합할 수 있도록 설계되었습니다. 자세한 내용은 [도메인 특정 언어에 맞게 코드를 작성](../modeling/writing-code-to-customise-a-domain-specific-language.md)합니다.

> [!NOTE]
> DSL 정의 파일을 업데이트 하는 경우 클릭 잊지 **모든 템플릿 변형** 도구 모음에서 **솔루션 탐색기** 솔루션을 다시 작성 하기 전에 합니다.

## <a name="article-reference"></a>문서 참조

|이 결과를 얻으려면|이 항목을 참조 하세요.|
|-|-|
|도형의 색 및 스타일 속성을 설정 하려면 사용자를 허용 합니다.|셰이프 또는 연결선 클래스를 마우스 오른쪽 **Add Exposed**, 한 항목을 클릭 합니다.|
|다른 모델 요소 클래스의 초기 높이 및 너비, 색, 도구 설명 등의 속성을 공유 다이어그램에서 유사 합니다.|셰이프 또는 연결선 클래스 간의 상속을 사용 합니다. 파생 된 모양 및 파생 된 도메인 클래스 간의 매핑을 부모의 매핑 정보를 상속합니다.<br /><br /> 또는 동일한 모양 클래스를 다른 도메인 클래스를 매핑합니다.|
|모델 요소 클래스는 다양 한 모양 컨텍스트에서 표시 됩니다.|동일한 도메인 클래스에 둘 이상의 모양 클래스를 매핑하십시오. 솔루션을 빌드하면 오류 보고서를 따르고 데 모양을 결정 하는 요청 된 코드를 제공 합니다.|
|셰이프 색상 또는 글꼴 등의 기타 기능에는 현재 상태를 나타냅니다.|참조 [모양 및 연결선은 모델을 반영 하도록 업데이트](../modeling/updating-shapes-and-connectors-to-reflect-the-model.md)합니다.<br /><br /> 노출된 된 속성을 업데이트 하는 규칙을 만듭니다. 참조 [규칙에는 모델 내부의 변경 내용 전파](../modeling/rules-propagate-changes-within-the-model.md)합니다.<br /><br /> 또는 OnAssociatedPropertyChanged()를 사용 하 여 링크 화살표 등 글꼴 비공개 기능을 업데이트 합니다.|
|모양 변경 상태를 나타내는 아이콘입니다.|DSL 정보 창에서 decorator 매핑의 표시 유형을 설정 합니다. 동일한 위치에 여러 이미지 데코레이터를 찾습니다. 참조 [모양 및 연결선은 모델을 반영 하도록 업데이트](../modeling/updating-shapes-and-connectors-to-reflect-the-model.md)합니다.<br /><br /> 재정의 또는 `ImageField.GetDisplayImage()`합니다. 예제를 참조 <xref:Microsoft.VisualStudio.Modeling.Diagrams.ImageField>합니다.|
|모양에 배경 이미지 설정|고정된 이미지 필드를 추가 하려면 InitializeInstanceResources()를 재정의 합니다.|
|임의 깊이까지 모양 중첩|트리를 포함 하는 재귀를 설정 합니다. Boundsrules로 셰이프를 포함 하도록 정의 합니다.|
|커넥터에 있는 고정된 요소의 경계 지점에 연결 합니다.|다이어그램에서 작은 포트를 나타내는 포함 된 터미널 요소를 정의 합니다. Boundsrules로 되어에서 포트를 해결 하려면 사용 합니다. 회로 다이어그램 샘플을 참조 [Visualization and Modeling SDK](http://go.microsoft.com/fwlink/?LinkID=186128)합니다.|
|텍스트 필드에 다른 값에서 파생 된 값을 표시 합니다.|Calculated 또는 사용자 지정 저장소 도메인 속성에 텍스트 decorator를 매핑하십시오. 자세한 내용은 [사용자 지정 저장소 속성 및 계산](../modeling/calculated-and-custom-storage-properties.md)합니다.|
|모델 요소 간에 또는 셰이프 사이의 변경 내용 전파|참조 [도메인별 언어에서 유효성 검사](../modeling/validation-in-a-domain-specific-language.md)합니다.|
|Store 외부의 다른 Visual Studio 확장과 같은 리소스에 대 한 변경 내용을 전파 합니다.|참조 [이벤트 처리기로 모델 외부의 변경 내용을 전파](../modeling/event-handlers-propagate-changes-outside-the-model.md)합니다.|
|속성 창 관련 요소의 속성을 표시합니다.|전달 하는 속성을 설정 합니다. 참조 [속성 창 사용자 지정](../modeling/customizing-the-properties-window.md)합니다.|
|속성 범주|속성 창 범주 이라는 섹션으로 나뉩니다. 설정 된 **범주** 도메인 속성입니다. 범주 이름이 같은 속성은 동일한 섹션에 표시 됩니다. 설정할 수도 있습니다는 **범주** 관계 역할입니다.|
|도메인 속성에 대 한 사용자 액세스 제어|설정할 **Is Browsable** 도메인 속성이 런타임 시 속성 창에서 표시 하지 않으려면 false입니다. 여전히 텍스트 decorator를 매핑할 수 있습니다.<br /><br /> **UI Read Only가** 사용자가 도메인 속성을 변경할 수 없습니다.<br /><br /> 도메인 속성에 대 한 프로그램을 받지 않습니다.|
|이름, 아이콘 및 DSL의 모델 탐색기의 노드 표시 유형을 변경 합니다.|참조 [모델 탐색기 사용자 지정](../modeling/customizing-the-model-explorer.md)합니다.|
|복사, 잘라내기 및 붙여넣기를 사용 하도록 설정|설정 합니다 **Enable Copy Paste** 의 속성을 **편집기** DSL 탐색기에서 노드.|
|요소 복사 될 때마다 참조 링크 및 해당 목표를 복사 합니다. 예를 들어, 항목에 첨부 된 메모를 복사 합니다.|설정 된 **Propagates Copy** 속성 (DSL 정의 다이어그램에서 도메인 관계의 한쪽에 있는 선으로 표시 됨) 소스 역할을 합니다.<br /><br /> 더 복잡 한 효과를 얻기 위해 ProcessOnCopy를 재정의 하는 코드를 작성 합니다.<br /><br /> 참조 [복사 동작 사용자 지정](../modeling/customizing-copy-behavior.md)합니다.|
|삭제 하 고, 부모를 재지정 또는 요소를 삭제 하는 경우에 관련 된 요소를 다시 연결 합니다.|설정 된 **Propagates Delete** 관계 역할의 값입니다. 더 복잡 한 효과 대해 재정의 `ShouldVisitRelationship` 하 고 `ShouldVisitRolePlayer` 에서 메서드를 `MyDslDeleteClosure` 에 정의 된 클래스 **형식을 DomainModel.cs**합니다.|
|복사 및 끌어서 놓기에 모양과 셰이프 레이아웃을 유지 합니다.|추가할 모양 및 연결선 복사한 `ElementGroupPrototype`합니다. 재정의에 가장 편리한 방법은 `ElementOperations.CreateElementGroupPrototype()`<br /><br /> 참조 [복사 동작 사용자 지정](../modeling/customizing-copy-behavior.md)합니다.|
|선택한 위치(예: 현재 커서 위치)에 모양을 붙여넣습니다.|재정의 `ClipboardCommandSet.ProcessOnCopy()` 의 위치별 버전을 사용 하도록 `ElementOperations.Merge().` 참조 [복사 동작 사용자 지정](../modeling/customizing-copy-behavior.md)합니다.|
|붙여넣을 때 추가 링크를 만들려면|Override ClipboardCommandSet.ProcessOnPasteCommand()|
|설정에서에서 끌어서 놓기이 다이어그램에서 다른 Dsl 및 Windows 요소|[방법: 끌어서 놓기 처리기 추가](../modeling/how-to-add-a-drag-and-drop-handler.md)|
|부모를 끌어 된 것 처럼 도형이 나 도구는 포트와 같은 자식 셰이프를 끌어 놓을 수를 허용 합니다.|부모에 끌어 놓은 개체를 전달할 대상 개체 클래스에 대해 요소 병합 지시문을 정의 합니다. 참조 [요소 만들기 및 이동 사용자 지정](../modeling/customizing-element-creation-and-movement.md)합니다.|
|도형 또는 도구가 셰이프를 끌어 놓을 수 있는 추가 링크를 허용 하거나 생성 된 개체입니다. 예를 들어, 메모를 연결할가 항목을 놓을 수 있도록 합니다.|대상 도메인 클래스의 요소 병합 지시문을 정의 하 고 생성에 대 한 링크를 정의 합니다. 복잡 한 경우 사용자 지정 코드를 추가할 수 있습니다. 참조 [요소 만들기 및 이동 사용자 지정](../modeling/customizing-element-creation-and-movement.md)합니다.|
|하나의 도구를 사용 하 여 요소의 그룹을 만듭니다. 예를 들어, 고정된 된 포트 집합을 사용 하 여 구성 요소입니다.|도구 상자 초기화 ToolboxHelper.cs의 메서드를 재정의 합니다. 요소 그룹 프로토타입을 EGP () 요소 및 해당 관계 링크가 포함 된를 만듭니다. 참조 [도구 및 도구 상자 사용자 지정](../modeling/customizing-tools-and-the-toolbox.md)합니다.<br /><br /> 보안 주체 및 포트 셰이프는 EGP 포함 하거나는 EGP 인스턴스화될 때 포트 모양은 위치로 boundsrules로 정의 합니다.|
|연결 도구 하나를 사용 하 여 여러 유형의 관계를 인스턴스화합니다.|도구에서 호출 되는 연결 작성기에 링크 연결 지시문 (LCD)를 추가 합니다. Lcd 두 요소의 형식에서 관계 유형을 결정합니다. 요소의 상태에 따라 달라 집니다.이 위해 사용자 지정 코드를 추가할 수 있습니다. 참조 [도구 및 도구 상자 사용자 지정](../modeling/customizing-tools-and-the-toolbox.md)합니다.|
|스티커 도구-사용자 수를 연속 해 서 많은 모양이 나 연결선을 만들려면 도구 두 번 클릭 합니다.|DSL 탐색기에서 선택 된 `Editor` 노드. 속성 창에서 설정할 **스티커 도구 상자 항목을 사용 하 여**입니다.|
|메뉴 명령 정의|[방법: 표준 메뉴 명령 수정](../modeling/how-to-modify-a-standard-menu-command-in-a-domain-specific-language.md)|
|유효성 검사 규칙을 사용 하 여 모델을 제한 합니다.|참조 [도메인별 언어에서 유효성 검사](../modeling/validation-in-a-domain-specific-language.md)|
|DSL에서 코드, 구성 파일 또는 문서를 생성 합니다.|[도메인별 언어에서 코드 생성](../modeling/generating-code-from-a-domain-specific-language.md)|
|모델을 저장 하는 방법을 사용자 지정 파일에 있습니다.|참조 [파일 저장소 및 XML Serialization을 사용자 지정](../modeling/customizing-file-storage-and-xml-serialization.md)|
|데이터베이스 또는 다른 미디어에 모델을 저장 합니다.|재정의 *YourLanguage*DocData<br /><br /> 참조 [파일 저장소 및 XML Serialization을 사용자 지정](../modeling/customizing-file-storage-and-xml-serialization.md)|
|응용 프로그램의 일부로 작동 되도록 여러 Dsl을 통합 합니다.|참조 [Visual Studio Modelbus를 사용 하 여 모델 통합](../modeling/integrating-models-by-using-visual-studio-modelbus.md)합니다.|
|제 3 자에서 확장할 DSL을 허용 하 고 확장을 제어 합니다.|[MEF를 사용하여 DSL 확장](../modeling/extend-your-dsl-by-using-mef.md)<br /><br /> [DSL 라이브러리를 사용하여 DSL 간에 클래스 공유](../modeling/sharing-classes-between-dsls-by-using-a-dsl-library.md)<br /><br /> [잠금 정책을 정의하여 읽기 전용 세그먼트 만들기](../modeling/defining-a-locking-policy-to-create-read-only-segments.md)|

## <a name="see-also"></a>참고자료

- [도메인별 언어 정의 방법](../modeling/how-to-define-a-domain-specific-language.md)
- [도메인별 언어 사용자 지정 하는 코드 작성](../modeling/writing-code-to-customise-a-domain-specific-language.md)
- [Visual Studio용 모델링 SDK - 도메인별 언어](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
