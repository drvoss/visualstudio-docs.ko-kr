---
title: Directed Graph Markup Language (DGML) reference | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
ms.assetid: cc3e4ae7-60fa-4e22-9227-98020b480b73
caps.latest.revision: 10
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 16a51c7fc05d51b551884f70dc514e8939962818
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74296032"
---
# <a name="directed-graph-markup-language-dgml-reference"></a>DGML(Directed Graph Markup Language) 참조
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

DGML(Directed Graph Markup Language)은 시각화에 사용되고 복잡성 분석을 수행하는 데 사용되는 정보를 설명하며, Visual Studio에서 코드 맵을 지속하는 데 사용되는 형식입니다. 단순 XML을 사용하여 순환 및 비순환 방향이 지정된 그래프를 설명합니다. 방향이 지정된 그래프는 링크 또는 가장자리로 연결되는 노드의 집합입니다. 노드 및 링크를 사용하여 소프트웨어 프로젝트의 요소와 같은 네트워크 구조를 나타낼 수 있습니다.

 Note that some versions of Visual Studio support only a subset of DGML capabilities, see [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

> [!NOTE]
> .dgml 파일을 편집하는 경우 IntelliSense를 사용하면 각 요소 및 요소 값에 사용할 수 있는 특성을 식별할 수 있습니다. 특성에 색을 지정하려면 "Blue"와 같은 일반적인 색의 이름 또는 "#ffa0b1c3"과 같은 ARGB 16진수 값을 사용합니다. DGML은 WPF(Windows Presentation Foundation) 색 정의 형식의 일부를 사용합니다. For more information, see [Colors Class](https://go.microsoft.com/fwlink/?LinkId=182345).

## <a name="DGML"></a> DGML syntax
 다음 표에서는 DGML에서 사용되는 요소 종류에 대해 설명합니다.

- `<DirectedGraph></DirectedGraph>`

   이 요소는 코드 맵(.dgml) 문서의 루트 요소입니다. 다른 모든 DGML 요소는 이 요소의 범위 내에 나타납니다.

   다음 목록에서는 포함할 수 있는 선택적 특성에 대해 설명합니다.

   `Background` - 맵 배경의 색입니다.

   `BackgroundImage` - 맵 배경으로 사용할 이미지 파일의 위치입니다.

   `GraphDirection` - 맵이 트리 레이아웃(`Sugiyama`)으로 설정되면 대부분의 링크가 지정된 방향, 즉 `TopToBottom`, `BottomToTop`, `LeftToRight` 또는 `RightToLeft`로 흐르도록 노드를 정렬합니다. See [Change the map layout](../modeling/browse-and-rearrange-code-maps.md#Selecting).

   `Layout` - 맵을 `None`, `Sugiyama`(트리 레이아웃), `ForceDirected`(빠른 클러스터) 또는 `DependencyMatrix` 레이아웃으로 설정합니다. See [Change the map layout](../modeling/browse-and-rearrange-code-maps.md#Selecting).

   `NeighborhoodDistance` - 맵이 트리 레이아웃 또는 빠른 클러스터 레이아웃으로 설정되면 선택한 노드에서 지정된 링크 수(1-7)만큼 떨어진 노드만 표시합니다. See [Change the map layout](../modeling/browse-and-rearrange-code-maps.md#Selecting).

   예제:

  ```xml
  <?xml version="1.0" encoding="utf-8"?>
  <DirectedGraph Title="DrivingTest" Background="Blue" xmlns="http://schemas.microsoft.com/vs/2009/dgml">
     <Nodes>
        ...
     </Nodes>
     <Links>
        ...
     </Links>
     <Categories>
        ...
     </Categories>
     <Properties>
        ...
     </Properties>
  </DirectedGraph>
  ```

- `<Nodes></Nodes>`

   이 요소는 맵의 노드를 정의하는 `<Node/>` 요소 목록을 포함하는 선택적 요소입니다. 자세한 내용은 `<Node/>` 요소를 참조하십시오.

  > [!NOTE]
  > `<Link/>` 요소에서 정의되지 않은 노드를 참조하는 경우 맵에서 `<Node/>` 요소를 자동으로 만듭니다.

   예제:

  ```xml
  <?xml version="1.0" encoding="utf-8"?>
  <DirectedGraph Title="DrivingTest" xmlns="http://schemas.microsoft.com/vs/2009/dgml">
     <Nodes>
        <Node ... />
     </Nodes>
     <Links>
        <Link ... />
     </Links>
  </DirectedGraph>
  ```

- `<Node/>`

   이 요소는 단일 노드를 정의합니다. 또한 `<Nodes><Nodes/>` 요소 목록 내에 나타납니다.

   이 요소에는 다음과 같은 특성이 포함되어야 합니다.

   `Id` - `Label` 특성이 별도로 지정되지 않은 경우 `Label` 특성의 기본값 및 노드의 고유 이름입니다. 이 이름은 노드를 참조하는 링크의 `Source` 또는 `Target` 특성과 일치해야 합니다.

   다음 목록에서는 포함할 수 있는 선택적 특성 중 일부에 대해 설명합니다.

   `Label` - The display name of the node.

   스타일 특성. [Customize code maps by editing the DGML files](../modeling/customize-code-maps-by-editing-the-dgml-files.md)을 참조하세요.

   `Category` - 이 특성을 공유하는 요소를 식별하는 범주의 이름입니다. 자세한 내용은 `<Category/>` 요소를 참조하십시오.

   `Property` - 속성 값이 같은 요소를 식별하는 속성의 이름입니다. 자세한 내용은 `<Property/>` 요소를 참조하십시오.

   `Group` - 노드에 다른 노드가 포함된 경우 이 특성을 `Expanded` 또는 `Collapsed`로 설정하여 노드의 내용을 표시하거나 숨길 수 있습니다. `<Link/>` 특성을 포함하고, 부모 노드와 자식 노드를 각각 소스 노드와 대상 노드로 지정하는 `Category="Contains"` 요소가 있어야 합니다. See [Group code elements](../modeling/customize-code-maps-by-editing-the-dgml-files.md#OrganizeNodes).

   `Visibility` - 이 특성을 `Visible`, `Hidden` 또는 `Collapsed`로 설정합니다. `System.Windows.Visibility`를 사용합니다. See [Hide or show nodes and links](../modeling/browse-and-rearrange-code-maps.md#HidingShowing).

   `Reference` - 이 특성을 문서 또는 URL에 대한 링크로 설정합니다. See [Link documents or URLs to code elements and links](../modeling/customize-code-maps-by-editing-the-dgml-files.md#AddReferences).

   예제:

  ```xml
  <?xml version="1.0" encoding="utf-8"?>
  <DirectedGraph Title="DrivingTest" xmlns="http://schemas.microsoft.com/vs/2009/dgml">
     <Nodes>
        <Node Id="Driver" Label="Student" Category="Person" />
        <Node Id="Passenger" Label="Instructor" Category="Person" />
        <Node Id="Car" Label="Car" Category="Automobile" />
        <Node Id="Truck" Label="Truck" Category="Automobile" />
     </Nodes>
     <Links>
        <Link ... />
     </Links>
     <Categories>
        <Category Id="Person" Background="Orange" />
        <Category Id="Automobile" Background="Yellow"/>
     </Categories>
  </DirectedGraph>
  ```

- `<Links></Links>`

   이 요소에는 노드 간의 링크를 정의하는 `<Link>` 요소 목록이 포함됩니다. 자세한 내용은 `<Link/>` 요소를 참조하십시오.

   예제:

  ```xml
  <?xml version="1.0" encoding="utf-8"?>
  <DirectedGraph Title="DrivingTest" xmlns="http://schemas.microsoft.com/vs/2009/dgml">
     <Links>
        <Link ... />
     </Links>
  </DirectedGraph>
  ```

- `<Link/>`

   이 요소는 소스 노드를 대상 노드에 연결하는 단일 링크를 정의합니다. 또한 `<Links></Links>` 요소 목록 내에 나타납니다.

  > [!NOTE]
  > 이 요소가 정의되지 않은 노드를 참조하는 경우 맵 문서에서는 지정된 특성을 포함하는 노드를 자동으로 만듭니다.

   이 요소에는 다음과 같은 특성이 포함되어야 합니다.

   `Source` - 링크의 소스 노드입니다.

   `Target` - 링크의 대상 노드입니다.

   다음 목록에서는 포함할 수 있는 선택적 특성 중 일부에 대해 설명합니다.

   `Label` - 링크의 표시 이름입니다.

   스타일 특성. [Customize code maps by editing the DGML files](../modeling/customize-code-maps-by-editing-the-dgml-files.md)을 참조하세요.

   `Category` - 이 특성을 공유하는 요소를 식별하는 범주의 이름입니다. 자세한 내용은 `<Category/>` 요소를 참조하십시오.

   `Property` - 속성 값이 같은 요소를 식별하는 속성의 이름입니다. 자세한 내용은 `<Property/>` 요소를 참조하십시오.

   예제:

  ```xml
  <?xml version="1.0" encoding="utf-8"?>
  <DirectedGraph Title="DrivingTest" xmlns="http://schemas.microsoft.com/vs/2009/dgml">
     <Nodes>
        <Node Id="Driver" Label="Student" Category="Person" />
        <Node Id="Passenger" Label="Instructor" Category="Person" />
        <Node Id="Car" Label="Car" Category="Automobile" />
        <Node Id="Truck" Label="Truck" Category="Automobile" />
     </Nodes>
     <Links>
        <Category Id="Person" Background="Orange" />
        <Category Id="Automobile" Background="Yellow"/>
        <Link Source="Driver" Target="Car" Label="Passed" Stroke="Black" Background="Green" Category="PassedTest" />
        <Link Source="Driver" Target="Truck" Label="Failed" Stroke="Black" Background="Red" Category="PassedTest" />
     </Links>
  </DirectedGraph>
  ```

- `<Categories></Categories>`

   이 요소에는 `<Category/>` 요소 목록이 포함됩니다. 자세한 내용은 `<Category/>` 요소를 참조하십시오.

   예제:

  ```xml
  <?xml version="1.0" encoding="utf-8"?>
  <DirectedGraph Title="DrivingTest" xmlns="http://schemas.microsoft.com/vs/2009/dgml">
     <Categories>
         <Category ... />
     </Categories>
  </DirectedGraph>
  ```

- `<Category/>`

   이 요소는 이 특성을 공유하는 요소를 식별하는 데 사용되는 `Category` 특성을 정의합니다. `Category` 특성을 사용하면 맵 요소를 구성하고, 공유된 특성을 상속을 통해 제공하거나 추가 메타데이터를 정의할 수 있습니다.

   이 요소에는 다음과 같은 특성이 포함되어야 합니다.

   `Id` - `Label` 특성이 별도로 지정되지 않은 경우 `Label` 특성의 기본값 및 범주의 고유 이름입니다.

   다음 목록에서는 포함할 수 있는 선택적 특성 중 일부에 대해 설명합니다.

   `Label` - 읽기 쉬운 형식의 범주 이름입니다.

   `BasedOn` - 현재 요소의 `<Category/>`가 상속되는 부모 범주입니다.

   이 요소의 예제에서 `FailedTest` 범주는 `Stroke` 범주에서 `PassedTest` 특성을 상속합니다. See "To create hierarchical categories" in [Customize code maps by editing the DGML files](../modeling/customize-code-maps-by-editing-the-dgml-files.md).

   또한 범주는 노드 및 링크가 맵에 표시되는 모양을 제어하는 몇 가지 기본적인 템플릿 동작을 제공합니다. [Customize code maps by editing the DGML files](../modeling/customize-code-maps-by-editing-the-dgml-files.md)을 참조하세요.

   예제:

  ```xml
  <?xml version="1.0" encoding="utf-8"?>
  <DirectedGraph Title="DrivingTest" xmlns="http://schemas.microsoft.com/vs/2009/dgml">
     <Nodes>
        <Node Id="Driver" Label="Driver" Category="Person" />
        <Node Id="Car" Label="Car" Category="Automobile" />
        <Node Id="Truck" Label="Truck" Category="Automobile" />
        <Node Id="Passenger" Category="Person" />
     </Nodes>
     <Links>
        <Link Source="Driver" Target="Car" Label="Passed" Category="PassedTest" />
        <Link Source="Driver" Target="Truck" Label="Failed" Category="FailedTest" />
     </Links>
     <Categories>
        <Category Id="Person" Background="Orange" />
        <Category Id="Automobile" Background="Yellow"/>
        <Category Id="PassedTest" Label="Passed" Stroke="Black" Background="Green" />
        <Category Id="FailedTest" Label="Failed" BasedOn="PassedTest" Background="Red" />
     </Categories>
  </DirectedGraph>
  ```

- `<Properties></Properties>`

   이 요소에는 `<Property/>` 요소 목록이 포함됩니다. 자세한 내용은 `<Property/>` 요소를 참조하십시오.

   예제:

  ```xml
  <?xml version="1.0" encoding="utf-8"?>
  <DirectedGraph Title="DrivingTest" xmlns="http://schemas.microsoft.com/vs/2009/dgml">
     <Properties>
         <Property ... />
     </Properties>
  </DirectedGraph>
  ```

- `<Property/>`

   이 요소는 범주 및 기타 속성을 포함하여 DGML 요소 또는 특성에 값을 할당할 때 사용할 수 있는 `Property` 특성을 정의합니다.

   이 요소에는 다음과 같은 특성이 포함되어야 합니다.

  - `Id` - `Label` 특성이 별도로 지정되지 않은 경우 `Label` 특성의 기본값 및 속성의 고유 이름입니다.

  - `DataType` - 속성에 의해 저장되는 데이터의 형식입니다.

    If you want the property to appear in the **Properties** window, use the `Label` property to specify the property's display name.

    See [Assign categories to code elements and links](../modeling/customize-code-maps-by-editing-the-dgml-files.md#AssignCategories).

    예제:

  ```xml
  <?xml version="1.0" encoding="utf-8"?>
  <DirectedGraph Title="DrivingTest" xmlns="http://schemas.microsoft.com/vs/2009/dgml">
     <Nodes>
        <Node Id="Driver" Label="Driver" Category="Person" DrivingAge="18"/>
        <Node Id="Car" Label="Car" Category="Automobile" />
        <Node Id="Truck" Label="Truck" Category="Automobile" />
        <Node Id="Passenger" Category="Person" />
     </Nodes>
     <Links>
        <Link Source="Driver" Target="Car" Label="Passed" Category="PassedTest" />
        <Link Source="Driver" Target="Truck" Label="Failed" Category="FailedTest" />
     </Links>
     <Categories>
        <Category Id="Person" Background="Orange" />
        <Category Id="Automobile" Background="Yellow"/>
        <Category Id="PassedTest" Label="Passed" Stroke="Black" Background="Green" />
        <Category Id="FailedTest" Label="Failed" BasedOn="PassedTest" Background="Red" />
     </Categories>
     <Properties>
         <Property Id="DrivingAge" Label="Driving Age" DataType="System.Int32" />
     </Properties>
  </DirectedGraph>
  ```

### <a name="AddAlias"></a> Aliases for commonly-used paths
 일반적으로 사용되는 경로를 별칭으로 바꾸면 .dgml 파일의 크기뿐만 아니라 파일을 로드하거나 저장하는 데 필요한 시간을 줄일 수 있습니다. 별칭을 만들려면 .dgml 파일의 끝에 `<Paths></Paths>` 섹션을 추가합니다. 다음과 같이 이 섹션에서 `<Path/>` 요소를 추가하여 경로의 별칭을 정의합니다.

```xml
<Paths>
   <Path Id="MyPathAlias" Value="C:\...\..." />
</Paths>
```

 To reference the alias from an element in the .dgml file, enclose the `Id` of the \<Path/> element with a dollar sign ($) and parentheses (()):

```xml
<Nodes>
   <Node Id="MyNode" Reference="$(MyPathAlias)MyDocument.txt" />
</Nodes>
<Properties>
   <Property Id="Reference" Label="My Document" DataType="System.String" IsReference="True" />
</Properties>
```

## <a name="see-also"></a>관련 항목:
 [Map dependencies across your solutions](../modeling/map-dependencies-across-your-solutions.md) [Use code maps to debug your applications](../modeling/use-code-maps-to-debug-your-applications.md) [Find potential problems using code map analyzers](../modeling/find-potential-problems-using-code-map-analyzers.md)
