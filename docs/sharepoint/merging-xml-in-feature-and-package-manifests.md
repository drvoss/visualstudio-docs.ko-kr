---
title: 매니페스트 XML 기능 및 패키지 병합 | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, packaging
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 1378cddbc9770af923a98f1b7083a8792874b5b3
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63429279"
---
# <a name="merge-xml-in-feature-and-package-manifests"></a>기능 및 패키지 매니페스트에서 XML 병합
  기능과 패키지 정의한 [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] 매니페스트 파일. 이러한 패키지 매니페스트 디자이너와 사용자 지정에서 생성 된 데이터의 조합인 [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] 가 매니페스트 템플릿을 입력 합니다. 패키징 시 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 사용자 지정 병합 [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] 디자이너 제공를 사용 하 여 문을 [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] 하 여 패키지 된 [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] 매니페스트 파일. 유사한 요소 병합 예외의 뒷부분에 설명 된 예외를 사용 하 여 병합 하지 않으려면 [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] 유효성 검사 오류를 SharePoint에 파일을 배포한 후 더 작고 효율적으로 파일 매니페스트를 확인 합니다.

## <a name="modify-the-manifests"></a>매니페스트를 수정 합니다.
 기능 또는 패키지 디자이너를 사용 하지 않도록 설정 될 때까지 패키지 매니페스트 파일은 직접 수정할 수 없습니다. 사용자 지정을 수동으로 추가할 수 있지만 [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] 매니페스트 템플릿 요소 기능 및 패키지 디자이너를 통해 또는 [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] 편집기입니다. 자세한 내용은 [방법: Customize a SharePoint Feature](../sharepoint/how-to-customize-a-sharepoint-feature.md) 고 [방법: SharePoint 솔루션 패키지 사용자 지정](../sharepoint/how-to-customize-a-sharepoint-solution-package.md)합니다.

## <a name="feature-and-package-manifest-merge-process"></a>기능 및 패키지 매니페스트 병합 프로세스
 디자이너에서 제공 요소와 함께 사용자 지정 요소를 결합 하는 경우 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 다음 프로세스를 사용 합니다. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 각 요소에 고유한 키 값이 있는지 여부를 확인 합니다. 요소에 고유한 키 값이 없으면 요소가 패키지된 매니페스트 파일에 추가됩니다. 이와 마찬가지로 여러 키가 있는 요소는 병합될 수 없으므로 따라서 매니페스트 파일에 추가 됩니다.

 요소에 고유 키가 있으면 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 디자이너와 사용자 지정 키의 값을 비교 합니다. 값이 일치 하는 경우 단일 값으로 병합 합니다. 값이 다르면 디자이너 키 값을 무시 되 고 사용자 지정 키 값이 사용 됩니다. 컬렉션도 병합 됩니다. 예를 들어 경우 디자이너에서 생성 [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] 사용자 지정 [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] 모두 어셈블리 컬렉션을 포함, 패키지 매니페스트 하나만 어셈블리 컬렉션을 포함 합니다.

## <a name="merge-exceptions"></a>예외를 병합 합니다.
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 대부분의 디자이너 병합 [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] 유사한 사용자 지정과 함께 요소 [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] 만큼 동일 하 게 고유한 식별 특성을 단일 요소입니다. 그러나 일부 요소에 필요한 고유 식별자를 부족 [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] 병합 합니다. 이러한 요소 라고 *예외를 병합*입니다. 이러한 경우 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 사용자 지정을 병합 하지 않습니다 [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] 디자이너에서 제공 하는 함께 요소 [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] 요소인 하지만 대신 패키지 매니페스트 파일에 추가 합니다.

 다음은 기능 및 패키지에 대 한 병합 예외 목록을 [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] 매니페스트 파일.

|Designer|XML 요소|
|--------------|-----------------|
|기능 디자이너|ActivationDependency|
|기능 디자이너|UpgradeAction|
|패키지 디자이너|SafeControl|
|패키지 디자이너|CodeAccessSecurity|

## <a name="feature-manifest-elements"></a>기능 매니페스트 요소
 다음 표는 병합할 수 있는 모든 기능 매니페스트 요소 및 일치에 사용 되는 고유 키의 목록입니다.

|요소 이름|고유 키|
|------------------|----------------|
|기능 (모든 특성)|*특성 이름* (Feature 요소의 각 특성 이름이 고유한 키 임)|
|ElementFile|위치|
|ElementManifests/ElementManifest|위치|
|속성/속성|Key|
|CustomUpgradeAction|이름|
|CustomUpgradeActionParameter|이름|

> [!NOTE]
> CustomUpgradeAction 요소를 수정 하는 유일한 방법은 사용자 지정 이므로 [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] 편집기 없습니다를 병합 한 결과 부족 합니다.

## <a name="package-manifest-elements"></a>패키지 매니페스트 요소
 다음 표는 병합할 수 있는 모든 패키지 매니페스트 요소 및 일치에 사용 되는 고유 키의 목록입니다.

|요소 이름|고유 키|
|------------------|----------------|
|솔루션 (모든 특성)|*특성 이름* (Solution 요소의 각 특성 이름이 고유한 키 임)|
|ApplicationResourceFiles/ApplicationResourceFile|위치|
|어셈블리/어셈블리|위치|
|ClassResources/ClassResource|위치|
|DwpFiles/DwpFile|위치|
|FeatureManifests/FeatureManifest|위치|
|Resources/Resource|위치|
|RootFiles/RootFile|위치|
|SiteDefinitionManifests/SiteDefinitionManifest|위치|
|WebTempFile|위치|
|TemplateFiles/TemplateFile|위치|
|SolutionDependency|SolutionID|

## <a name="manually-add-deployed-files"></a>배포 된 파일에 수동으로 추가
 ApplicationResourceFile DwpFiles, 등의 일부 매니페스트 요소에 파일 이름을 포함 하는 위치를 지정 합니다. 그러나 매니페스트 템플릿 파일 이름 항목을 추가 파일이 추가 되지 않습니다는 기본 패키지입니다. 패키지에 포함 하 여 해당 배포 유형 속성을 적절 하 게 설정 하는 프로젝트에 파일을 추가 해야 합니다.

## <a name="see-also"></a>참고자료
- [패키지 및 SharePoint 솔루션 배포](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
- [SharePoint 솔루션 빌드 및 디버그](../sharepoint/building-and-debugging-sharepoint-solutions.md)
