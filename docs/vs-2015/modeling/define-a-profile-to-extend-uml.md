---
title: Define a profile to extend UML | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- profiles, UML
- stereotypes, UML
- UML, profiles and stereotypes
- UML - extending, defining profiles
- UML, customizing
- UML, profiles
ms.assetid: 776589cb-f89d-48d5-aafa-04a4c074b0d6
caps.latest.revision: 44
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: bdb6620f8d73bf7fae7b7dbb1b92af38e71345b6
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74295674"
---
# <a name="define-a-profile-to-extend-uml"></a>프로필을 정의하여 UML 확장
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

You can define a *UML profile* to customize the standard model elements for specific purposes. A profile defines one or more *UML stereotypes*. 스테레오타입을 사용하여 특정 종류의 개체를 나타내는 것으로 형식을 표시할 수 있습니다. 스테레오타입은 요소의 속성 목록을 확장할 수도 있습니다.

 지원되는 버전의 Visual Studio와 함께 여러 프로필이 설치됩니다. 이 기능을 지원하는 Visual Studio 버전을 확인하려면 [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)을 참조하세요. For more information about those profiles and about how to apply stereotypes, see [Customize your model with profiles and stereotypes](../modeling/customize-your-model-with-profiles-and-stereotypes.md).

 사용자 고유의 프로필을 정의하여 비즈니스 영역 또는 아키텍처에 맞게 UML을 조정 및 확장할 수 있습니다. 예를 들어 다음과 같은 가치를 제공해야 합니다.

- 웹 사이트를 자주 정의하는 경우 클래스 다이어그램의 클래스에 적용할 수 있는 «WebPage» 스테레오타입을 제공하는 고유한 프로필을 정의할 수 있습니다. 그런 다음 클래스 다이어그램을 사용하여 웹 사이트를 계획할 수 있습니다. 모든 «WebPage» 클래스에 페이지 콘텐츠, 스타일 등에 대한 추가 속성이 있습니다.

- 뱅킹 소프트웨어를 개발하는 경우 «Account» 스테레오타입을 제공하는 프로필을 정의할 수 있습니다. 그런 다음 클래스 다이어그램을 사용하여 다양한 계정 형식을 정의하고 형식 간의 관계를 표시할 수 있습니다.

  팀에 고유한 프로필을 배포할 수 있습니다. 각 팀 멤버가 프로필을 설치할 수 있습니다. 이렇게 하면 해당 스테레오타입을 사용하는 모델을 만들고 편집할 수 있습니다.

> [!NOTE]
> 편집 중인 모델에 프로필의 스테레오타입을 적용한 후 다른 사용자와 모델을 공유하는 경우 자신의 컴퓨터에 동일한 프로필을 설치해야 합니다. 그렇지 않으면 사용된 스테레오타입을 볼 수 없습니다.

 A profile is often part of a larger [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] extension. 예를 들어 모델의 일부를 코드로 변환하는 명령을 정의할 수 있습니다. 사용자가 변환하려는 패키지에 적용해야 하는 프로필을 정의할 수 있습니다. 단일 [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] 확장에서 이 프로필과 함께 새 명령을 배포합니다.

 프로필의 지역화된 변형을 정의할 수도 있습니다. 확장을 로드하는 사용자에게 해당 문화권에 적합한 변형이 표시됩니다.

## <a name="DefineProfile"></a> How to Define a Profile

#### <a name="to-define-a-uml-profile"></a>UML 프로필을 정의하려면

1. 파일 이름 확장명이 `.profile`인 새 XML 파일을 만듭니다.

2. Add stereotype definitions according to the guidelines described in [The Structure of a Profile](#Schema).

3. Visual Studio 확장(`.vsix` 파일)에 프로필을 추가합니다. 프로필에 대한 새 확장을 만들거나 기존 확장에 프로필을 추가할 수 있습니다.

     See the next section, [How to Add a Profile to a Visual Studio Extension](#AddProfile).

4. 컴퓨터에 확장을 설치합니다.

    1. 파일 이름 확장명이 `.vsix`인 확장 파일을 두 번 클릭합니다.

    2. Visual Studio를 다시 시작합니다.

5. 프로필이 설치되었는지 확인합니다.

    1. UML 탐색기에서 모델을 선택합니다.

    2. In the Properties window, click the **Profiles** property. 프로필이 메뉴에 나타납니다. 프로필 옆의 확인 표시를 설정합니다.

    3. 프로필에서 스테레오타입을 정의하는 요소를 선택합니다. In the Properties window, click the **Stereotypes** property. 스테레오타입이 목록에 나타납니다. 스테레오타입 중 하나에 대해 확인 표시를 설정합니다.

    4. 프로필에서 이 스테레오타입에 대한 추가 속성을 정의하는 경우 스테레오타입 속성을 확장하여 표시합니다.

6. 자신의 컴퓨터에 설치하도록 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]의 다른 사용자에게 확장 파일을 보냅니다.

## <a name="AddProfile"></a> How to Add a Profile to a Visual Studio Extension
 프로필을 설치하고 다른 사용자에게 보낼 수 있으려면 Visual Studio 확장에 프로필을 추가해야 합니다. For more information, see [Deploying Visual Studio Extensions](https://go.microsoft.com/fwlink/?LinkId=160780).

#### <a name="to-define-a-profile-in-a-new-visual-studio-extension"></a>새 Visual Studio 확장에서 프로필을 정의하려면

1. Visual Studio 확장 프로젝트를 만듭니다.

   > [!NOTE]
   > 이 절차를 사용하려면 [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)]가 설치되어 있어야 합니다.

   1. **파일** 메뉴에서 **새로 만들기**를 가리킨 다음 **프로젝트**를 클릭합니다.

   2. In the **New Project** dialog box, under **Installed Templates**, expand **Visual C#** , click **Extensibility**, and then click **VSIX project**. Set the project name and click **OK**.

2. 프로젝트에 프로필을 추가합니다.

   - In Solution Explorer, right-click the project, point to **Add**, and then click **Existing Item**. 대화 상자에서 프로필 파일을 찾습니다.

3. Set the profile file's **Copy to Output** property.

   1. In Solution Explorer, right-click the profile file, and then click **Properties**.

   2. In the Properties window, set the **Copy to Output Directory** property to **Copy Always**.

4. 솔루션 탐색기에서 `source.extension.vsixmanifest`를 엽니다.

    파일이 확장 매니페스트 편집기에서 열립니다.

5. On the **Assets** page, add a row describing the profile:

   - **새로 만들기**를 클릭합니다. Set the fields in the **Add New Asset** dialog as follows.

   - Set **Type** to `Microsoft.VisualStudio.UmlProfile`

        이것은 드롭다운 선택 항목 중 하나가 아니므로 키보드에서 이 이름을 입력합니다.

   - Click **File on filesystem** and select the name of your profile file, for example `MyProfile.profile`

6. 프로젝트를 빌드합니다.

7. **To debug the profile**, press F5.

    Visual Studio의 실험적 인스턴스가 열립니다. 이 인스턴스에서 모델링 프로젝트를 엽니다. UML 탐색기에서 모델의 루트 요소를 선택하고 속성 창에서 프로필을 선택합니다. 그런 다음 모델 내의 요소를 선택하고 요소에 대해 정의한 스테레오타입을 설정합니다.

8. **To extract the VSIX for deployment**

   1. In Windows Explorer, open the folder **.\bin\Debug** or **.\bin\Release** to find the **.vsix** file. 이 파일은 [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] 확장 파일입니다. 컴퓨터에 설치하고 다른 Visual Studio 사용자에게 보낼 수 있습니다.

   2. 확장을 설치하려면

       1. `.vsix` 파일을 두 번 클릭합니다. Visual Studio 확장 설치 관리자가 시작됩니다.

       2. 실행 중인 Visual Studio 인스턴스를 다시 시작합니다.

   [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)]를 설치하지 않은 경우 소규모 설치에는 다음 절차를 대신 사용할 수 있습니다.

#### <a name="to-define-a-profile-extension-without-using-visual-studio-sdk"></a>Visual Studio SDK를 사용하지 않고 프로필 확장을 정의하려면

1. 다음 세 개의 파일이 포함된 Windows 디렉터리를 만듭니다.

    - *YourProfile* `.profile`

    - `extension.vsixmanifest`

    - `[Content_Types].xml` - 이 이름을 대괄호와 함께 여기에 표시된 대로 입력합니다.

2. 다음 텍스트를 포함하도록 `[Content_Types].xml`을 편집합니다. 각 파일 이름 확장명에 대한 항목이 포함되었는지 확인합니다.

    ```
    <?xml version="1.0" encoding="utf-8"?>
    <Types xmlns="http://schemas.openxmlformats.org/package/2006/content-types">
      <Default Extension="profile" ContentType="application/octet-stream" />
      <Default Extension="vsixmanifest" ContentType="text/xml" />
    </Types>
    ```

3. 기존 `extension.vsixmanifest`를 복사하고 XML 편집기에서 편집합니다. ID, 이름 및 콘텐츠 노드를 변경합니다.

    - 다음 디렉터리에서 `extension.vsixmanifest`의 예를 확인할 수 있습니다.

         *drive* **:\Program Files\Microsoft Visual Studio [version]\Common7\IDE\Extensions\Microsoft\Architecture Tools\UmlProfiles**

    - 콘텐츠 노드는 다음과 같아야 합니다.

        ```
        <Content>
          <CustomExtension Type="Microsoft.VisualStudio.UmlProfile"
          >YourProfile.Profile</CustomExtension>
        </Content>
        ```

4. 세 개의 파일을 Zip 파일로 압축합니다.

     In Windows Explorer, select the three files, right-click, point to **Send To**, and then click **Compressed (zipped) folder**.

5. Zip 파일의 이름을 바꾸고 파일 이름 확장명을 `.zip`에서 `.vsix`로 변경합니다.

6. 적절한 버전의 Visual Studio가 있는 컴퓨터에 프로필을 설치하려면 `.vsix` 파일을 두 번 클릭합니다.

#### <a name="to-install-a-uml-profile-from-a-visual-studio-extension"></a>Visual Studio 확장에서 UML 프로필을 설치하려면

1. Windows 탐색기에서 `.vsix` 파일을 두 번 클릭하거나 Visual Studio 내에서 엽니다.

2. Click **Install** in the dialog box that appears.

3. To uninstall or temporarily disable the extension, open **Extensions and Updates** from the **Tools** menu.

## <a name="Localized"></a> How to Define Localized Profiles
 각 문화권 또는 언어에 대해 다른 프로필을 정의하고 모두 동일한 확장에 패키징할 수 있습니다. 사용자가 확장을 로드하면 해당 문화권에 대해 정의한 프로필이 표시됩니다.

 기본 프로필은 항상 제공해야 합니다. 사용자 문화권에 대해 프로필을 정의하지 않은 경우 기본 프로필이 표시됩니다.

#### <a name="to-define-a-localized-profile"></a>지역화된 프로필을 정의하려면

1. Create a profile as described in the previous sections[How to Define a Profile](#DefineProfile) and [How to Add a Profile to a Visual Studio Extension](#AddProfile). 이는 기본 프로필이며, 지역화된 프로필을 제공하지 않은 모든 설치에 사용됩니다.

2. 기본 프로필 파일과 동일한 디렉터리에 새 디렉터리를 추가합니다.

    > [!NOTE]
    > Visual Studio 확장 프로젝트를 사용하여 확장을 빌드하는 경우 솔루션 탐색기를 사용하여 프로젝트에 새 폴더를 추가합니다.

3. 새 디렉터리의 이름을 지역화된 문화권에 대한 ISO 짧은 코드로 변경합니다. 예를 들어 불가리아어는 `bg`이고, 프랑스어는 `fr`입니다. `fr-CA`와 같은 특정 문화권이 아니라 일반적으로 두 문자로 이루어진 중립 문화권 코드를 사용해야 합니다. For more information about culture codes, see [CultureInfo.GetCultures method](https://go.microsoft.com/fwlink/?LinkId=160782), which provides a complete list of culture codes.

4. 기본 프로필의 복사본을 새 디렉터리에 추가합니다. 파일 이름을 변경하지 마세요.

     A sample [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] Extension folder, before it is built or compressed into a `.vsix` file, would contain the following folders and files:

     `extension.vsixmanifest`

     `MyProfile.profile`

     `fr\MyProfile.profile`

     `de\MyProfile.profile`

    > [!NOTE]
    > 지역화된 버전의 프로필에 대한 참조를 `extension.vsixmanifest`에 삽입하면 안 됩니다. 복사된 프로필 파일은 부모 폴더의 프로필과 이름이 같아야 합니다.

5. 프로필의 새 복사본을 편집하고 `displayName` 특성과 같이 사용자에게 표시되는 모든 파트를 대상 언어로 번역합니다.

6. 개수 제한 없이 원하는 문화권에 대한 추가 문화권 폴더 및 지역화된 프로필을 만들 수 있습니다.

7. 이전 섹션에서 설명한 대로 확장 프로젝트를 빌드하거나 모든 파일을 압축하여 Visual Studio 확장을 빌드합니다.

## <a name="Schema"></a> The Structure of a Profile
 The XSD file for UML profiles can be found in the following sample: [Setting Stereotypes and Profiles XSD](https://go.microsoft.com/fwlink/?LinkID=213811). 프로필 파일 편집에 도움이 되도록 `.xsd` 파일을 다음 위치에 설치합니다.

 **%ProgramFiles%\Microsoft Visual Studio [version]\Xml\Schemas**

 이 섹션에서는 C# 프로필을 예로 사용합니다. 전체 프로필 정의는 다음 위치에서 확인할 수 있습니다.

 *drive* **:\Program Files\Microsoft Visual Studio [version]\Common7\IDE\Extensions\Microsoft\Architecture Tools\UmlProfiles\CSharp.profile**

 이 경로의 첫 번째 부분은 설치마다 다를 수 있습니다.

 For more information about the .NET profile, see [Standard stereotypes for UML models](../modeling/standard-stereotypes-for-uml-models.md).

### <a name="main-sections-of-the-uml-profile-definition"></a>UML 프로필 정의의 주요 섹션
 모든 프로필에는 다음 내용이 포함됩니다.

```
<?xml version="1.0" encoding="utf-8"?>
<profile dslVersion="1.0.0.0"
       name="CSharpProfile" displayName="C# Profile"
       xmlns="http://schemas.microsoft.com/UML2.1.2/ProfileDefinition">
  <stereotypes>...</stereotypes>
  <metaclasses>...</metaclasses>
  <propertyTypes>...</propertyTypes>
</profile>
```

> [!NOTE]
> `name`이라는 특성은 공백이나 문장 부호를 포함하지 않아야 합니다. 사용자 인터페이스에 표시되는 `displayName` 특성은 유효한 XML 문자열이어야 합니다.

 모든 프로필에 세 개의 주요 섹션이 있습니다. 해당 프로필은 반대 순서로 다음과 같습니다.

- `<propertyTypes>` - 스테레오타입 섹션에서 정의된 속성에 사용되는 형식 목록입니다.

- `<metaclasses>` - 이 프로필의 스테레오타입이 적용되는 모델 요소 형식(예: IClass, IInterface, IOperation, IDependency)의 목록입니다.

- `<stereotypes>` - 스테레오타입 정의입니다. 각 정의는 대상 모델 요소에 추가된 속성의 이름 및 형식을 포함합니다.

#### <a name="property-types"></a>속성 형식
 The `<propertyTypes>` section declares a list of types that are used for properties in the `<stereotypes>` section. 두 종류의 속성 형식이 있으며, 외부 형식과 열거형입니다.

 외부 형식은 표준 .NET 형식의 정규화된 이름을 선언합니다.

```
<externalType name="System.String" />
```

 열거형 형식은 리터럴 값 집합을 정의합니다.

```
<enumerationType name="PackageVisibility">
  <enumerationLiterals>
    <enumerationLiteral name="internal" displayName="internal"  />
    <enumerationLiteral name="protectedinternal" displayName="protected internal" />
  </enumerationLiterals>
</enumerationType>
```

#### <a name="metaclasses"></a>메타클래스
 `<metaclasses>` 섹션은 이 프로필의 스테레오타입을 정의할 수 있는 모델 요소 형식의 목록입니다.

```
<metaclass
      name="Microsoft.VisualStudio.Uml.Classes.IClass" />
<metaclass
      name="Microsoft.VisualStudio.Uml.Classes.IInterface" />
<metaclass
      name="Microsoft.VisualStudio.Uml.Components.IComponent" />
```

 For the full list of model element and relationship types that you can use as metaclasses, see [Model Element Types](#Elements).

#### <a name="stereotype-definition"></a>스테레오타입 정의
 `<stereotypes>` 섹션에는 하나 이상의 스테레오타입 정의가 포함되어 있습니다.

```
<stereotype name="CSharpClass" displayName="C# Class"> ...
```

 각 스테레오타입은 적용될 수 있는 하나 이상의 모델 요소 또는 관계 형식을 나열합니다. 모든 파생 형식을 포함하도록 기본 형식의 이름을 지정할 수 있습니다. 예를 들어 `Microsoft.VisualStudio.Uml.Classes.IType`을 지정하는 경우 스테레오타입을 `IClass`, `IInterface`, `IEnumeration` 및 여러 다른 형식의 요소에 적용할 수 있습니다.

```
<metaclasses>
  <metaclassMoniker name=
   "/CSharpProfile/Microsoft.VisualStudio.Uml.Classes.IClass" />
</metaclasses>
```

 `name`의 `metaclassMoniker` 특성은 `<metaClasses>` 섹션의 요소에 대한 링크입니다.

> [!NOTE]
> 모니커 이름은 `/yourProfileName/`으로 시작해야 합니다. 여기서 `yourProfileName`은 프로필의 `name` 특성(이 예제에서는 "CSharpProfile")에서 정의됩니다. 모니커는 메타클래스 섹션에 있는 항목 중 하나의 이름으로 끝납니다.

 각 스테레오타입은 적용되는 모델 요소에 추가하는 0개 이상의 속성을 나열할 수 있습니다. The `<propertyType>` contains a link to one of the types that are defined in the `<propertyTypes>` section. 링크는 `<externalTypeMoniker>`을 참조하는 `<externalType>,` 또는 `<enumerationTypeMoniker>`을 참조하는 `<enumerationType>` 중 하나여야 합니다. 다시, 링크는 프로필 이름으로 시작합니다.

```
  <properties>
    <property name="IsStatic"
            displayName="Is Static" defaultValue="false">
      <propertyType>
<externalTypeMoniker
               name="/CSharpProfile/System.Boolean" />
      </propertyType>
    </property>
    <property name="PackageVisibility"
              displayName="Package Visibility"
              defaultValue="internal">
      <propertyType>
        <enumerationTypeMoniker
              name="/CSharpProfile/PackageVisibility"/>
      </propertyType>
    </property>
  </properties>
</stereotype>
```

## <a name="Elements"></a> Model Element Types
 The set of types for which you can define stereotypes is listed in [UML model element types](../modeling/uml-model-element-types.md).

## <a name="troubleshooting"></a>문제 해결
 내 스테레오타입이 UML 모델에 나타나지 않습니다.
패키지 또는 모델에서 프로필을 선택해야 합니다. 그러면 패키지 또는 모델 내 요소에 스테레오타입이 나타납니다. For more information, see [Add stereotypes to UML model elements](../modeling/add-stereotypes-to-uml-model-elements.md).

 The following error appears when I open a UML model: **VS1707: The following profiles cannot be loaded because a serialization error occurred: MyProfile.profile**
1. .profile의 기본 XML 구문이 올바른지 확인합니다.

2. 각 모니커 이름이 /profileName/nodeName 형식인지 확인합니다. profileName은 루트 프로필 노드의 name 특성 값입니다. nodeName은 메타클래스, externalType 또는 enumerationType의 name 특성 값입니다.

3. Ensure the syntax is as described here, and as demonstrated in _drive_ **:\Program Files\Microsoft Visual Studio [version]\Common7\IDE\Extensions\Microsoft\Architecture Tools\UmlProfiles\\** .

4. 오류가 발생한 확장을 제거합니다. **도구** 메뉴에서 **확장 및 업데이트**를 클릭합니다.

   - 확장이 나타나지 않는 경우 다음 항목을 참조하세요.

5. VSIX 파일을 다시 빌드하고 Windows 탐색기에서 열어 다시 설치합니다. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]를 다시 시작합니다.

   The extension does not appear in Extension Manager, but when you try to re-install it, the following message appears: **The extension is already installed to all applicable products.**
   1. Remove the extension file from a subfolder of *LocalAppData*\Microsoft\VisualStudio\\[version]\Extensions\

   - To see *LocalAppData*, you must set Show Hidden Files and Folders in the View tab of the Windows Explorer Folder Options.

   - *LocalAppData* is typically in C:\Users\\*userName*\AppData\Local\

6. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]를 다시 시작합니다.

## <a name="see-also"></a>관련 항목:
 [Add stereotypes to UML model elements](../modeling/add-stereotypes-to-uml-model-elements.md) [Customize your model with profiles and stereotypes](../modeling/customize-your-model-with-profiles-and-stereotypes.md) [Standard stereotypes for UML models](../modeling/standard-stereotypes-for-uml-models.md) [Sample: Color UML Elements by Stereotype](https://go.microsoft.com/fwlink/?LinkID=213841) [Sample: Setting Stereotypes, Profiles XSD](https://go.microsoft.com/fwlink/?LinkID=213811)
