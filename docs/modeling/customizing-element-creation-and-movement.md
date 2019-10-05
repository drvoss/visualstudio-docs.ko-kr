---
title: 요소 만들기 및 이동 사용자 지정
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.dsltools.dsldesigner.elementmergedirective
helpviewer_keywords:
- Domain-Specific Language, element merge directives
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 00026cd53a67a216e126bcc5de92a136a6359331
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62994882"
---
# <a name="customizing-element-creation-and-movement"></a>요소 만들기 및 이동 사용자 지정

요소를 끌 수 다른 도구에서 또는 붙여넣기 또는 이동 작업을 허용할 수 있습니다. 지정 된 관계를 사용 하 여 대상 요소에 연결 하는 이동된 된 요소를 사용할 수 있습니다.

요소 병합 지시문 (EMD) 이상의 모델 요소 경우 어떻게 할지 지정 *병합* 다른 모델 요소에 있습니다. 이런 경우:

- 사용자는 다이어그램 또는 셰이프를 도구 상자에서 끌어 놓습니다.

- 사용자는 탐색기 또는 구획 모양을 추가 메뉴를 사용 하 여 요소를 만듭니다.

- 스윔 레인 항목 간에 이동 하는 사용자.

- 사용자는 요소를 붙여 넣습니다.

- 프로그램 코드 요소 병합 지시문을 호출합니다.

만들기 작업의 복사 작업을 다르게 보이지만 실제로 동일한 방식으로 작동 합니다. 요소에 추가 되 면 예를 들어 도구 상자에서 프로토타입을 복제 됩니다. 프로토타입 모델의 다른 부분에서 복사 된 요소와 동일한 방식으로 모델에 병합 됩니다.

Emd는 추가의 책임 개체 또는 개체 그룹만 병합할 방법을 모델의 특정 위치를 결정 하는 것입니다. 특히 모델에 병합 된 그룹을 연결 하려면 어떤 관계를 인스턴스화해야를 결정 합니다. 또한 속성을 설정 하 고 추가 개체를 만들 수를 지정할 수 있습니다.

![DSL&#45;EMD&#95;Merge](../modeling/media/dsl-emd_merge.png)

Emd는 추가 포함 관계를 정의할 때 자동으로 생성 됩니다. 사용자가 새 자식 인스턴스 부모를 추가 하는 경우이 기본 EMD 관계의 인스턴스를 만듭니다. 사용자 지정 코드를 추가 하 여 예를 들어 이러한 기본 EMDs를 수정할 수 있습니다.

또한 사용자가 끌거나 병합 되 고 받는 클래스의 다양 한 조합을 붙여 넣을 수 있도록 DSL 정의에서 고유한 EMDs를 추가할 수 있습니다.

## <a name="defining-an-element-merge-directive"></a>요소 병합 지시문을 정의합니다.

도메인 클래스, 도메인 관계, 모양, 연결선 및 다이어그램에 요소 병합 지시문을 추가할 수 있습니다. 추가 하거나 수신 하는 도메인 클래스에서 DSL 탐색기에서 찾을 수 있습니다. 받는 클래스는 모델에는 복사 또는 새 요소를 병합할에 이미 있는 요소의 도메인 클래스입니다.

![DSL&#45;EMD&#95;세부 정보](../modeling/media/dsl-emd_details.png)

합니다 **인덱싱 클래스** 받는 클래스의 멤버에 병합할 수 있는 요소의 도메인 클래스입니다. 설정 하지 않은 경우 인덱싱 클래스의 서브 클래스의 인스턴스에서이 EMD에서 병합 될 수도 **서브 클래스에 적용** False로 합니다.

병합 지시문의 두 종류가 있습니다.

- A **프로세스 병합** 지시문은 트리에 새 요소를 연결 관계를 지정 합니다.

- A **앞으로 병합** 지시문 다른 받는 요소를 일반적으로 부모에 새 요소를 리디렉션합니다.

병합 지시문에 사용자 지정 코드를 추가할 수 있습니다.

- 설정할 **사용 하 여 사용자 지정 허용** 인덱싱 요소의 특정 인스턴스를 대상 요소에 병합 해야 하는지 여부를 확인 하려면 사용자 고유의 코드를 추가 합니다. 사용자가 도구 상자에서 "잘못 된" 포인터 코드 병합 허용 하지 않는 경우 표시 됩니다.

   예를 들어 받는 요소를 특정 상태에 있을 때만 병합을 허용할 수 있습니다.

- 설정할 **사용 하 여 사용자 지정 병합** 추가할 자체 코드는 변경 내용을 병합을 수행할 때 모델에 대 한 정의를 제공 합니다.

   예를 들어 모델에서 새 위치에서 데이터를 사용 하 여 병합 된 요소에 속성을 설정할 수 있습니다.

> [!NOTE]
> 사용자 지정 병합 코드를 작성 하는 경우이 EMD를 사용 하 여 수행 되는 유일한 병합을 영향을 줍니다. 동일한 유형의 개체를 병합 하는 다른 EMDs 있거나 기타 사용자 지정 코드를 EMD 사용 하지 않고 이러한 개체를 만드는 경우 다음은 받지 병합 사용자 지정 코드에서.
>
> 사용자 지정 코드에서 새 요소 또는 새 관계를 항상 처리 되지 않는 있는지 확인 하려는 경우 고려해를 `AddRule` 포함 관계에 대해 및 `DeleteRule` 요소의 도메인 클래스에 있습니다. 자세한 내용은 [규칙이 전파 변경 내용을 내에서 모델](../modeling/rules-propagate-changes-within-the-model.md)합니다.

## <a name="example-defining-an-emd-without-custom-code"></a>예제: 사용자 지정 코드 없이 emd는 추가 정의

다음 예제에서는 기존 셰이프를 도구 상자에서 끌어서 동시에 요소 및 커넥터를 만들 수 있도록 합니다. 예제는 DSL 정의에 emd는 추가 추가합니다. 이 수정 하기 전에 사용자가 기존 셰이프에 있지만 다이어그램으로 도구를 끌 수 있습니다.

사용자가 다른 요소에는 요소를 붙여 넣을 수도 있습니다.

### <a name="to-let-users-create-an-element-and-a-connector-at-the-same-time"></a>사용자가 동시에 요소 및 커넥터를 만들 수 있도록 하려면

1. 사용 하 여 새 DSL을 만들 수는 **최소 언어** 솔루션 템플릿.

    이 DSL을 실행 하는 경우 셰이프 및 셰이프 사이 연결선을 만들 수 있습니다. 새 끌면 **ExampleElement** 기존 셰이프를 도구 상자에서 셰이프.

2. 사용자가 요소를 병합할 수 있습니다 `ExampleElement` 도형을 만들기에서 새 EMD는 `ExampleElement` 도메인 클래스:

   1. **DSL 탐색기**를 확장 하 고 **도메인 클래스**합니다. 마우스 오른쪽 단추로 클릭 `ExampleElement` 을 클릭 한 다음 **새 요소 병합 지시문 추가**합니다.

   2. 있는지 확인 합니다 **DSL 정보** 창이 열려 새 EMD의 세부 정보를 볼 수 있도록 합니다. (메뉴: **볼**, **다른 Windows**합니다 **DSL 정보**.)

3. 설정 된 **인덱싱 클래스** DSL 세부 정보 창에 어떤 종류의 요소를 병합할 수 있게 정의 `ExampleElement` 개체입니다.

    예를 들어 선택 `ExampleElements`사용자 기존 요소에 새 요소를 끌 수 있도록 합니다.

    인덱싱 클래스는 DSL 탐색기에서 EMD의 이름이 됩니다 있는지 확인 합니다.

4. 아래 **링크를 만들어 병합 처리**, 두 개의 경로 추가 합니다.

   - 하나의 경로 부모 모델에 새 요소를 연결합니다. 입력 해야 하는 경로 식에서에서 이동는 기존 요소를 포함 관계를 통해 부모 모델 합니다. 마지막으로, 새 링크는 새 요소를 할당할 수의 역할을 지정 합니다. 경로 다음과 같습니다.

      `ExampleModelHasElements.ExampleModel/!ExampleModel/.Elements`

   - 다른 경로 기존 요소를 새 요소를 연결합니다. 경로 식은 참조 관계 및 새 요소를 할당할 역할을 지정 합니다. 이 경로 다음과 같습니다.

      `ExampleElementReferencesTargets.Sources`

      각 경로 만들려면 경로 탐색 도구를 사용할 수 있습니다.

      1. 아래 **경로에 대 한 링크를 만들어 병합 처리**, 클릭  **\<경로 추가 >** 합니다.

      2. 목록 항목의 오른쪽에 드롭다운 화살표를 클릭 합니다. 트리 뷰가 나타납니다.

      3. 지정 하려는 경로 구성 하려면 트리 노드를에서 확장 합니다.

5. DSL을 테스트 합니다.

   1. 키를 눌러 **F5** 를 다시 빌드하고 솔루션을 실행 합니다.

        새 DSL 정의에 맞게 텍스트 템플릿에서 생성된 된 코드를 업데이트할 수는 없으므로 다시 작성 평소 보다 오래 걸릴 됩니다.

   2. Visual Studio의 실험적 인스턴스가 시작 하는 경우에 DSL의 모델 파일을 엽니다. 일부 예제에서는 요소를 만듭니다.

   3. 끌어 합니다 **예제에서는 요소** 기존 모양 도구입니다.

        새 셰이프 나타나고 커넥터를 사용 하 여 기존 셰이프에 연결 됩니다.

   4. 기존 셰이프를 복사 합니다. 다른 셰이프를 선택 하 고 붙여 넣습니다.

        첫 번째 셰이프의 복사본이 만들어집니다.  새 이름을 고 커넥터를 사용 하 여 두 번째 shape에 연결 됩니다.

이 프로시저에서 다음 사항을 확인 합니다.

- 요소 병합 지시문을 만들어 적용할 다른 요소의 모든 클래스를 허용할 수 있습니다. 수신 도메인 클래스에는 EMD 만들어지고 허용된 도메인 클래스에 지정 된 된 **인덱스 클래스** 필드입니다.

- 경로 정의 하 여 지정할 수 있습니다 링크는 기존 모델에 새 요소를 연결 하는 데 사용 됩니다.

     지정 된 링크는 포함 관계 하나 포함 해야 합니다.

- EMD는 모두 만들기를를 선택 하 고 또한 붙여넣기 작업에 영향을 줍니다.

     EMD는를 사용 하 여 명시적으로 호출할 수 있습니다 새 요소를 만든 사용자 지정 코드를 작성 하는 경우는 `ElementOperations.Merge` 메서드. 코드의에서 링크는 새 요소 모델에 다른 작업으로 동일한 방식으로 이렇게 됩니다. 자세한 내용은 [복사 동작 사용자 지정](../modeling/customizing-copy-behavior.md)합니다.

## <a name="example-adding-custom-accept-code-to-an-emd"></a>예제: Emd는 추가를 허용 하는 사용자 지정 코드 추가

사용자 지정 코드에 emd는 추가를 추가 하면 더 복잡 한 병합 동작을 정의할 수 있습니다. 이 간단한 예제에서는 고정 된 수의 요소를 둘 이상의 다이어그램에 추가 사용자를 방지 합니다. 이 예제에서는 EMD 포함 관계와 함께 제공 되는 기본값을 수정 합니다.

### <a name="to-write-custom-accept-code-to-restrict-what-the-user-can-add"></a>사용자에 추가할 수를 제한 하도록 Custom Accept 코드를 작성

1. 사용 하 여 DSL을 만들 수는 **최소 언어** 솔루션 템플릿. DSL 정의 다이어그램을 엽니다.

2. DSL 탐색기에서 확장 **도메인 클래스**하십시오 `ExampleModel`, **요소 병합 지시문**합니다. 선택 이라고 하는 요소 병합 지시문은 `ExampleElement`합니다.

     이 EMD 사용자 새로 만들 수 있습니다 하는 방법을 제어 `ExampleElement` 예를 들어 끌어서 도구 상자에서 모델의 개체입니다.

3. 에 **DSL 세부 정보** 창에서 **사용 하 여 사용자 지정 허용**합니다.

4. 솔루션을 다시 빌드합니다. 모델에서 생성된 된 코드를 업데이트할 수는 없으므로 평소 보다 오래 걸립니다.

     빌드 오류를 보고와 유사 하 게 됩니다. "Company.ElementMergeSample.ExampleElement 없습니다 정의 CanMergeExampleElement..."

     메서드를 구현 해야 `CanMergeExampleElement`합니다.

5. 새 코드 파일을 만듭니다는 **Dsl** 프로젝트입니다. 해당 콘텐츠를 다음 코드로 바꿉니다 하 고 프로젝트의 네임 스페이스에 네임 스페이스를 변경 합니다.

    ```csharp
    using Microsoft.VisualStudio.Modeling;

    namespace Company.ElementMergeSample // EDIT.
    {
      partial class ExampleModel
      {
        /// <summary>
        /// Called whenever an ExampleElement is to be merged into this ExampleModel.
        /// This happens when the user pastes an ExampleElement
        /// or drags from the toolbox.
        /// Determines whether the merge is allowed.
        /// </summary>
        /// <param name="rootElement">The root element in the merging EGP.</param>
        /// <param name="elementGroupPrototype">The EGP that the user wants to merge.</param>
        /// <returns>True if the merge is allowed</returns>
        private bool CanMergeExampleElement(ProtoElementBase rootElement, ElementGroupPrototype elementGroupPrototype)
        {
          // Allow no more than 4 elements to be added:
          return this.Elements.Count < 4;
        }
      }
    }
    ```

    이 간단한 예제에서는 부모 모델에 병합할 수 있는 요소의 수를 제한 합니다. 메서드는 더 흥미로운 조건에 대 한 속성 및 수신 개체의 링크를 검사할 수 있습니다. 제공 되는 병합 요소의 속성을 검사할 수도 있습니다는 <xref:Microsoft.VisualStudio.Modeling.ElementGroupPrototype>합니다. 에 대 한 자세한 내용은 `ElementGroupPrototypes`를 참조 하세요 [복사 동작 사용자 지정](../modeling/customizing-copy-behavior.md)합니다. 모델을 읽는 코드를 작성 하는 방법에 대 한 자세한 내용은 참조 하세요. [탐색 및 업데이트 프로그램 코드에서 모델](../modeling/navigating-and-updating-a-model-in-program-code.md)합니다.

6. DSL을 테스트 합니다.

    1. 키를 눌러 **F5** 솔루션을 다시 빌드해야 합니다. Visual Studio의 실험적 인스턴스가 열리면 DSL의 인스턴스를 엽니다.

    2. 여러 가지 방법으로 새 요소를 만듭니다.

        - 끌어 합니다 **예제에서는 요소** 다이어그램 도구입니다.

        - 에 **예제 모델 탐색기**에서 루트 노드를 마우스 오른쪽 단추로 클릭 하 고 클릭 **새 예제 요소 추가**합니다.

        - 복사 된 다이어그램에서 요소를 붙여넣습니다.

    3. 모델에 4 개 요소를 추가 하려면 다음이 방법 중 하나로 사용할 수 없다는 것을 확인 합니다. 요소 병합 지시문을 사용 하 여 모두 때문입니다.

## <a name="example-adding-custom-merge-code-to-an-emd"></a>예제: Emd는 추가에 병합 하는 사용자 지정 코드 추가

사용자 지정 병합 코드에서 사용자 도구를 끌 요소에 붙여넣을 때 수행할 작업을 정의할 수 있습니다. 두 가지 방법으로 사용자 지정 병합을 정의할 수 있습니다.

1. 설정할 **사용자 지정 병합 사용** 필요한 코드를 제공 합니다. 코드를 생성 된 병합 코드를 바꿉니다. 완전히 병합이 수행 하는 작업을 재정의 하려는 경우이 옵션을 사용 합니다.

2. 재정의 `MergeRelate` 메서드를 선택적으로 `MergeDisconnect` 메서드. 이 작업을 수행 하려면 설정 해야 합니다 **Generates Double Derived** 도메인 클래스의 속성입니다. 코드는 기본 클래스에서 생성 된 병합 코드를 호출할 수 있습니다. 병합을 수행한 후 추가 작업을 수행 하려는 경우이 옵션을 사용 합니다.

   이러한 접근 방식은이 EMD를 사용 하 여 수행 되는 병합을만 영향을 줍니다. 대안은 정의 하는 병합 된 요소를 만들 수 있습니다 하는 모든 방법에 영향을 하려는 경우는 `AddRule` 포함 관계에 대해 및 `DeleteRule` 병합 된 도메인 클래스의 합니다. 자세한 내용은 [규칙이 전파 변경 내용을 내에서 모델](../modeling/rules-propagate-changes-within-the-model.md)합니다.

### <a name="to-override-mergerelate"></a>MergeRelate 재정의 하려면

1. DSL 정의에서는 코드를 추가 하려면 원하는 EMD 정의 했다고 확인 합니다. 경로 추가 하 고 정의할 수 있습니다, 원하는 경우 이전 섹션에 설명 된 대로 사용자 지정 코드를 허용 합니다.

2. DslDefinition 다이어그램에서 병합의 받는 클래스를 선택 합니다. 일반적으로 포함 관계의 소스 end에 있는 클래스입니다.

     예를 들어 최소 언어 솔루션에서 생성 된 DSL에서 선택 `ExampleModel`합니다.

3. 에 **속성** 창에서 **Generates Double Derived** 하 **true**합니다.

4. 솔루션을 다시 빌드합니다.

5. 콘텐츠를 검사할 **Dsl\Generated Files\DomainClasses.cs**합니다. 명명 된 메서드에 대 한 검색 `MergeRelate` 하 고 해당 내용을 검사 합니다. 이 고유한 버전을 작성 하는 데 도움이 됩니다.

6. 새 코드 파일을 받는 클래스에 대 한 partial 클래스를 작성 한 재정의 `MergeRelate` 메서드. 기본 메서드를 호출 해야 합니다. 예를 들어:

    ```csharp
    partial class ExampleModel
    {
      /// <summary>
      /// Called when the user drags or pastes an ExampleElement onto the diagram.
      /// Sets the time of day as the name.
      /// </summary>
      /// <param name="sourceElement">Element to be added</param>
      /// <param name="elementGroup">Elements to be merged</param>
      protected override void MergeRelate(ModelElement sourceElement, ElementGroup elementGroup)
      {
        // Connect the element according to the EMD:
        base.MergeRelate(sourceElement, elementGroup);

        // Custom actions:
        ExampleElement mergingElement = sourceElement as ExampleElement;
        if (mergingElement != null)
        {
          mergingElement.Name = DateTime.Now.ToLongTimeString();
        }
      }
    }
    ```

### <a name="to-write-custom-merge-code"></a>병합 하는 사용자 지정 코드를 작성

1. **Dsl\Generated Code\DomainClasses.cs**, 라는 메서드를 검사 `MergeRelate`합니다. 이러한 메서드는 새 요소를 기존 모델 사이 링크를 만듭니다.

    또한 라는 메서드를 검사 `MergeDisconnect`합니다. 이러한 메서드를 삭제할 때 모델에서 요소를 연결 해제 합니다.

2. **DSL 탐색기**선택 하거나 사용자 지정 하려는 요소 병합 지시문을 만듭니다. 에 **DSL 세부 정보** 창에서 **사용자 지정 병합 사용**합니다.

    이 옵션을 설정 하는 경우는 **프로세스 병합** 하 고 **앞으로 병합** 옵션은 무시 됩니다. 코드 대신 사용 됩니다.

3. 솔루션을 다시 빌드합니다. 모델에서 생성된 된 코드 파일을 업데이트할 수는 없으므로 평소 보다 오래 걸립니다.

    오류 메시지가 나타납니다. 생성된 된 코드에 대 한 지침을 보려면 오류 메시지를 두 번 클릭 합니다. 이러한 지침 두 메서드를 제공 하도록 요청할 `MergeRelate` *YourDomainClass* 하 고 `MergeDisconnect` *YourDomainClass*

4. 별도 코드 파일의 partial 클래스 정의에서 메서드를 작성 합니다. 예제에서는 이전에 검사 해야 필요한 것이 좋습니다.

   사용자 지정 병합 코드 개체 및 관계를 직접 만드는 코드는 영향을 주지 않습니다 하 고 다른 EMDs 영향을 주지 않습니다. 요소는 생성 하는 방법에 관계 없이 추가 변경 내용을 구현 되었는지 확인, 쓰기는 것이 좋습니다는 `AddRule` 및 `DeleteRule` 대신 합니다. 자세한 내용은 [규칙이 전파 변경 내용을 내에서 모델](../modeling/rules-propagate-changes-within-the-model.md)합니다.

## <a name="redirecting-a-merge-operation"></a>병합 작업을 리디렉션

전달 병합 지시문에는 병합 작업의 대상을 리디렉션합니다. 일반적으로 새 대상이 포함 부모 최초 목표입니다.

예를 들어 구성 요소 다이어그램 템플릿을 사용 하 여 생성 된 DSL에서 포트 구성 요소에 포함 됩니다. 포트 구성 요소 셰이프 가장자리에 있는 작은 모양으로 표시 됩니다. 사용자 구성 요소 셰이프를 포트 도구를 끌어 포트를 만듭니다. 하지만 경우에 따라 사용자 실수로 끌어 포트 도구 구성 요소에는 대신 기존 포트를 하 고 작업이 실패 합니다. 기존 포트를 여러 가지 경우는 쉬운 실수입니다. 이 것을 방지 하려면 사용자를 위해 기존 포트를 끌어 놓을 수 있으 나 부모 구성 요소에 리디렉션 작업에 대 한 포트를 허용할 수 있습니다. 작업 대상 요소는 구성 요소 처럼 작동 합니다.

구성 요소 모델 솔루션에는 앞으로 병합 지시문을 만들 수 있습니다. 를 컴파일하고 원래 솔루션을 실행 하는 경우 사용자가 임의 개수의 끌 수 표시 됩니다 **Input Port** 또는 **출력 포트** 요소를 **도구 상자** 하는 **구성 요소** 요소입니다. 그러나 기존 포트에 포트를 끌 수 없습니다. 사용할 수 없는 포인터이 이동이 설정 되어 있지 않은지 경고 하 합니다. 포트는 의도 하지 않게 되도록 정방향 병합 지시문을 만들 수 있지만 기존 삭제 **입력 포트** 에 전달 되는 **구성 요소** 요소.

### <a name="to-create-a-forward-merge-directive"></a>전달 병합 지시문을 만들려면

1. 만들기는 [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] 구성 요소 모델 템플릿을 사용 하 여 솔루션입니다.

2. 표시 된 **DSL 탐색기** DslDefinition.dsl을 열어서 합니다.

3. 에 **DSL 탐색기**를 확장 하 고 **도메인 클래스**합니다.

4. 합니다 **ComponentPort** 추상 도메인 클래스는 둘 다의 기본 클래스 **InPort** 하 고 **OutPort**합니다. 마우스 오른쪽 단추로 클릭 **ComponentPort** 을 클릭 한 다음 **새 요소 병합 지시문 추가**합니다.

    새 **의 요소 병합 지시문** 노드 아래에 나타납니다 합니다 **요소 병합 지시문** 노드.

5. 선택 합니다 **의 요소 병합 지시문** 노드를 열고 다음을 **DSL 세부 정보** 창.

6. 인덱싱 클래스 목록에서 선택 **ComponentPort**합니다.

7. 선택 **다른 도메인 클래스에 병합 전달**합니다.

8. 경로 선택 목록에서 확장 **ComponentPort**를 확장 하 고 **ComponentHasPorts**를 선택한 후 **구성 요소**.

    새 경로이 다음과 유사 합니다.

    **ComponentHasPorts.Component/!Component**

9. 솔루션을 저장 하 고 다음에서 맨 오른쪽 단추를 클릭 하 여 템플릿을 변형 합니다 **솔루션 탐색기** 도구 모음입니다.

10. 솔루션을 빌드하고 실행합니다. Visual Studio의 새 인스턴스가 표시 됩니다.

11. **솔루션 탐색기**, Sample.mydsl를 엽니다. 다이어그램 및 **ComponentLanguage 도구 상자** 표시 합니다.

12. 끌어서는 **Input Port** 에서 합니다 **도구 상자** 다른 **입력 포트입니다.** 다음으로 끌어를 **OutputPort** 에 **InputPort** 다음에 또 다른 **OutputPort**합니다.

     포인터를 사용할 수 없게 표시 되지 않아야 하 고 새 있으려면 **입력 포트** 기존에 있습니다. 새 선택 **입력 포트** 다른 지점으로 놓습니다 합니다 **구성 요소**합니다.

## <a name="see-also"></a>참고 항목

- [프로그램 코드에서 모델 탐색 및 업데이트](../modeling/navigating-and-updating-a-model-in-program-code.md)
- [도구 및 도구 상자 사용자 지정](../modeling/customizing-tools-and-the-toolbox.md)
- [회로 다이어그램 샘플 DSL](https://code.msdn.microsoft.com/Visualization-Modeling-SDK-763778e8)