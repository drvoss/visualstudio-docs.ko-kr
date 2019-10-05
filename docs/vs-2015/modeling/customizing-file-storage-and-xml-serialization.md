---
title: 파일 저장소 및 XML Serialization을 사용자 지정 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
f1_keywords:
- vs.dsltools.dsldesigner.xmlbehavior
helpviewer_keywords:
- Domain-Specific Language, serialization
ms.assetid: 76c53ef1-e3b9-45da-b425-1bddb3c01395
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: b41f5f6a3d937f23db1039fdab5e1cf7e36960ef
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63433261"
---
# <a name="customizing-file-storage-and-xml-serialization"></a>파일 스토리지 및 XML Serialization 사용자 지정
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

사용자 인스턴스를 저장 하는 경우 또는 *모델*, 도메인 특정 언어 (DSL)의 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], XML 파일로 만들어지거나 업데이트 됨. 파일은 저장소에 모델을 다시 다시 로드 될 수 있습니다.  
  
 아래에서 설정을 조정 하 여 serialization 체계를 사용자 지정할 수 있습니다 **Xml 직렬화 동작** DSL 탐색기에서. 아래에 있는 노드가 **Xml 직렬화 동작** 모든 도메인 클래스, 속성 및 관계에 대 한 합니다. 관계의 원본 클래스 아래에 있습니다. 셰이프, 커넥터 및 다이어그램 클래스에 해당 하는 노드가 있습니다.  
  
 또한 고급 사용자 지정에 대 한 프로그램 코드를 작성할 수 있습니다.  
  
> [!NOTE]
> 특정 형식으로 모델을 저장 하려면 해당 형식에서 다시 로드 해야 하지만 경우에 텍스트 템플릿을 사용 하 여 사용자 지정 serialization 체계 대신이 모델에서 출력을 생성 하는 것이 좋습니다. 자세한 내용은 [도메인별 언어에서 코드 생성](../modeling/generating-code-from-a-domain-specific-language.md)합니다.  
  
## <a name="model-and-diagram-files"></a>모델 및 다이어그램 파일  
 각 모델은 일반적으로 두 개의 파일에 저장 됩니다.  
  
- 모델 파일의 이름이 같은 **Model1.mydsl**합니다. 모델 요소 및 관계와 해당 속성을 저장합니다. 와 같은 파일 확장명 **.mydsl** 에 의해 결정 됩니다 합니다 **FileExtension** 속성을 **편집기** DSL 정의에서 노드.  
  
- 다이어그램 파일의 이름이 같은 **Model1.mydsl.diagram**합니다. 셰이프, 커넥터 및 해당 위치, 색, 선 두께 및 기타 세부 정보는 다이어그램의 모양을 저장합니다. 사용자를 삭제 하는 경우는 **.diagram** 파일인 모델에는 중요 한 정보는 손실 되지 않습니다. 다이어그램의 레이아웃만 손실 됩니다. 모델 파일을 열면 모양의 기본 설정 및 커넥터 생성 됩니다.  
  
#### <a name="to-change-the-file-extension-of-a-dsl"></a>DSL의 파일 확장명을 변경 하려면  
  
1. DSL 정을 엽니다. DSL 탐색기에서 편집기 노드를 클릭 합니다.  
  
2. 속성 창에서 편집 합니다 **FileExtension** 속성입니다. 초기 포함 되지 않습니다 "." 파일 이름 확장명입니다.  
  
3. 솔루션 탐색기에서 두 항목 템플릿 파일의 이름을 변경 **DslPackage\ProjectItemTemplates**합니다. 이러한 파일에 다음과 같은이 형식 이름이:  
  
     `myDsl.diagram`  
  
     `myDsl.myDsl`  
  
## <a name="the-default-serialization-scheme"></a>기본 Serialization 체계  
 이 항목에 대 한 예제를 만들려면 다음 DSL 정의 사용 했습니다.  
  
 ![DSL 정의 다이어그램 &#45; 패밀리 트리 모델](../modeling/media/familyt-person.png "FamilyT_Person")  
  
 이 DSL 모양이 되 면 다음 화면에는 모델을 만드는 데 사용 된 합니다.  
  
 ![패밀리 트리 다이어그램, 도구 상자 및 탐색기](../modeling/media/familyt-instance.png "FamilyT_Instance")  
  
 이 모델을 저장 하 고 다시 XML 텍스트 편집기에서 열립니다.  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<familyTreeModel xmlns:dm0="http://schemas.microsoft.com/VisualStudio/2008/DslTools/Core" dslVersion="1.0.0.0" Id="f817b728-e920-458e-bb99-98edc469d78f" xmlns="http://schemas.microsoft.com/dsltools/FamilyTree">  
  <people>  
    <person name="Henry VIII" birthYear="1491" deathYear="1547" age="519">  
      <children>  
        <personMoniker name="/f817b728-e920-458e-bb99-98edc469d78f/Elizabeth I" />  
        <personMoniker name="/f817b728-e920-458e-bb99-98edc469d78f/Mary" />  
      </children>  
    </person>  
    <person name="Elizabeth I" birthYear="1533" deathYear="1603" age="477" />  
    <person name="Mary" birthYear="1515" deathYear="1558" age="495" />  
  </people>  
</familyTreeModel>  
  
```  
  
 직렬화 된 모델에 대 한 다음 사항에 유의 합니다.  
  
- 각 XML 노드 이름이 도메인 클래스 이름으로 동일한 첫 글자는 소문자입니다. 예를 들어 `familyTreeModel` 및 `person`를 지정합니다.  
  
- 도메인 속성 이름과 생 년 등 XML 노드에 특성으로 serialize 됩니다. 마찬가지로 속성 이름의 초기 문자를 소문자로 변환 됩니다.  
  
- 각 관계는 관계의 원본 끝을 내부에 중첩 된 XML 노드로 serialize 됩니다. 노드 이름이 같은 소문자 초기 문자를 사용 하 여 원본 역할 속성으로.  
  
     역할 이라고 하는 DSL 정의에서 예를 들어 **사람들** 소스로 합니다 **FamilyTree** 클래스.  Xml에서 명명 된 노드에 의해 표시 됩니다 `people` 안에 중첩 된 `familyTreeModel` 노드.  
  
- 각 포함 관계의 대상 끝 관계 아래에 중첩 노드로 serialize 됩니다. 예를 들어 합니다 `people` 여러 노드에 포함 `person` 노드.  
  
- 각 참조 관계의 대상 끝으로 serialize 되는 *모니커*, 대상 요소에 대 한 참조를 인코딩하는 합니다.  
  
     예를 들어 아래는 `person` 노드를 있을 수 있습니다는 `children` 관계입니다. 이 노드에 같은 모니커를 포함 합니다.  
  
    ```  
    <personMoniker name="/f817b728-e920-458e-bb99-98edc469d78f/Elizabeth I" />  
    ```  
  
## <a name="understanding-monikers"></a>이해 모니커  
 모니커는 모델 및 다이어그램 파일의 다른 부분 간의 상호 참조를 나타내는 데 사용 됩니다. 에 사용 되는 `.diagram` 모델 파일에 있는 노드를 가리키도록 파일. 두 가지 방법으로 모니커:  
  
- *Id 모니커* 대상 요소의 GUID를 인용 합니다. 예를 들어:  
  
  ```  
  <personShapeMoniker Id="f79734c0-3da1-4d72-9514-848fa9e75157" />  
  
  ```  
  
- *키 모니커 정규화* 모니커 키 라는 지정 된 도메인 속성의 값에 따라 대상 요소를 식별 합니다. 대상 요소의 모니커는 모니커가 포함 관계 트리의 부모 요소의 접두사로 추가 됩니다.  
  
   다음 예제는 DSL 있습니다은 명명 된 Song 클래스는 도메인 관계에 포함 된 같이 Album 이라는 도메인 클래스에서 수행 됩니다.  
  
  ```  
  <albumMoniker title="/My Favorites/Jazz after Teatime" />  
  <songMoniker title="/My Favorites/Jazz after Teatime/Hot tea" />  
  
  ```  
  
   대상 클래스는 도메인에 대 한 속성이 있는 경우 정규화 된 키 모니커를 사용할지 옵션 **모니커 키가** 로 설정 된 `true` 에서 **Xml 직렬화 동작**합니다. 예제에서는이 옵션은 도메인 클래스 "앨범" 및 "Song"에서 "Title" 이라는 도메인 속성에 대 한 설정 됩니다.  
  
  정규화 된 키 모니커는 ID 모니커 보다 읽기 쉬울입니다. 사용자가 읽을 수 있도록 모델 파일의 XML을 하려는 경우에 정규화 된 키 모니커를 사용 하 여 하는 것이 좋습니다. 그러나 동일한 모니커 키가 둘 이상의 요소를 설정 하는 사용자에 대 한 가능한 것입니다. 중복 키 파일이 올바르게 다시 로드 하지 발생할 수 있습니다. 따라서 정규화 된 키 모니커를 사용 하 여 참조 되는 도메인 클래스를 정의 하는 경우 중복 된 모니커를 가진 파일을 저장 하는 중에서 사용자를 방지 하는 방법으로 고려해 야 합니다.  
  
#### <a name="to-set-a-domain-class-to-be-referenced-by-id-monikers"></a>도메인 클래스 ID 모니커를 참조할 수를 설정 하려면  
  
1. 했는지 **모니커 키가** 는 `false` 클래스와 기준 클래스의 모든 도메인 속성에 대 한 합니다.  
  
    1. DSL 탐색기에서 확장 **Xml Serialization Behavior\Class 데이터\\** _\<도메인 클래스 >_ **\Element 데이터**입니다.  
  
    2. 확인 **모니커 키가** 는 `false` 모든 도메인 속성에 대 한 합니다.  
  
    3. 도메인 클래스는 기본 클래스에 해당 클래스의 절차를 반복 합니다.  
  
2. 설정할 **Id Serialize**  =  `true` 도메인 클래스에 대 한 합니다.  
  
     이 속성에서 찾을 수 있습니다 **Xml 직렬화 동작**합니다.  
  
#### <a name="to-set-a-domain-class-to-be-referenced-by-qualified-key-monikers"></a>정규화 된 모니커 키에서 참조 하는 도메인 클래스를 설정 하려면  
  
- 설정할 **모니커 키가** 기존 도메인 클래스의 도메인 속성에 대 한 합니다. 속성의 형식 이어야 합니다 `string`합니다.  
  
    1. DSL 탐색기에서 확장 **Xml Serialization Behavior\Class 데이터\\** _\<도메인 클래스 >_ **\Element 데이터**를 선택한 후는 도메인 속성입니다.  
  
    2. 속성 창에서 설정할 **모니커 키가** 에 `true`입니다.  
  
- \- 또는 -  
  
     사용 하 여 새 도메인 클래스는 **명명 된 도메인 클래스** 도구입니다.  
  
     이 도구는 Name 이라는 도메인 속성이 포함 된 새 클래스를 만듭니다. 합니다 **Is Element Name** 하 고 **모니커 키가** 이 도메인 속성의 속성으로 초기화 됩니다 `true`합니다.  
  
- \- 또는 -  
  
     도메인 클래스에서 모니커 키 속성이 포함 된 다른 클래스에 상속 관계를 만듭니다.  
  
### <a name="avoiding-duplicate-monikers"></a>중복 된 모니커를 방지합니다.  
 정규화 된 키 모니커를 사용 하는 경우 가능 사용자 모델의 두 요소간 키 속성에 동일한 값을 가질 수는 있습니다. 예를 들어 DSL 사용자 이름 속성이 있는 클래스에 있으면 사용자 동일 하도록 두 요소의 이름을 설정 수 없습니다. 모델 수 있지만 파일에 저장 하는 다시 로드 하지 정확 합니다.  
  
 이 상황을 방지 하는 데 도움이 되는 방법은 여러 가지가 있습니다.  
  
- 설정할 **Is Element Name**  =  `true` 키 도메인 속성에 대 한 합니다. DSL 정의 다이어그램에서 도메인 속성을 선택 하 고 속성 창에서 값을 설정 합니다.  
  
     사용자 클래스의 새 인스턴스를 만들 때이 값을 사용 하면 도메인 속성을 다른 값을 자동으로 할당 합니다. 기본 동작을 클래스 이름 끝에 숫자를 추가합니다. 사용자는 중복 된 이름을 변경 하지 못하게 되지는 않습니다 하지만 도움이 됩니다 경우에서 사용자 모델을 저장 하기 전에 값을 설정 하지 않습니다.  
  
- DSL에 대 한 유효성 검사를 사용 하도록 설정 합니다. DSL 탐색기에서 Editor\Validation를 선택 하 고 설정 된 **사용 하는 중...**  속성을 `true`입니다.  
  
     모호성에 대 한 확인 하는 자동으로 생성 된 유효성 검사 메서드를 있습니다. 이 메서드를는 `Load` 유효성 검사 범주입니다. 이렇게 하면는 사용자 경고가 표시 됩니다 다시 파일을 열 수도 없습니다.  
  
     자세한 내용은 [도메인별 언어에서 유효성 검사](../modeling/validation-in-a-domain-specific-language.md)합니다.  
  
### <a name="moniker-paths-and-qualifiers"></a>모니커 경로 및 한정자  
 정규화 된 키 모니커 모니커 키를 사용 하 여 끝내 고 포함 트리의 부모 모니커 접두사로 추가 됩니다. 예를 들어 앨범의 모니커 이면:  
  
```  
<albumMoniker title="/My Favorites/Jazz after Teatime" />  
  
```  
  
 그런 다음 해당 앨범의 곡을 중 수 있습니다.  
  
```  
<songMoniker title="/My Favorites/Jazz after Teatime/Hot tea" />  
```  
  
 그러나 앨범 대신 ID로 참조 되는 경우 다음 모니커는 다음과 같을 수: 있습니다  
  
```  
<albumMoniker Id="77472c3a-9bf9-4085-976a-d97a4745237c" />  
<songMoniker title="/77472c3a-9bf9-4085-976a-d97a4745237c/Hot tea" />  
```  
  
 GUID가 고유 하므로 되지 앞에 옵니다 부모의 모니커에서 지 확인 합니다.  
  
 모델 내에서 고유한 값을는 특정 도메인 속성은 항상 알고 있는 경우 설정할 수 있습니다 **는 모니커 한정자** 에 `true` 해당 속성에 대 한 합니다. 이렇게 하면 부모의 모니커를 사용 하지 않고 한정자로 사용할 수 있도록 합니다. 예를 들어, 모두 설정 하면 **는 모니커 한정자** 하 고 **모니커 키가** 앨범 클래스의 Title 도메인 속성에 대 한 모델의 이름 또는 식별자에 사용 되지 않습니다 모니커의 Album 및 해당 포함 자식:  
  
```  
<albumMoniker name="Jazz after Teatime" />  
<songMoniker title="/Jazz after Teatime/Hot tea" />  
  
```  
  
## <a name="customizing-the-structure-of-the-xml"></a>XML의 구조를 사용자 지정  
 다음 사용자 지정을 하려면 확장 합니다 **Xml 직렬화 동작** DSL 탐색기에서 노드. 도메인 클래스에서 속성 및이 클래스에서 제공 되는 관계의 목록을 보려면 요소 데이터 노드를 확장 합니다. 관계를 선택 하 고 속성 창에서 해당 옵션을 조정 합니다.  
  
- 설정할 **생략 요소** 대상 요소의 목록만 종료 소스 역할 노드를 생략 하려면 true입니다. 원본 및 대상 클래스 간에 둘 이상의 관계가 있으면이 옵션을 설정 하지 않아야 합니다.  
  
    ```  
  
    <familyTreeModel ...>  
      <!-- The following node is omitted by using Omit Element: -->  
      <!-- <people> -->  
        <person name="Henry VIII" .../>  
        <person name="Elizabeth I" .../>  
      <!-- </people> -->  
    </familyTreeModel>  
  
    ```  
  
- 설정 **사용 하 여 전체 폼** 관계 인스턴스를 나타내는 노드에서 대상 노드를 포함 합니다. 이 옵션은 도메인 관계에 도메인 속성을 추가할 때 자동으로 설정 됩니다.  
  
    ```  
  
    <familyTreeModel ...>  
      <people>  
        <!-- The following node is inserted by using Use Full Form: -->  
        <familyTreeModelHasPeople myRelationshipProperty="x1">  
          <person name="Henry VIII" .../>  
        </familyTreeModelHasPeople>  
        <familyTreeModelHasPeople myRelationshipProperty="x2">  
          <person name="Elizabeth I" .../>  
        </familyTreeModelHasPeople>  
      </people>  
    </familyTreeModel>  
  
    ```  
  
- 설정할 **표현을** = **요소** 특성 값으로 대신 요소로 저장 됩니다 도메인 속성이 있어야 합니다.  
  
    ```  
    <person name="Elizabeth I" birthYear="1533">  
      <deathYear>1603</deathYear>  
    </person>  
    ```  
  
- 특성 및 관계 serialize 되는 순서를 변경 하려면 요소 데이터에서 항목을 마우스 오른쪽 단추로 클릭 하 고 사용 합니다 **위로 이동** 또는 **아래로 이동** 메뉴 명령입니다.  
  
## <a name="major-customization-using-program-code"></a>프로그램 코드를 사용 하 여 주요 사용자 지정  
 Serialization 알고리즘의 일부 또는 전체를 대체할 수 있습니다.  
  
 코드를 연구 하는 것이 좋습니다 **Dsl\Generated Code\Serializer.cs** 하 고 **SerializationHelper.cs**합니다.  
  
#### <a name="to-customize-the-serialization-of-a-particular-class"></a>특정 클래스의 serialization을 사용자 지정 하려면  
  
1. 설정 **Is Custom** 아래에서 해당 클래스 노드에 **Xml 직렬화 동작**합니다.  
  
2. 모든 템플릿 변환 하 고 솔루션을 빌드하고 결과 컴파일 오류를 조사 합니다. 각 오류 근처 주석을 제공 해야 하는 코드를 설명 합니다.  
  
#### <a name="to-provide-your-own-serialization-for-the-whole-model"></a>전체 모델에 대 한 고유한 직렬화를 제공 합니다.  
  
1. Dsl\GeneratedCode\SerializationHelper.cs에서 메서드를 재정의  
  
## <a name="options-in-xml-serialization-behavior"></a>Xml Serialization 동작 옵션  
 DSL 탐색기의 Xml 직렬화 동작 노드는 각 도메인 클래스, 관계, 모양, 연결선 및 다이어그램 클래스에 대 한 자식 노드를 포함합니다. 각 노드 아래에 있는 속성 및 해당 요소에서 발생 해야 하는 관계의 목록이입니다. 관계는 독자적인와 해당 소스 클래스 아래에 표시 됩니다.  
  
 다음 표에서 DSL 정의의이 섹션에서는 설정할 수 있는 옵션을 보여 줍니다. 각 경우에서는 DSL 탐색기에서 요소를 선택 하 고 속성 창에서 옵션을 설정 합니다.  
  
### <a name="xml-class-data"></a>Xml 클래스 데이터  
 DSL 탐색기에서 발견 된 이러한 요소가 **Xml Serialization Behavior\Class 데이터**입니다.  
  
|||  
|-|-|  
|속성|설명|  
|사용자 지정 요소 스키마가|True 이면 도메인 클래스에 사용자 지정 요소 스키마|  
|이 사용자 지정|이 값을 설정 **True** 이 도메인 클래스에 대 한 고유한 serialization 및 deserialization 코드를 작성 하려는 경우.<br /><br /> 솔루션을 구축 하 고 자세한 지침을 검색 하려면 오류를 조사 합니다.|  
|도메인 클래스|이 클래스의 데이터 노드에 적용 되는 도메인 클래스입니다. 읽기 전용입니다.|  
|요소 이름|이 클래스의 요소에 대 한 Xml 노드 이름입니다. 기본값은 도메인 클래스 이름의 소문자 버전입니다.|  
|모니커 특성 이름|참조를 포함 하도록 모니커 요소에서 사용 된 특성의 이름입니다. 공백인 경우 키 속성의 id 이름을 사용 됩니다.<br /><br /> 이 예에서는 "name":  `<personMoniker name="/Mike Nash"/>`|  
|모니커 요소 이름|이 클래스의 요소를 참조 하는 모니커에 사용 되는 xml 요소의 이름입니다.<br /><br /> 기본값은 "Moniker" 붙음 클래스 이름의 소문자 버전입니다. 예를 들어, `personMoniker`을 입력합니다.|  
|모니커 형식 이름|이 클래스의 요소 모니커에 대해 생성 된 xsd 형식의 이름입니다. 에 XSD **Dsl\Generated 코드\\\*Schema.xsd**|  
|Id를 직렬화 합니다.|True 이면 요소 GUID를 파일에 포함 됩니다. 표시 된 속성이 없는 경우에 true 여야 합니다 **모니커 키가** DSL이이 클래스에 참조 관계를 정의 합니다.|  
|형식 이름|지정된 된 도메인 클래스에서 xsd에서 생성 된 xml 형식의 이름입니다.|  
|노트|이 요소와 연결 된 비공식 메모|  
  
### <a name="xml-property-data"></a>Xml 속성 데이터  
 Xml 속성 노드 클래스 노드에 있습니다.  
  
|||  
|-|-|  
|속성|설명|  
|도메인 속성|Xml 직렬화 구성 데이터가 적용 되는 속성입니다. 읽기 전용입니다.|  
|모니커 키|True 이면 속성을이 도메인 클래스의 인스턴스를 참조 하는 모니커를 만들기 위한 키로 사용 됩니다.|  
|모니커 한정자는|True 이면 속성이 모니커의 한정자를 만드는 데 사용 됩니다. False 이면 및 SerializeId이 도메인 클래스에 대해 true가 아니면 모니커는 모니커가 포함 트리의 부모 요소의 한정 됩니다.|  
|표현|속성이; xml 특성으로 serialize 되는 경우 요소의 경우; 요소로 serialize Ignore 없는 경우 직렬화 합니다.|  
|Xml 이름|Xml 특성 또는 속성을 나타내는 요소에 사용 되는 이름입니다. 기본적으로 도메인 속성 이름의 소문자 버전입니다.|  
|노트|이 요소와 연결 된 비공식 메모|  
  
### <a name="xml-role-data"></a>Xml 역할 데이터  
 데이터 노드 역할은 원본 클래스 노드에 있습니다.  
  
|속성|설명|  
|--------------|-----------------|  
|사용자 지정 모니커는|사용자 고유의 코드를 생성 하 고이 관계를 트래버스하는 모니커 확인을 제공 하려는 경우 true로 설정 합니다.<br /><br /> 자세한 내용은 솔루션을 빌드하고 오류 메시지를 두 번 클릭 합니다.|  
|도메인 관계|이러한 옵션은 적용 하려는 관계를 지정 합니다. 읽기 전용입니다.|  
|요소를 생략 합니다.|True 이면 소스 역할에 해당 하는 XML 노드의 스키마에서 생략 됩니다.<br /><br /> 원본 및 대상 클래스 간에 둘 이상의 관계가 없으면이 역할 노드 두 관계에 속해 있는 링크를 구분 합니다. 따라서는 설정 하지 않으면이 옵션이 경우에 것이 좋습니다.|  
|역할 요소 이름|소스 역할에서 파생 되는 XML 요소의 이름을 지정 합니다. 기본값에는 역할 속성 이름입니다.|  
|전체 형식 사용|True 이면 각 대상 요소 또는 모니커 관계를 나타내는 XML 노드에 묶입니다. 이 경우 관계는 자체 도메인 속성이 true로 설정 되어야 합니다.|  
  
## <a name="see-also"></a>참고 항목  
 [탐색 및 프로그램 코드에서 모델 업데이트](../modeling/navigating-and-updating-a-model-in-program-code.md)   
 [도메인별 언어에서 코드 생성](../modeling/generating-code-from-a-domain-specific-language.md)
