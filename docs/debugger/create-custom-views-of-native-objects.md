---
title: C++ 개체의 사용자 지정 뷰 만들기
description: Natvis 프레임 워크를 사용 하 여 Visual Studio 디버거에서 네이티브 형식을 표시 하는 방식을 사용자 지정 하려면
ms.date: 10/31/2018
ms.topic: conceptual
f1_keywords:
- natvis
dev_langs:
- C++
ms.assetid: 2d9a177a-e14b-404f-a6af-49498eff0bd7
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: f8ef28b453ba6c754c337c5d42581bd658be5f04
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62564482"
---
# <a name="create-custom-views-of-c-objects-in-the-debugger"></a>사용자 지정 뷰 만들기 C++ 디버거에서 개체

Visual Studio *Natvis* 프레임 워크와 같은 디버거 변수 창에 네이티브 형식을 표시 하는 방법을 사용자 지정 합니다 **지역** 하 고 **조사식** windows에 **DataTips**합니다. Natvis 시각화를 디버깅 하는 동안 더 잘 보이도록 만들 형식을 도움이 됩니다.

Natvis 대체 합니다 *autoexp.dat* XML 구문, 보다 효과적인 진단, 버전 관리를 사용 하 여 이전 버전의 Visual Studio에서 파일 및 여러 파일을 지원 합니다.

## <a name="BKMK_Why_create_visualizations_"></a>Natvis 시각화

Natvis 프레임 워크를 사용 하 여 개발자가 디버깅 하는 동안 더 쉽게 볼 수 있도록를 만든 형식에 대 한 시각화 규칙을 만듭니다.

예를 들어, 다음 그림과 형식 변수의 [되지](http://go.microsoft.com/fwlink/?LinkId=258422) 사용자 지정 시각화가 적용 되는 디버거 창에서입니다.

![TextBox 기본 시각화](../debugger/media/dbg_natvis_textbox_default.png "TextBox 기본 시각화")

강조 표시된 행은 `Text` 클래스의 `TextBox` 속성을 보여 줍니다. 복잡 한 클래스 계층 구조를 사용 하면이 속성을 찾을 어려워집니다. 디버거가는 텍스트 상자 내에 들어 있는 문자열을 볼 수 없습니다. 사용자 지정 문자열 형식을 해석 하는 방법을 알지 못합니다.

동일한 `TextBox` Natvis 시각화 도우미 사용자 지정 규칙이 적용 되 면 변수 창에서 훨씬 간단 하 게 표시 합니다. 클래스의 중요 한 멤버 함께 나타나고 디버거 사용자 지정 문자열 형식의 기본 문자열 값을 보여 줍니다.

![시각화 도우미를 사용 하 여 텍스트 데이터](../debugger/media/dbg_natvis_textbox_visualizer.png "시각화 도우미를 사용 하 여 텍스트 데이터")

## <a name="BKMK_Using_Natvis_files"></a>.natvis 파일을 사용 하 여 C++ 프로젝트

다음을 사용 하 여 Natvis *.natvis* 시각화 규칙을 지정 하는 파일입니다. A *.natvis* 파일이 사용 하 여 XML 파일을 *.natvis* 확장 합니다. Natvis 스키마에 정의 되어 *%VSINSTALLDIR%\Xml\Schemas\natvis.xsd*합니다.

기본 구조를 *.natvis* 파일은 하나 이상의 `Type` 시각화 항목을 나타내는 요소입니다. 각 정규화 된 이름이 `Type` 에 지정 된 요소가 해당 `Name` 특성입니다.

```xml
<?xml version="1.0" encoding="utf-8"?>
<AutoVisualizer xmlns="http://schemas.microsoft.com/vstudio/debugger/natvis/2010">
  <Type Name="MyNamespace::CFoo">
    .
    .
  </Type>

  <Type Name="...">
    .
    .
  </Type>
</AutoVisualizer>
```

Visual Studio에는 일부 *.natvis* 파일을 *%VSINSTALLDIR%\Common7\Packages\Debugger\Visualizers* 폴더입니다. 이러한 파일은 많은 공통 형식에 대 한 시각화 규칙이 새 형식에 대 한 시각화를 작성 하기 위한 예제로 사용할 수 있습니다.

### <a name="add-a-natvis-file-to-a-c-project"></a>.Natvis 파일을 추가할는 C++ 프로젝트

추가할 수는 *.natvis* 파일에 C++ 프로젝트입니다.

**새 추가할 *.natvis* 파일:**

1. 선택 된 C++ 에서 프로젝트 노드 **솔루션 탐색기**를 선택한 **프로젝트** > **새 항목 추가**, 또는 프로젝트를 마우스 오른쪽 단추로 클릭 하 고 선택 **추가** > **새 항목**합니다.

1. 에 **새 항목 추가** 대화 상자에서 **시각적 C++**   >  **유틸리티** > **디버거 시각화 파일 (.natvis)** .

1. 선택한 파일 이름을 **추가**합니다.

   새 파일에 추가 됩니다 **솔루션 탐색기**, Visual Studio 문서 창에서 열립니다.

Visual Studio 디버거를 로드 *.natvis* 파일 C++ 프로젝트를 자동으로 하 고 기본적으로 또한에 *.pdb* 프로젝트가 빌드될 때 파일입니다. 디버거를 로드 하는 기본 제공된 앱을 디버그 하는 경우는 *.natvis* 에서 파일을 *.pdb* 파일을 프로젝트를 열고 없는 경우에 합니다. 하지 못하도록 하려는 경우는 *.natvis* 에 포함 된 파일을 *.pdb*, 기본 제공에서 제외할 수 있습니다 *.pdb* 파일입니다.

**제외에 *.natvis* 에서 파일을 *.pdb*:**

1. 선택는 *.natvis* 파일 **솔루션 탐색기**를 선택 하 고는 **속성** 아이콘을 또는 파일을 마우스 오른쪽 단추로 클릭 하 고 선택 **속성**.

1. 화살표 옆에 드롭다운 **빌드에서 제외** 선택한 **예**를 선택한 후 **확인**합니다.

>[!NOTE]
>실행 파일 프로젝트의 디버깅을 위해 추가할 솔루션 항목을 사용 *.natvis* 에 없는 파일을 *.pdb*되므로, 없습니다 C++ 프로젝트를 사용할 수 있습니다.

>[!NOTE]
>Natvis 규칙에서 로드를 *.pdb* 모듈의 형식에만 적용 하는 *.pdb* 가리킵니다. 예를 들어, 경우 *Module1.pdb* 명명 된 형식에 대해 Natvis 항목이 `Test`에 적용 됩니다는 `Test` 클래스 *Module1.dll*. 다른 모듈은 또한 라는 클래스를 정의 하는 경우 `Test`서 *module1.pdb가* Natvis 항목에 적용 되지 않습니다.

### <a name="BKMK_natvis_location"></a> Natvis 파일 위치

추가할 수 있습니다 *.natvis* 파일을 사용자 디렉터리 또는 시스템 디렉터리에 여러 프로젝트에 적용 하려는 경우.

합니다 *.natvis* 파일은 다음 순서로 평가 됩니다.

1. 모든 *.natvis* 에 포함 된 파일을 *.pdb* 로드 된 프로젝트에서 동일한 이름의 파일이 존재 하지 않는 경우 디버그 하 합니다.

2. 모든 *.natvis* 로드에 있는 파일을 C++ 프로젝트 또는 최상위 솔루션입니다. 이 그룹에 로드 된 모든 C++ 프로젝트에 클래스 라이브러리를 포함 하 여 하지만 다른 언어의 프로젝트 없습니다.

::: moniker range="vs-2017"

3. 사용자별 Natvis 디렉터리 (예를 들어 *%USERPROFILE%\Documents\Visual Studio 2017\Visualizers*).

::: moniker-end

::: moniker range=">= vs-2019"

3. 사용자별 Natvis 디렉터리 (예를 들어 *%USERPROFILE%\Documents\Visual Studio 2019\Visualizers*).

::: moniker-end

4. 시스템 차원 Natvis 디렉터리(*%VSINSTALLDIR%\Common7\Packages\Debugger\Visualizers*). 이 디렉터리에는 *.natvis* Visual Studio와 함께 설치 되는 파일입니다. 관리자 권한이 있는 경우에이 디렉터리에 파일을 추가할 수 있습니다.

## <a name="modify-natvis-files-while-debugging"></a>디버깅 하는 동안.natvis 파일을 수정 합니다.

수정할 수는 *.natvis* 해당 프로젝트를 디버깅 하는 동안 IDE에서 파일입니다. 사용 하면 디버깅 하는 Visual Studio의 동일한 인스턴스에 파일을 열고, 수정 및 저장 파일이 저장 되 면 즉시 합니다 **조사식** 및 **지역** windows 업데이트 변경 내용을 반영 합니다.

추가 하거나 삭제할 수도 있습니다 *.natvis* 디버그 하 고 Visual Studio를 추가 하거나 관련 시각화 요소를 제거 하는 솔루션 파일입니다.

업데이트할 수 없습니다 *.natvis* 파일에 포함 된 *.pdb* 디버깅할 때 파일입니다.

수정 하는 경우는 *.natvis* 파일 Visual Studio 외부에서 변경 내용이 적용 되지 않습니다 자동으로 합니다. 디버거 창을 업데이트를 다시 평가할 수 있습니다는 **.natvisreload** 명령에 **조사식** 창입니다. 그런 다음 변경 내용을 디버깅 세션을 다시 시작 하지 않고 적용 합니다.

또한 사용 하 여는 **.natvisreload** 업그레이드 하는 명령 합니다 *.natvis* 최신 버전으로 파일. 예를 들어를 *.natvis* 파일 소스 제어에 체크 인할 수 있습니다 및 다른 사용자가 최근 변경 내용을 선택 하려고 합니다.

## <a name="BKMK_Expressions_and_formatting"></a> 식 및 형식 지정
Natvis 시각화에서는 C++ 식을 사용하여 표시할 데이터 항목을 지정합니다. 향상 된 기능 및 제한 사항 외에도 C++ 에 설명 된 디버거에서 식을 [컨텍스트 연산자 (C++)](../debugger/context-operator-cpp.md), 다음에 유의 합니다.

- Natvis 식은 현재 스택 프레임이 아닌 시각화되는 개체의 컨텍스트에서 평가됩니다. 예를 들어 `x` 라는 필드 참조 식에는 Natvis **x** 라는 지역 변수 필요가 시각화 되는 개체에 **x** 현재 함수에서. Natvis 식 내의 지역 변수는 액세스할 수 없지만 전역 변수에 액세스할 수 있습니다.

- Natvis 식 함수 평가 또는 부작용을 허용 하지 않습니다. 함수 호출 및 할당 연산자는 무시 됩니다. [디버거 내장 함수](../debugger/expressions-in-the-debugger.md#BKMK_Using_debugger_intrinisic_functions_to_maintain_state) 는 부작용이 발생하지 않기 때문에 다른 함수 호출이 금지되어 있더라도 어떤 Natvis 식에서든 자유롭게 호출할 수 있습니다.

- 식을 표시 하는 방법을 제어 하에 설명 된 형식 지정자를 사용할 수 있습니다 [형식 지정자에서 C++ ](format-specifiers-in-cpp.md#BKMK_Visual_Studio_2012_format_specifiers)합니다. 항목에서를 사용할 때 내부적으로 Natvis 같은 서식 지정자는 무시 합니다 `Size` 식에는 [ArrayItems 확장](../debugger/create-custom-views-of-native-objects.md#BKMK_ArrayItems_expansion).

## <a name="natvis-views"></a>Natvis 뷰

다른 방법으로 형식을 표시 하려면 다른 Natvis 뷰를 정의할 수 있습니다. 예를 들어 여기서는의 시각화 요소 `std::vector` 라는 간단한 뷰를 정의 하는 `simple`합니다. `DisplayString` 및 `ArrayItems` 기본 보기에 표시 된 요소 및 `simple` 보기 동안 합니다 `[size]` 및 `[capacity]` 항목에 표시 되지는 `simple` 보기.

```xml
<Type Name="std::vector&lt;*&gt;">
    <DisplayString>{{ size={_Mylast - _Myfirst} }}</DisplayString>
    <Expand>
        <Item Name="[size]" ExcludeView="simple">_Mylast - _Myfirst</Item>
        <Item Name="[capacity]" ExcludeView="simple">_Myend - _Myfirst</Item>
        <ArrayItems>
            <Size>_Mylast - _Myfirst</Size>
            <ValuePointer>_Myfirst</ValuePointer>
        </ArrayItems>
    </Expand>
</Type>
```

에 **조사식** 창을 사용 하 여는 **, 보기** 형식 지정자를 대체 뷰를 지정할 합니다. 로 simple 뷰 나타납니다 **vec,view(simple)**:

![간단한 뷰를 사용 하 여 조사식 창이](../debugger/media/watch-simpleview.png "간단한 뷰를 사용 하 여 조사식 창")

## <a name="BKMK_Diagnosing_Natvis_errors"></a> Natvis 오류

디버거 시각화 항목에서 오류가 발생 하는 무시 합니다. 형식을 원시 형식으로 표시 하거나 적합 한 다른 시각화를 선택 합니다. 디버거 시각화 항목을 무시 하는 이유를 파악 하 고 기본 구문 및 구문 분석 오류에 Natvis 진단을 사용할 수 있습니다.

**Natvis 진단을 켜려면:**

- 아래 **도구가** > **옵션** (또는 **디버그** > **옵션**) > **디버깅**  >  **출력 창**설정 **Natvis 진단 메시지 (C++ 만)** 하 **오류**합니다 **경고** 또는 **Verbose**를 선택한 후 **확인**합니다.

에 오류가 표시 되는 **출력** 창입니다.

## <a name="BKMK_Syntax_reference"></a> Natvis 구문 참조

### <a name="BKMK_AutoVisualizer"></a> AutoVisualizer 요소
`AutoVisualizer` 요소는 *.natvis* 파일의 루트 노드이며 네임스페이스 `xmlns:` 특성을 포함합니다.

```xml
<?xml version="1.0" encoding="utf-8"?>
<AutoVisualizer xmlns="http://schemas.microsoft.com/vstudio/debugger/natvis/2010">
.
.
</AutoVisualizer>
```

`AutoVisualizer` 요소가 있을 수 있습니다 [형식](#BKMK_Type), [HResult](#BKMK_HResult)를 [UIVisualizer](#BKMK_UIVisualizer), 및 [CustomVisualizer](#BKMK_CustomVisualizer) 자식입니다.

### <a name="BKMK_Type"></a> Type 요소

기본 `Type` 이 예제 것 같습니다.

```xml
<Type Name="[fully qualified type name]">
  <DisplayString Condition="[Boolean expression]">[Display value]</DisplayString>
  <Expand>
    ...
  </Expand>
</Type>
```

 `Type` 요소를 지정 합니다.

1. 시각화 유형을 사용 해야 (의 `Name` 특성).

2. 이 형식의 개체 값이 표시되는 모양( `DisplayString` 요소)

3. 사용자 입력 변수 창에서을 확장 하는 경우 형식의 멤버 모양을 (의 `Expand` 노드).

#### <a name="templated-classes"></a>템플릿 클래스
`Name` 특성을 `Type` 요소에는 별표 `*` 템플릿 클래스 이름에 사용할 수 있는 와일드 카드 문자로 합니다.

다음 예제에서는 동일한 시각화가 개체 인지 사용을 `CAtlArray<int>` 또는 `CAtlArray<float>`합니다. 에 대 한 특정 시각화 항목이 있으면를 `CAtlArray<float>`, 다음 일반적인 단어는 무시 됩니다.

```xml
<Type Name="ATL::CAtlArray&lt;*&gt;">
    <DisplayString>{{Count = {m_nSize}}}</DisplayString>
</Type>
```

등 고 매크로 $T1, $T2를 사용 하 여 시각화 항목에서 템플릿 매개 변수를 참조할 수 있습니다. 이러한 매크로의 예를 살펴보려면 Visual Studio와 함께 제공되는 *.natvis* 파일을 참조하세요.

#### <a name="BKMK_Visualizer_type_matching"></a> 시각화 도우미 형식 일치
유효성 검사에 실패 하면 시각화 항목을 다음으로 사용 가능한 시각화가 됩니다.

#### <a name="inheritable-attribute"></a>상속 가능한 특성
선택적 `Inheritable` 특성 시각화 기본 형식에만 적용 됩니다. 기본 형식 및 모든 파생 형식 하는지 여부를 지정 합니다. `Inheritable` 의 기본값은 `true`입니다.

다음 예제에서는 시각화에만 적용 됩니다는 `BaseClass` 형식:

```xml
<Type Name="Namespace::BaseClass" Inheritable="false">
    <DisplayString>{{Count = {m_nSize}}}</DisplayString>
</Type>
```

#### <a name="priority-attribute"></a>Priority 특성

선택적 `Priority` 특성 정의 구문 분석 하지 못하는 경우 대체 정의가 사용 하는 순서를 지정 합니다. 가능한 값 `Priority` 는: `Low`, `MediumLow`,`Medium`합니다 `MediumHigh`, 및 `High`합니다. 기본값은 `Medium`입니다. 합니다 `Priority` 특성을 구별할 수만 동일한 우선 순위 *.natvis* 파일입니다.

다음 예제에는 먼저 2015 STL과 일치 하는 항목을 구문 분석 합니다. 구문 분석에 실패 하는 경우에 대체 항목을 사용 하 여 STL의 2013 버전:

```xml
<!-- VC 2013 -->
<Type Name="std::reference_wrapper&lt;*&gt;" Priority="MediumLow">
     <DisplayString>{_Callee}</DisplayString>
    <Expand>
        <ExpandedItem>_Callee</ExpandedItem>
    </Expand>
</Type>

<!-- VC 2015 -->
<Type Name="std::reference_wrapper&lt;*&gt;">
    <DisplayString>{*_Ptr}</DisplayString>
    <Expand>
        <Item Name="[ptr]">_Ptr</Item>
    </Expand>
</Type>
```

### <a name="optional-attribute"></a>Optional 특성
넣을 수는 `Optional` 노드에 특성입니다. 선택적 노드 내의 하위 식을 구문 분석할 수 실패할 경우 디버거에서 해당 노드를 무시 하지만를의 나머지 부분을 적용 하는 `Type` 규칙입니다. 다음 형식에서 `[State]` 는 필수이지만 `[Exception]` 은 선택적입니다.  경우 `MyNamespace::MyClass` _ 라는 필드가`M_exceptionHolder`모두를 `[State]` 노드 및 `[Exception]` 경우 노드가 표시 되지 않습니다 `_M_exceptionHolder` 필드에를 `[State]` 노드가 표시 됩니다.

```xml
<Type Name="MyNamespace::MyClass">
    <Expand>
      <Item Name="[State]">_M_State</Item>
      <Item Name="[Exception]" Optional="true">_M_exceptionHolder</Item>
    </Expand>
</Type>
```

### <a name="BKMK_Condition_attribute"></a> 조건 특성

선택적 `Condition` 특성은 많은 시각화 요소를 사용할 수 있으며 시각화 규칙을 사용 하는 시기를 지정 합니다. Condition 특성 내부의 식이로 확인 되 면 `false`, 시각화 규칙이 적용 되지 않습니다. 로 평가 되 면 `true`, 없거나 없습니다 `Condition` 특성인 시각화 적용 됩니다. 시각화 항목에 if-else 논리에 대 한이 특성을 사용할 수 있습니다.

예를 들어, 다음 시각화에는 두 개의 `DisplayString` 스마트 포인터 형식에 대 한 요소입니다. 경우는 `_Myptr` 멤버가 비어 첫 번째 조건이 `DisplayString` 요소를 확인 `true`이므로 해당 폼에 표시 됩니다. 경우는 `_Myptr` 멤버를 비어 있지, 조건이 `false`, 및 두 번째 `DisplayString` 요소에 표시 됩니다.

```xml
<Type Name="std::auto_ptr&lt;*&gt;">
  <DisplayString Condition="_Myptr == 0">empty</DisplayString>
  <DisplayString>auto_ptr {*_Myptr}</DisplayString>
  <Expand>
    <ExpandedItem>_Myptr</ExpandedItem>
  </Expand>
</Type>
```

### <a name="includeview-and-excludeview-attributes"></a>IncludeView 및 ExcludeView 특성

합니다 `IncludeView` 고 `ExcludeView` 특성 요소에서 특정 보기를 표시할지 여부를 지정 합니다. Natvis 사양을에서 예를 들어 `std::vector`는 `simple` 보기에는 표시 하지 않습니다는 `[size]` 및 `[capacity]` 항목입니다.

```xml
<Type Name="std::vector&lt;*&gt;">
    <DisplayString>{{ size={_Mylast - _Myfirst} }}</DisplayString>
    <Expand>
        <Item Name="[size]" ExcludeView="simple">_Mylast - _Myfirst</Item>
        <Item Name="[capacity]" ExcludeView="simple">_Myend - _Myfirst</Item>
        <ArrayItems>
            <Size>_Mylast - _Myfirst</Size>
            <ValuePointer>_Myfirst</ValuePointer>
        </ArrayItems>
    </Expand>
</Type>
```

사용할 수는 `IncludeView` 및 `ExcludeView` 형식 및 개별 멤버 특성이 있습니다.

### <a name="BKMK_Versioning"></a> Version 요소
`Version` 요소 범위 시각화 항목을 특정 모듈 및 버전을 지정 합니다. `Version` 요소 이름 충돌을 방지할 수, 실수로 인 한 불일치 감소 및 서로 다른 형식 버전에 대 한 서로 다른 시각화 요소를 허용 합니다.

형식을 정의 하는 다른 모듈에서 사용 되는 공통 헤더 파일, 버전이 지정 된 시각화 유형이 지정 된 모듈 버전의 경우에 나타납니다.

다음 예제에서는 시각화에만 적용 됩니다는 `DirectUI::Border` 형식에는 `Windows.UI.Xaml.dll` 버전 1.0부터 1.5에서에서.

```xml
<Type Name="DirectUI::Border">
  <Version Name="Windows.UI.Xaml.dll" Min="1.0" Max="1.5"/>
  <DisplayString>{{Name = {*(m_pDO->m_pstrName)}}}</DisplayString>
  <Expand>
    <ExpandedItem>*(CBorder*)(m_pDO)</ExpandedItem>
  </Expand>
</Type>
```

### <a name="BKMK_DisplayString"></a> DisplayString 요소
`DisplayString` 요소 변수의 값으로 표시할 문자열을 지정 합니다. 또한 식과 혼합된 임의의 문자열을 허용합니다. 중괄호 내의 모든 항목은 식으로 해석됩니다. 예를 들어, 다음 `DisplayString` 항목:

```xml
<Type Name="CPoint">
  <DisplayString>{{x={x} y={y}}}</DisplayString>
</Type>
```

의미 형식의 변수는 `CPoint` 이 그림과 같이 표시 합니다.

 ![DisplayString 요소를 사용 하 여](../debugger/media/dbg_natvis_cpoint_displaystring.png "DisplayString 요소 사용")

에 `DisplayString` 식 `x` 하 고 `y`, 멤버의 `CPoint`, 중괄호 안에 되므로 해당 값이 계산 됩니다. 또한이 예제에서는 이중 중괄호를 사용 하 여 중괄호 이스케이프할 수 있습니다 ( `{{` 또는 `}}` ).

> [!NOTE]
> `DisplayString` 요소는 임의 문자열 및 중괄호 구문을 허용하는 유일한 요소입니다. 다른 모든 시각화 요소에는 디버거를 실행할 수 있는 식만 허용 합니다.

### <a name="BKMK_StringView"></a> StringView 요소

`StringView` 요소 디버거는 기본 제공 텍스트 시각화 도우미로 보낼 수 있는 값을 정의 합니다. 예를 들어, 다음 시각화에 대 한 지정 된 된 `ATL::CStringT` 형식:

```xml
<Type Name="ATL::CStringT&lt;wchar_t,*&gt;">
  <DisplayString>{m_pszData,su}</DisplayString>
</Type>
```

`CStringT` 이 예제에서와 같이 변수 창의 개체를 표시 합니다.

![CStringT DisplayString 요소](../debugger/media/dbg_natvis_displaystring_cstringt.png "CStringT DisplayString 요소")

추가 된 `StringView` 요소 값을 텍스트 시각화로 표시할 수 디버거에 지시 합니다.

```xml
<Type Name="ATL::CStringT&lt;wchar_t,*&gt;">
  <DisplayString>{m_pszData,su}</DisplayString>
  <StringView>m_pszData,su</StringView>
</Type>
```

디버그 하는 동안 있습니다 수 해당 변수 옆에 돋보기 아이콘을 선택한 후 **텍스트 시각화 도우미** 문자열을 표시 하는 **m_pszData** 가리킵니다.

 ![StringView 시각화 도우미가 있는 CStringT 데이터](../debugger/media/dbg_natvis_stringview_cstringt.png "StringView 시각화 도우미가 있는 CStringT 데이터")

식 `{m_pszData,su}` 포함 됩니다는 C++ 형식 지정자 **su**을 유니코드 문자열로 값을 표시 합니다. 자세한 내용은 [형식 지정자에서 C++ ](../debugger/format-specifiers-in-cpp.md)합니다.

### <a name="BKMK_Expand"></a> 요소 확장

선택적 `Expand` 노드 변수 창에서 형식을 확장 하면 시각화 된 형식의 자식을 사용자 지정 합니다. `Expand` 노드 자식 요소를 정의 하는 자식 노드의 목록을 허용 합니다.

- 경우는 `Expand` 기본 확장 규칙을 사용 하는 자식 노드가 시각화 항목을에 지정 되지 않습니다.

- 경우는 `Expand` 노드 아래에 자식 노드가 없는 지정 된 형식을 디버거 창에서 확장 되지 않습니다.

#### <a name="BKMK_Item_expansion"></a> 항목 확장

 합니다 `Item` 요소는 가장 기본 및 일반 요소에는 `Expand` 노드. `Item` 은 단일 자식 요소를 정의합니다. 예를 들어, 한 `CRect` 필드를 사용 하 여 클래스 `top`, `left`, `right`, 및 `bottom` 다음과 같은 시각화 항목이:

```xml
<Type Name="CRect">
  <DisplayString>{{top={top} bottom={bottom} left={left} right={right}}}</DisplayString>
  <Expand>
    <Item Name="Width">right - left</Item>
    <Item Name="Height">bottom - top</Item>
  </Expand>
</Type>
```

디버거 창에는 `CRect` 형식이 예제와 같습니다.

![항목 요소 확장을 사용 하 여 CRect](../debugger/media/dbg_natvis_expand_item_crect1.png "항목 요소 확장을 사용 하 여 CRect")

에 지정 된 식을 평가 하는 디버거를 `Width` 및 `Height` 요소에서 값을 표시 하 고는 **값** 변수 창의 열.

디버거가 자동으로 생성 합니다 **[Raw 뷰]** 모든 사용자 지정 확장에 대 한 노드. 이전 스크린샷에서 표시 된 **[Raw 뷰]** 개체의 기본 raw 뷰가 해당 Natvis 시각화에서 어떻게 다른 지를 표시 하려면 노드를 확장 합니다. 기본 확장 기본 클래스의 하위 트리를 만들고 모든 데이터 멤버는 기본 클래스의 자식으로 나열 합니다.

> [!NOTE]
> 항목 요소의 식이 복합 형식을 가리키는 경우 합니다 **항목** 노드 자체를 확장할 수 있습니다.

#### <a name="BKMK_ArrayItems_expansion"></a> Size
`ArrayItems` 노드를 사용하면 Visual Studio 디버거가 형식을 배열로 해석하고 해당 개별 요소를 표시하도록 할 수 있습니다. `std::vector` 에 대한 시각화는 좋은 예입니다.

```xml
<Type Name="std::vector&lt;*&gt;">
  <DisplayString>{{size = {_Mylast - _Myfirst}}}</DisplayString>
  <Expand>
    <Item Name="[size]">_Mylast - _Myfirst</Item>
    <Item Name="[capacity]">(_Myend - _Myfirst)</Item>
    <ArrayItems>
      <Size>_Mylast - _Myfirst</Size>
      <ValuePointer>_Myfirst</ValuePointer>
    </ArrayItems>
  </Expand>
</Type>
```

`std::vector` 는 변수 창에서 확장되는 경우 개별 요소를 표시합니다.

![ArrayItems 확장을 사용 하는 std:: vector](../debugger/media/dbg_natvis_expand_arrayitems_stdvector.png "ArrayItems 확장을 사용 하는 std:: vector")

`ArrayItems` 노드에 있어야 합니다.

- 디버거에서 배열의 길이를 파악하기 위한 `Size` 식(정수로 계산되어야 함)입니다.
- A `ValuePointer` 첫 번째 요소를 가리키는 식이 (아닌 요소 형식의 포인터 여야 `void*`).

배열 하한의 기본값은 0입니다. 값을 재정의 하려면 사용을 `LowerBound` 요소입니다. 합니다 *.natvis* Visual Studio와 함께 제공 되는 파일의 한 예입니다.

>[!NOTE]
>사용할 수는 `[]` 예를 들어 연산자 `vector[i]`를 사용 하는 1 차원 배열 시각화를 사용 하 여 `ArrayItems`경우에 형식 자체 (예를 들어 `CATLArray`)이이 연산자를 허용 하지 않습니다.

다차원 배열도 지정할 수 있습니다. 이 경우 디버거에는 자식 요소를 올바르게 표시할 약간 더 많은 정보가 필요 합니다.

```xml
<Type Name="Concurrency::array&lt;*,*&gt;">
  <DisplayString>extent = {_M_extent}</DisplayString>
  <Expand>
    <Item Name="extent">_M_extent</Item>
    <ArrayItems Condition="_M_buffer_descriptor._M_data_ptr != 0">
      <Direction>Forward</Direction>
      <Rank>$T2</Rank>
      <Size>_M_extent._M_base[$i]</Size>
      <ValuePointer>($T1*) _M_buffer_descriptor._M_data_ptr</ValuePointer>
    </ArrayItems>
  </Expand>
</Type>
```

- `Direction` 배열 행 중심 순서 인지 열 중심 순서 인지 여부를 지정 합니다.
- `Rank` 는 배열의 차수를 지정합니다.
- `Size` 요소는 해당 차원에서 배열의 길이를 확인하기 위해 차원 인덱스로 대체되는 암시적 `$i` 매개 변수를 허용합니다. 이전 예제에서는 식 `_M_extent.M_base[0]` 0 번째 차원의 길이 지정 해야 `_M_extent._M_base[1]` 자사, 및 등입니다.

방법 2 차원 같습니다 `Concurrency::array` 디버거 창에서 개체를 찾습니다.

![ArrayItems 확장이 있는 2 차원 배열](../debugger/media/dbg_natvis_expand_arrayitems_2d.png "ArrayItems 확장이 있는 2 차원 배열")

#### <a name="BKMK_IndexListItems_expansion"></a> IndexListItems 확장

사용할 수 있습니다 `ArrayItems` 배열 요소는 연속적으로 메모리에 배치 하는 경우에 확장 합니다. 디버거는 포인터를 늘리는 방식으로 다음 요소를 가져옵니다. 인덱스 값 노드를 조작 해야 하는 경우 사용 하 여 `IndexListItems` 노드. 여기에 사용 하 여 시각화 요소는 `IndexListItems` 노드:

```xml
<Type Name="Concurrency::multi_link_registry&lt;*&gt;">
  <DisplayString>{{size = {_M_vector._M_index}}}</DisplayString>
  <Expand>
    <Item Name="[size]">_M_vector._M_index</Item>
    <IndexListItems>
      <Size>_M_vector._M_index</Size>
      <ValueNode>*(_M_vector._M_array[$i])</ValueNode>
    </IndexListItems>
  </Expand>
</Type>
```

간의 유일한 차이점 `ArrayItems` 및 `IndexListItems` 은 합니다 `ValueNode`, i 전체 식이 있어야 하는<sup>번째</sup> 암시적 요소 `$i` 매개 변수입니다.

>[!NOTE]
>사용할 수는 `[]` 예를 들어 연산자 `vector[i]`를 사용 하는 1 차원 배열 시각화를 사용 하 여 `IndexListItems`경우에 형식 자체 (예를 들어 `CATLArray`)이이 연산자를 허용 하지 않습니다.

#### <a name="BKMK_LinkedListItems_expansion"></a> LinkedListItems 확장

시각화된 형식이 링크된 목록을 나타내는 경우 디버거에서는 `LinkedListItems` 노드를 사용하여 해당 자식을 표시할 수 있습니다. 에 대 한 다음과 같은 시각화를 `CAtlList` 사용 하 여 입력 `LinkedListItems`:

```xml
<Type Name="ATL::CAtlList&lt;*,*&gt;">
  <DisplayString>{{Count = {m_nElements}}}</DisplayString>
  <Expand>
    <Item Name="Count">m_nElements</Item>
    <LinkedListItems>
      <Size>m_nElements</Size>
      <HeadPointer>m_pHead</HeadPointer>
      <NextPointer>m_pNext</NextPointer>
      <ValueNode>m_element</ValueNode>
    </LinkedListItems>
  </Expand>
</Type>
```

`Size` 요소는 목록의 길이를 참조합니다. `HeadPointer` 는 첫 번째 요소를 가리키고, `NextPointer` 는 다음 요소를 참조하며, `ValueNode` 는 항목의 값을 참조합니다.

디버거에서 `NextPointer` 하 고 `ValueNode` 식의 컨텍스트에서 `LinkedListItems` 노드 요소, 부모 목록 형식이 아닌. 이전 예에서 `CAtlList` 에 `CNode` 클래스 (있는 `atlcoll.h`) 연결 된 목록의 노드는 합니다. `m_pNext` 및 `m_element` 의 필드 `CNode` 클래스 아닌는 `CAtlList` 클래스입니다.

`ValueNode` 비어 있을 수 있습니다, 또는 사용 하 여 `this` 를 참조 하는 `LinkedListItems` 노드 자체입니다.

#### <a name="customlistitems-expansion"></a>CustomListItems 확장
`CustomListItems` 확장을 사용하여 해시 테이블 같은 데이터 구조 전송에 대한 사용자 지정 논리를 작성할 수 있습니다. 사용 하 여 `CustomListItems` 사용할 수 있는 데이터 구조를 시각화 하 C++ 를 평가 하는 데 필요한 모든 것에 대 한 식의 유형에 적합 하지 않은 하지만 `ArrayItems`, `IndexListItems`, 또는 `LinkedListItems`합니다.

다음 시각화 도우미 `CAtlMap` 는 가장 좋은 예는 `CustomListItems` 적합 합니다.

```xml
<Type Name="ATL::CAtlMap&lt;*,*,*,*&gt;">
    <AlternativeType Name="ATL::CMapToInterface&lt;*,*,*&gt;"/>
    <AlternativeType Name="ATL::CMapToAutoPtr&lt;*,*,*&gt;"/>
    <DisplayString>{{Count = {m_nElements}}}</DisplayString>
    <Expand>
      <CustomListItems MaxItemsPerView="5000" ExcludeView="Test">
        <Variable Name="iBucket" InitialValue="-1" />
        <Variable Name="pBucket" InitialValue="m_ppBins == nullptr ? nullptr : *m_ppBins" />
        <Variable Name="iBucketIncrement" InitialValue="-1" />

        <Size>m_nElements</Size>
        <Exec>pBucket = nullptr</Exec>
        <Loop>
          <If Condition="pBucket == nullptr">
            <Exec>iBucket++</Exec>
            <Exec>iBucketIncrement = __findnonnull(m_ppBins + iBucket, m_nBins - iBucket)</Exec>
            <Break Condition="iBucketIncrement == -1" />
            <Exec>iBucket += iBucketIncrement</Exec>
            <Exec>pBucket = m_ppBins[iBucket]</Exec>
          </If>
          <Item>pBucket,na</Item>
          <Exec>pBucket = pBucket->m_pNext</Exec>
        </Loop>
      </CustomListItems>
    </Expand>
</Type>
```

사용할 수 있습니다 `Exec` 내부에서 코드를 실행 하는 `CustomListItems` 변수 및 확장에 정의 된 개체를 사용 하 여 확장 합니다. 논리 연산자, 산술 연산자 및 대입 연산자를 사용할 수 `Exec`입니다. 사용할 수 없습니다 `Exec` 함수를 평가 합니다.

`CustomListItems` 다음 내장 함수를 지원합니다.

- `strlen`, `wcslen`, `strnlen`, `wcsnlen`, `strcmp`, `wcscmp`, `_stricmp`, `_strcmpi`, `_wcsicmp`, `strncmp`, `wcsncmp`, `_strnicmp`, `_wcsnicmp`, `memcmp`, `memicmp`, `wmemcmp`, `strchr`, `wcschr`, `memchr`, `wmemchr`, `strstr`, `wcsstr`, `__log2`, `__findNonNull`
- `GetLastError`, `TlsGetValue`, `DecodeHString`, `WindowsGetStringLen`, `WindowsGetStringRawBuffer`, `WindowsCompareStringOrdinal`, `RoInspectCapturedStackBackTrace`, `CoDecodeProxy`, `GetEnvBlockLength`, `DecodeWinRTRestrictedException`, `DynamicMemberLookup`, `DecodePointer`, `DynamicCast`
- `ConcurrencyArray_OperatorBracket_idx // Concurrency::array<>::operator[index<>] and operator(index<>)`
- `ConcurrencyArray_OperatorBracket_int // Concurrency::array<>::operator(int, int, ...)`
- `ConcurrencyArray_OperatorBracket_tidx // Concurrency::array<>::operator[tiled_index<>] and operator(tiled_index<>)`
- `ConcurrencyArrayView_OperatorBracket_idx // Concurrency::array_view<>::operator[index<>] and operator(index<>)`
- `ConcurrencyArrayView_OperatorBracket_int // Concurrency::array_view<>::operator(int, int, ...)`
- `ConcurrencyArrayView_OperatorBracket_tidx // Concurrency::array_view<>::operator[tiled_index<>] and operator(tiled_index<>)`
- `Stdext_HashMap_Int_OperatorBracket_idx`
- `Std_UnorderedMap_Int_OperatorBracket_idx`
- `TreeTraverse_Init // Initializes a new tree traversal`
- `TreeTraverse_Next // Returns nodes in a tree`
- `TreeTraverse_Skip // Skips nodes in a pending tree traversal`

#### <a name="BKMK_TreeItems_expansion"></a> TreeItems 확장
 시각화된 형식이 트리를 나타내는 경우 디버거에서는 `TreeItems` 노드를 사용하여 트리를 단계별로 진행하면서 해당 자식을 표시할 수 있습니다. 다음에 대 한 시각화를은 `std::map` 를 사용 하 여 입력을 `TreeItems` 노드:

```xml
<Type Name="std::map&lt;*&gt;">
  <DisplayString>{{size = {_Mysize}}}</DisplayString>
  <Expand>
    <Item Name="[size]">_Mysize</Item>
    <Item Name="[comp]">comp</Item>
    <TreeItems>
      <Size>_Mysize</Size>
      <HeadPointer>_Myhead->_Parent</HeadPointer>
      <LeftPointer>_Left</LeftPointer>
      <RightPointer>_Right</RightPointer>
      <ValueNode Condition="!((bool)_Isnil)">_Myval</ValueNode>
    </TreeItems>
  </Expand>
</Type>
```

구문은 비슷합니다는 `LinkedListItems` 노드. `LeftPointer`하십시오 `RightPointer`, 및 `ValueNode` 트리 노드 클래스의 컨텍스트에서 평가 됩니다. `ValueNode` 사용할지 비어 있을 수 있습니다 `this` 를 참조 하는 `TreeItems` 노드 자체.

#### <a name="BKMK_ExpandedItem_expansion"></a> ExpandedItem 확장
 `ExpandedItem` 요소 시각화 된 형식의 자식 이었던 것 처럼 기본 클래스 또는 데이터 멤버의 속성을 표시 하 여 집계 된 자식 뷰를 생성 합니다. 디버거가 지정된 된 식을 계산 하 고 결과의 자식 노드가 시각화 된 형식의 자식 목록에 추가 합니다.

예를 들어, 스마트 포인터 형식 `auto_ptr<vector<int>>` 으로 일반적으로 표시 됩니다.

 ![자동&#95;ptr&#60;벡터&#60;int&#62; &#62; 기본 확장](../debugger/media/dbg_natvis_expand_expandeditem_default.png "기본 확장")

 벡터의 값을 보려면 통과 변수 창에서 두 수준 아래로 드릴 해야는 `_Myptr` 멤버입니다. `ExpandedItem` 요소를 추가하면 계층 구조에서 `_Myptr` 변수를 제거하고 벡터 요소를 바로 확인할 수 있습니다.

```xml
<Type Name="std::auto_ptr&lt;*&gt;">
  <DisplayString>auto_ptr {*_Myptr}</DisplayString>
  <Expand>
    <ExpandedItem>_Myptr</ExpandedItem>
  </Expand>
</Type>
```

 ![자동&#95;ptr&#60;벡터&#60;int&#62; &#62; ExpandedItem 확장](../debugger/media/dbg_natvis_expand_expandeditem_visualized.png "ExpandedItem 확장")

다음 예제에서는 파생된 클래스에서 기본 클래스에서 속성을 집계 하는 방법을 보여 줍니다. `CPanel` 클래스가 `CFrameworkElement`에서 파생된다고 가정해 보겠습니다. 기본에서 제공 하는 속성을 반복 하는 대신 `CFrameworkElement` 클래스를 `ExpandedItem` 노드 시각화의 자식 목록에 해당 속성을 추가 합니다 `CPanel` 클래스입니다.

```xml
<Type Name="CPanel">
  <DisplayString>{{Name = {*(m_pstrName)}}}</DisplayString>
  <Expand>
    <Item Name="IsItemsHost">(bool)m_bItemsHost</Item>
    <ExpandedItem>*(CFrameworkElement*)this,nd</ExpandedItem>
  </Expand>
</Type>
```

이때 파생된 클래스에 대해 시각화 일치를 해제하는 **nd** 형식 지정자가 필요합니다. 이 고, 그렇지 식 `*(CFrameworkElement*)this` 없었다는 `CPanel` 가장 적합 한 시각화를 기본 시각화 형식 일치 규칙 때문에 다시 적용할 수를 고려 합니다. 사용 된 **nd** 형식 지정자를 기본 클래스에 시각화가 없습니다. 기본 클래스 시각화 또는 기본 확장을 사용 하도록 디버거에 지시 합니다.

#### <a name="BKMK_Synthetic_Item_expansion"></a> 가상 항목 확장
 `ExpandedItem` 요소는 계층 구조를 제거하여 데이터를 보다 평면적으로 표시하지만 `Synthetic` 노드는 그 반대입니다. 식의 결과 없는 인위적인 자식 요소를 만들 수 있습니다. 인공 요소 자체의 자식 요소를 포함할 수 있습니다. 다음 예의 `Concurrency::array` 형식에 대한 시각화에서는 사용자에게 진단 메시지를 표시하기 위해 `Synthetic` 노드를 사용합니다.

```xml
<Type Name="Concurrency::array&lt;*,*&gt;">
  <DisplayString>extent = {_M_extent}</DisplayString>
  <Expand>
    <Item Name="extent" Condition="_M_buffer_descriptor._M_data_ptr == 0">_M_extent</Item>
    <ArrayItems Condition="_M_buffer_descriptor._M_data_ptr != 0">
      <Rank>$T2</Rank>
      <Size>_M_extent._M_base[$i]</Size>
      <ValuePointer>($T1*) _M_buffer_descriptor._M_data_ptr</ValuePointer>
    </ArrayItems>
    <Synthetic Name="Array" Condition="_M_buffer_descriptor._M_data_ptr == 0">
      <DisplayString>Array members can be viewed only under the GPU debugger</DisplayString>
    </Synthetic>
  </Expand>
</Type>
```

 ![가상 요소 확장을 사용 하 여 Concurrency::Array](../debugger/media/dbg_natvis_expand_synthetic.png "Concurrency::Array 가상 요소 확장을 사용 하 여")

### <a name="BKMK_HResult"></a> HResult 요소
 합니다 `HResult` 요소에 대해 표시 되는 정보를 사용자 지정할 수 있습니다는 **HRESULT** 디버거 창에 있습니다. `HRValue` 요소에는 사용자 지정할 **HRESULT**의 32비트 값이 포함되어 있어야 합니다. `HRDescription` 요소 디버거 창에 표시할 정보를 포함 합니다.

```xml

<HResult Name="MY_E_COLLECTION_NOELEMENTS">
  <HRValue>0xABC0123</HRValue>
  <HRDescription>No elements in the collection.</HRDescription>
</HResult>
```

### <a name="BKMK_UIVisualizer"></a> UIVisualizer 요소
`UIVisualizer` 요소는 디버거에 그래픽 시각화 도우미 플러그 인을 등록합니다. 그래픽 시각화 도우미 대화 상자나 다른 인터페이스를 보여 주는 변수 또는 개체 방식으로 데이터 형식을 사용 하 여 일치를 만듭니다. 시각화 도우미 플러그 인으로 작성 해야 합니다는 [VSPackage](../extensibility/internals/vspackages.md), 및 디버거가 사용할 수 있는 서비스를 노출 해야 합니다. 합니다 *.natvis* 파일 이름, 노출된 된 서비스 및 시각화할 수 있는 형식의 GUID 같은 플러그 인에 대 한 등록 정보를 포함 합니다.

UIVisualizer 요소의 예는 다음과 같습니다.

```xml
<?xml version="1.0" encoding="utf-8"?>
<AutoVisualizer xmlns="http://schemas.microsoft.com/vstudio/debugger/natvis/2010">
    <UIVisualizer ServiceId="{5452AFEA-3DF6-46BB-9177-C0B08F318025}"
        Id="1" MenuName="Vector Visualizer"/>
    <UIVisualizer ServiceId="{5452AFEA-3DF6-46BB-9177-C0B08F318025}"
        Id="2" MenuName="List Visualizer"/>
.
.
</AutoVisualizer>
```

- A `ServiceId`  -  `Id` 식별 하는 특성 쌍을 `UIVisualizer`입니다. `ServiceId` 시각화 도우미 서비스의 GUID 패키지 노출 됩니다. `Id` 둘 이상의 서비스를 제공 하는 경우 시각화 도우미를 구분할 수 있는 고유 식별자가입니다. 앞의 예에서 동일한 시각화 도우미 서비스는 두 명의 시각화 도우미를 제공합니다.

- `MenuName` 특성은 디버거에 돋보기 아이콘 옆의 드롭다운 목록에 표시 하는 시각화 도우미 이름을 정의 합니다. 예를 들어:

  ![UIVisualizer 메뉴 바로 가기 메뉴](../debugger/media/dbg_natvis_vectorvisualizer.png "UIVisualizer 메뉴 바로 가기 메뉴")

에 정의 된 각 유형에 *.natvis* 파일에는 표시할 수 있는 모든 UI 시각화 도우미가 명시적으로 나열 해야 합니다. 디버거는 등록 된 시각화 도우미를 사용 하 여 형식 항목의 시각화 도우미 참조를 찾습니다. 다음 항목을 입력 하는 예를 들어 `std::vector` 참조는 `UIVisualizer` 앞의 예제에서입니다.

```xml
<Type Name="std::vector&lt;int,*&gt;">
  <UIVisualizer ServiceId="{5452AFEA-3DF6-46BB-9177-C0B08F318025}" Id="1" />
</Type>
```

 예를 볼 수는 `UIVisualizer` 에 [이미지 조사식](https://marketplace.visualstudio.com/items?itemName=VisualCPPTeam.ImageWatch2017) 메모리 내 비트맵을 확인 하는 데 사용 되는 확장 합니다.

### <a name="BKMK_CustomVisualizer"></a>CustomVisualizer 요소
 `CustomVisualizer` Visual Studio code에서 시각화를 제어 하기 위해 작성할 수 있는 VSIX 확장을 지정 하는 확장성 지점이입니다. VSIX 확장명 작성 하는 방법에 대 한 자세한 내용은 참조는 [Visual Studio SDK](../extensibility/visual-studio-sdk.md)합니다.

XML Natvis 정의 보다 사용자 지정 시각화 도우미를 작성 하기 위해 많은 작업이 있지만 Natvis는 또는 지원 하지 않습니다 하는 방법에 대 한 제약 조건에서 자유롭게입니다. 사용자 지정 시각화 도우미는 디버거 확장성 Api 쿼리 및 디버기 프로세스를 수정 하거나 Visual Studio의 다른 부분과 통신 수의 전체 집합에 대 한 액세스.

 사용할 수는 `Condition`, `IncludeView`, 및 `ExcludeView` 특성을 `CustomVisualizer` 요소입니다.