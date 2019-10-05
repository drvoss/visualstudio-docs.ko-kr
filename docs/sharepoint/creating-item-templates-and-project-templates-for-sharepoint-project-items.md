---
title: 항목이 SharePoint에 대 한 템플릿/프로젝트 템플릿 프로젝트 항목
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint project items, creating custom templates
- .spdata files
- projects [SharePoint development in Visual Studio], creating custom templates
- SharePoint projects, creating custom templates
- SharePoint development in Visual Studio, creating custom project and item templates
- project items [SharePoint development in Visual Studio], creating custom templates
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 8f41783689e572ca823788e1a8dbcf772f07e924
ms.sourcegitcommit: 13ab9a5ab039b070b9cd9251d0b83dd216477203
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/23/2019
ms.locfileid: "66177622"
---
# <a name="create-item-templates-and-project-templates-for-sharepoint-project-items"></a>SharePoint 프로젝트 항목에 대 한 프로젝트 템플릿과 항목 템플릿 만들기

사용자 지정 SharePoint 프로젝트 항목 형식을 정의할 때에 프로젝트 템플릿 또는 항목 템플릿을 사용 하 여 연결할 수 있습니다. 이 연결에는 다른 개발자가 Visual Studio에서 프로젝트 항목을 사용할 수 있습니다. 또한 템플릿 마법사를 만들 수 있습니다.

예를 들어, Visual Studio 프로젝트 템플릿 또는 SharePoint 사이트에 필드 추가 대 한 항목 템플릿이 포함 되지 않습니다. 필드를 나타내는 SharePoint 프로젝트 항목 형식을 정의 하 고 그런 다음 다른 개발자 필드 항목을 SharePoint 프로젝트에 추가 하는 데 사용할 수 있는 항목 템플릿을 작성할 수 있습니다. 또는 개발자 필드 항목에는 새 SharePoint 프로젝트를 만들 수 있도록 프로젝트 템플릿을 생성할 수 있습니다. 두 경우 모두 개발자는 사용자 템플릿을 사용 하는 경우 표시 되는 마법사를 제공할 수 있습니다. 이 마법사는 새 항목 또는 프로젝트를 구성 하는 개발자에서 정보를 수집할 수 있습니다.

항목 템플릿 및 프로젝트 템플릿은 *.zip* 프로젝트 항목 또는 프로젝트를 만들려면 Visual Studio에서 사용 되는 파일을 포함 하는 파일입니다. 프로젝트 템플릿과 항목 템플릿의 기본 사항에 대 한 자세한 내용은 참조 하세요. [프로젝트 및 항목 템플릿 만들기](../ide/creating-project-and-item-templates.md)합니다.

## <a name="create-item-templates"></a>항목 템플릿 만들기
 SharePoint 프로젝트 항목에 대 한 항목 템플릿을 만들면 몇 가지는 항상 필요한 파일 및 프로젝트 항목의 특정 형식에서 사용할 수 있는 선택적 파일입니다. SharePoint 프로젝트 항목 형식 정의 및에 대 한 항목 템플릿을 만드는 방법을 보여 주는 연습을 참조 하세요 [연습: 항목 템플릿, 1 부를 사용 하 여 사용자 지정 작업 프로젝트 항목 만들기](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)합니다.

 다음 표에 SharePoint 프로젝트 항목에 대 한 항목 템플릿을 만드는 데 필요한 파일이 있습니다.

|필수 파일|설명|
|-------------------|-----------------|
|*.spdata* 파일|이 XML 파일 내용 및 프로젝트 항목의 기본 동작을 지정합니다. 이 파일 항목 템플릿에 포함 되어야 합니다. 내용에 대 한 자세한 내용은 *.spdata* 파일을 참조 하십시오 [SharePoint 프로젝트 항목 스키마 참조](../sharepoint/sharepoint-project-item-schema-reference.md)합니다.|
|A *.vstemplate* 파일입니다.|이 파일에 템플릿을 표시 하는 데 필요한 정보를 사용 하 여 Visual Studio를 제공 합니다 **새 항목 추가** 대화 상자 및 템플릿에서 프로젝트 항목을 만들려면. 이 파일 항목 템플릿에 포함 되어야 합니다. 자세한 내용은 [Visual Studio 템플릿 메타 데이터 파일](/previous-versions/visualstudio/visual-studio-2010/xsxc3ete\(v\=vs.100\))합니다.|
|구현 하는 Visual Studio 확장 프로그램 어셈블리를를 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> 인터페이스입니다.|이 어셈블리는 프로젝트 항목의 런타임 동작을 정의합니다. 이 어셈블리 항목 템플릿 사용 하 여 VSIX 패키지에 포함 되어야 합니다. 자세한 내용은 [사용자 지정 SharePoint 프로젝트 항목 형식 정의](../sharepoint/defining-custom-sharepoint-project-item-types.md) 하 고 [Visual Studio에서 SharePoint 도구의 확장을 배포](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)합니다.|

 다음 표에서 가장 일반적인 항목 템플릿에 포함 될 수 있는 선택적 파일의 일부를 나열 합니다. 일부 유형의 프로젝트 항목에는 다른 파일을 여기에 나열 되지 필요할 수 있습니다.

| 선택적 파일 | 설명 |
|----------------------| - |
| *Elements.xml* | A *Feature 요소* 파일입니다. 이 파일의 UI 및 프로젝트 항목을 만든 사용자 지정 동작을 정의 합니다. 각 유형의 목록 인스턴스, 콘텐츠 형식 또는 사용자 지정 동작 등 사용자 지정에는이 파일의 내용을 정의 하는 다른 스키마에 있습니다. 자세한 내용은 참조 하세요. [문서 블록: 기능](http://go.microsoft.com/fwlink/?LinkId=169183) 하 고 [스키마 기능](http://go.microsoft.com/fwlink/?LinkId=169192)합니다. |
| *Schema.xml* | 목록 정의 대 한 스키마 파일입니다. 자세한 내용은 참조 하세요. [문서 블록: 목록 및 문서 라이브러리](http://go.microsoft.com/fwlink/?LinkId=177792) 하 고 [Schema.xml](http://go.microsoft.com/fwlink/?LinkId=177793)합니다. |
| *.webpart* | A *웹 파트 정의* 파일입니다. 이 파일에는 웹 파트에 대 한 속성 설정을 포함합니다. 자세한 내용은 참조 하세요. [문서 블록: 웹 파트](http://go.microsoft.com/fwlink/?LinkId=177791)합니다. |
| *.ascx* | ASP.NET UserControl 파일입니다. 이 파일에는 비주얼 웹 파트의 UI를 정의 합니다. |
| *.aspx* | ASP.NET 페이지 파일입니다. 이 파일에 응용 프로그램 페이지를 정의 하는 XML 태그를 포함 합니다. |
| *.cs* 나 *.vb* 파일 | 이러한 코드 파일의 Visual C# 또는 Visual Basic 코드, 응용 프로그램 페이지, 웹 파트, 워크플로 등에서 액세스할 수 있는 프로그래밍 모델에 있는 SharePoint 사용자 지정 동작을 정의 합니다. |

## <a name="create-project-templates"></a>프로젝트 템플릿 만들기
 SharePoint 프로젝트 템플릿을 만들 때에 다음과 같은 몇 가지 파일은 항상 특정 형식의 프로젝트에서 사용할 수 있는 필수 및 선택적 파일입니다. 일반적으로 SharePoint 프로젝트에는 SharePoint 프로젝트 항목을 하나 이상 포함 됩니다. 그러나이 필요 하지 않습니다. 예를 들어, 다른 프로젝트에서 만든 SharePoint 솔루션을 배포 하는 데에 사용 하기 위한 SharePoint 프로젝트 템플릿을 정의할 수 있습니다.

 SharePoint 프로젝트 항목 형식 정의 및 프로젝트 템플릿을 만드는 방법을 보여 주는 연습을 참조 하세요. [연습: 1 부 프로젝트 템플릿을 사용 하 여 사이트 열 프로젝트 항목 만들기](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)합니다.

 다음 표에서 SharePoint 프로젝트 템플릿에 포함 되어야 하는 파일을 나열 합니다.

|필수 파일|설명|
|-------------------|-----------------|
|A *.vstemplate* 파일|이 파일에 템플릿을 표시 하는 데 필요한 정보를 사용 하 여 Visual Studio를 제공 합니다 **새 프로젝트** 대화 상자 및 템플릿에서 프로젝트를 만들려면. 자세한 내용은 [Visual Studio 템플릿 메타 데이터 파일](/previous-versions/visualstudio/visual-studio-2010/xsxc3ete\(v\=vs.100\))합니다.|
|A *.csproj* 하거나 *.vbproj* 파일|프로젝트 파일입니다. 내용 및 프로젝트의 구성 설정을 정의합니다.|
|*Package.package*|이 파일은 프로젝트에 대 한 배포 패키지를 정의 합니다. 패키지 디자이너를 사용 하 여 솔루션 패키지를 프로젝트에 대 한 사용자 지정 하는 경우 Visual Studio 솔루션 패키지에 대 한 데이터를이 파일에 저장 합니다.<br /><br /> 사용자 지정 SharePoint 프로젝트 템플릿을 만들 때만 필요한의 최소 구성 요소를 포함 하는 것이 좋습니다 합니다 *Package.package* 파일 및 Api를 사용 하 여 솔루션 패키지를 구성 하는 <xref:Microsoft.VisualStudio.SharePoint.Packages> 프로젝트 템플릿과 사용 하 여 연결 된 확장의 네임 스페이스입니다. 이 작업을 수행 하는 경우 프로젝트 템플릿을의 구조에 향후 변경 사항에서 보호 되는 *Package.package* 파일입니다. 만드는 방법을 보여 주는 예제는 *Package.package* 최소한의 필요한를 사용 하 여 파일 콘텐츠를 참조 하십시오 [연습: 1 부 프로젝트 템플릿을 사용 하 여 사이트 열 프로젝트 항목 만들기](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)합니다.<br /><br /> 수정 하려는 경우는 *Package.package* 파일을 직접,에서 스키마를 사용 하 여 콘텐츠를 확인할 수 있습니다 *% Program Files (x86)%\Microsoft Visual Studio 11.0\Xml\Schemas\PackageModelSchema.xsd* .|
|*Package.Template.xml*|이 파일은 솔루션 매니페스트 파일에 대 한 기본 제공 (*manifest.xml*) SharePoint 솔루션 패키지 ( *.wsp*) 프로젝트에서 생성 됩니다. 프로젝트 형식의 사용자가 변경할 수 없습니다는 몇 가지 동작을 지정 하려는 경우이 파일에 콘텐츠를 추가할 수 있습니다. 자세한 내용은 참조 하세요. [문서 블록: 솔루션](http://go.microsoft.com/fwlink/?LinkId=169186) 하 고 [솔루션 스키마](http://go.microsoft.com/fwlink/?LinkId=177794)합니다.<br /><br /> 프로젝트에서 솔루션 패키지를 빌드할 때 Visual Studio의 콘텐츠를 병합 하는 합니다 *Package.package* 하며 *Package.Template.xml* 솔루션 파일 매니페스트 파일. 솔루션 패키지를 작성 하는 방법에 대 한 자세한 내용은 참조 하세요. [방법: MSBuild 작업을 사용 하 여 SharePoint 솔루션 패키지 만들기](../sharepoint/how-to-create-a-sharepoint-solution-package-by-using-msbuild-tasks.md)합니다.|

 다음 표에서 프로젝트 템플릿에 포함 될 수 있는 선택적 파일을 나열 합니다.

|선택적 파일|설명|
|-------------------|-----------------|
|SharePoint 프로젝트 항목|SharePoint 프로젝트 항목 형식을 정의 하는 하나 이상의.spdata 파일을 포함할 수 있습니다. 각 *.spdata* 일치 하는 파일 있어야 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> 프로젝트 템플릿 사용 하 여 VSIX 패키지에 포함 된 확장 프로그램 어셈블리에 구현 합니다. 자세한 내용은 [항목 템플릿 만들기](#create-item-templates)합니다.<br /><br /> 일반적으로 SharePoint 프로젝트에는 SharePoint 프로젝트 항목을 하나 이상 포함 됩니다. 그러나이 필요 하지 않습니다.|
|*\<featureName>.feature*|이 파일은 배포에 대 한 여러 프로젝트 항목을 그룹화 하는 데 사용 되는 SharePoint 기능을 정의 합니다. 기능 디자이너를 사용 하 여 프로젝트의 기능을 사용자 지정 Visual Studio 기능에 대 한 데이터를이 파일에 저장 합니다. 다양 한 기능에 프로젝트 항목을 그룹화 하려는 경우에 여러를 포함할 수 있습니다 *.feature* 파일입니다.<br /><br /> 사용자 지정 SharePoint 프로젝트 템플릿을 만들 때 각 최소 필수 콘텐츠를 포함 하는 것이 좋습니다 *.feature* 파일 및 Api를 사용 하 여 기능을 구성 합니다 <xref:Microsoft.VisualStudio.SharePoint.Features> 네임 스페이스에는 프로젝트 템플릿과 사용 하 여 연결 된 확장입니다. 이 작업을 수행 하는 경우 프로젝트 템플릿을의 구조에 향후 변경 사항에서 보호 되는 *.feature* 파일입니다. 만드는 방법을 보여 주는 예제는 *.feature* 최소한의 필요한를 사용 하 여 파일 콘텐츠를 참조 하십시오 [연습: 1 부 프로젝트 템플릿을 사용 하 여 사이트 열 프로젝트 항목 만들기](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)합니다.<br /><br /> 수정 하려는 경우는 *.feature* 파일을 직접,에서 스키마를 사용 하 여 콘텐츠를 확인할 수 있습니다 *% Program Files (x86)%\Microsoft Visual Studio 11.0\Xml\Schemas\FeatureModelSchema.xsd*합니다.|
|*\<featureName>.Template.xml*|이 파일은 기능 매니페스트 파일에 대 한 기본 제공 (*Feature.xml*) 프로젝트에서 생성 되는 각 기능에 대 한 합니다. 프로젝트 형식의 사용자가 변경할 수 없습니다는 몇 가지 동작을 지정 하려는 경우이 파일에 콘텐츠를 추가할 수 있습니다. 자세한 내용은 참조 하세요. [문서 블록: 기능](http://go.microsoft.com/fwlink/?LinkId=169183) 하 고 [Feature.xml](http://go.microsoft.com/fwlink/?LinkId=177795) 파일입니다.<br /><br /> Visual Studio의 각 쌍의 내용을 병합 프로젝트에서 솔루션 패키지를 빌드하면  *\<featureName >.feature* 파일 및  *\<featureName >. Template.xml 파일* 기능 파일 매니페스트 파일. 솔루션 패키지를 작성 하는 방법에 대 한 자세한 내용은 참조 하세요. [방법: MSBuild 작업을 사용 하 여 SharePoint 솔루션 패키지 만들기](../sharepoint/how-to-create-a-sharepoint-solution-package-by-using-msbuild-tasks.md)합니다.|

## <a name="create-wizards-for-item-templates-and-project-templates"></a>마법사 프로젝트 템플릿과 항목 템플릿 만들기
 SharePoint 프로젝트 항목 형식을 정의 하 고 항목이 나 프로젝트 템플릿을 사용 하 여 연결 후에 마법사를 만들 수 있습니다. 개발자가 SharePoint 프로젝트 항목을 포함 하는 새 프로젝트를 만들려면 프로젝트 템플릿을 사용 하거나 개발자 항목 템플릿을 사용 하 여 프로젝트에 SharePoint 프로젝트 항목을 추가 하는 경우 표시 됩니다. 새 SharePoint 프로젝트 항목을 초기화 하는 개발자 정보를 수집 하는 마법사를 사용할 수 있습니다.

 프로젝트 템플릿과 항목 템플릿 마법사를 만드는 방법을 보여 주는 연습을 참조 하세요. [연습: 항목 템플릿, 2 부를 사용 하 여 사용자 지정 작업 프로젝트 항목 만들기](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md) 고 [연습: 2 부 프로젝트 템플릿을 사용 하 여 사이트 열 프로젝트 항목 만들기](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)합니다.

## <a name="see-also"></a>참고자료

- [사용자 지정 SharePoint 프로젝트 항목 형식 정의](../sharepoint/defining-custom-sharepoint-project-item-types.md)
- [연습: 항목 템플릿, 1 부를 사용 하 여 사용자 지정 작업 프로젝트 항목 만들기](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)
- [연습: 항목 템플릿, 2 부를 사용 하 여 사용자 지정 작업 프로젝트 항목 만들기](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md)
- [연습: 1 부 프로젝트 템플릿을 사용 하 여 사이트 열 프로젝트 항목 만들기](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)
- [연습: 2 부 프로젝트 템플릿을 사용 하 여 사이트 열 프로젝트 항목 만들기](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)
- [프로젝트 및 항목 템플릿 만들기](../ide/creating-project-and-item-templates.md)
