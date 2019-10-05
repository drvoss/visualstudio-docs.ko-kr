---
title: Office 솔루션에 대 한 응용 프로그램 매니페스트
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 62ad6a8147fc11b8bed34605b6447a1fe8a62a97
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62942925"
---
# <a name="application-manifests-for-office-solutions"></a>Office 솔루션에 대 한 응용 프로그램 매니페스트
  애플리케이션 매니페스트는 Microsoft Office 솔루션에 로드된 어셈블리를 설명하는 XML 파일입니다. Visual Studio에서 Microsoft Office 개발 도구를 사용 합니다 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] 에 정의 된 응용 프로그램 매니페스트 스키마를 [ClickOnce 응용 프로그램 매니페스트](../deployment/clickonce-application-manifest.md) 참조 합니다.

 Office 솔루션의 애플리케이션 매니페스트는 다음 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] 요소와 특성을 사용합니다.

|요소|설명|특성|
|-------------|-----------------|----------------|
|[&#60;어셈블리&#62; 요소 &#40;ClickOnce 응용 프로그램&#41;](../deployment/assembly-element-clickonce-deployment.md)|필수 요소. 최상위 요소입니다.|**manifestVersion**|
|[&#60;assemblyIdentity&#62; 요소 &#40;ClickOnce 응용 프로그램&#41;](../deployment/assemblyidentity-element-clickonce-deployment.md)|필수 요소. [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] 응용 프로그램의 주 어셈블리를 식별합니다.|**name**<br /><br /> **version**<br /><br /> **publicKeyToken**<br /><br /> **processorArchitecture**<br /><br /> **language**|
|[&#60;trustInfo&#62; 요소 &#40;ClickOnce 응용 프로그램&#41;](../deployment/trustinfo-element-clickonce-application.md)|애플리케이션 보안 요구 사항을 식별합니다.|없음|
|[&#60;entryPoint&#62; 요소 &#40;ClickOnce 응용 프로그램&#41;](../deployment/entrypoint-element-clickonce-application.md)|필수 요소. 실행을 위해 애플리케이션 코드 진입점을 식별합니다.|**name**<br /><br /> **dependencyName**<br /><br /> **customHostSpecified**|
|[&#60;종속성&#62; 요소 &#40;ClickOnce 응용 프로그램&#41;](../deployment/dependency-element-clickonce-deployment.md)|필수 요소. 애플리케이션을 실행하는 데 필요한 각 종속성을 식별합니다. 필요에 따라 사전 설치해야 하는 어셈블리를 식별합니다.|없음|
|[&#60;파일&#62; 요소 &#40;ClickOnce 응용 프로그램&#41;](../deployment/file-element-clickonce-application.md)|필수 요소. 애플리케이션에서 사용되는 각 비어셈블리 파일을 식별합니다. 파일에 연결된 COM(구성 요소 개체 모델) 격리 데이터를 포함할 수 있습니다.|**name**<br /><br /> **size**|

 Office 솔루션의 애플리케이션 매니페스트에는 `co.v1` 네임스페이스에 다음과 같은 요소가 있습니다.

```xml
<entryPoint>
    <co.v1:customHostSpecified />
</entryPoint>
```

 또한 이러한 애플리케이션 매니페스트에는 `vstav3` 네임스페이스에 다음과 같은 요소 및 특성도 있습니다.

```xml
<addIn>
  <entryPointsCollection>
    <entryPoints>
      <entryPoint>
      </entryPoint>
    </entryPoints>
  </entryPointsCollection>
  <update></update>
  <postActions>
    <postAction>
      <postActionData>
      </postActionData>
    <postAction>
  </postActions>
  <application>
    <customizations>
      <customization>
      </customization>
    </customizations>
  </application
</addIn>
```

|요소|설명|특성|
|-------------|-----------------|----------------|
|[&#60;customHostSpecified&#62; 요소 &#40;Visual Studio에서 Office 개발&#41;](../vsto/customhostspecified-element-office-development-in-visual-studio.md)|필수 요소. 매니페스트를 특별히 Office 솔루션으로 표시합니다.|없음|
|[&#60;추가 기능&#62; 요소 &#40;Visual Studio에서 Office 개발&#41;](../vsto/addin-element-office-development-in-visual-studio.md)|필수 요소. 진입점을 단일 네임스페이스에 저장합니다.|없음|
|[&#60;entryPointsCollection&#62; 요소 &#40;Visual Studio에서 Office 개발&#41;](../vsto/entrypointscollection-element-office-development-in-visual-studio.md)|필수 요소. 하나 이상의 Office 솔루션에 대한 모든 어셈블리를 그룹화합니다.|**ID**|
|[&#60;진입점&#62; 요소 &#40;Visual Studio에서 Office 개발&#41;](../vsto/entrypoints-element-office-development-in-visual-studio.md)|필수 요소. Office 솔루션을 실행하는 모든 어셈블리를 그룹화합니다.|없음|
|[&#60;entryPoint&#62; 요소 &#40;Visual Studio에서 Office 개발&#41;](../vsto/entrypoint-element-office-development-in-visual-studio.md)|필수 요소. Office 솔루션에서 실행하는 어셈블리를 식별합니다.|**class**<br /><br /> **contract**|
|[&#60;업데이트&#62; 요소 &#40;Visual Studio에서 Office 개발&#41;](../vsto/update-element-office-development-in-visual-studio.md)|필수 요소. 솔루션에 대한 업데이트를 구성합니다.|**enabled**<br /><br /> **expiration**|
|[&#60;postActions&#62; 요소 &#40;Visual Studio에서 Office 개발&#41;](../vsto/postactions-element-office-development-in-visual-studio.md)|선택 사항입니다. Office 솔루션을 설치한 후 실행하는 모든 배포 후 작업을 그룹화합니다.|없음|
|[&#60;postAction&#62; 요소 &#40;Visual Studio에서 Office 개발&#41;](../vsto/postaction-element-office-development-in-visual-studio.md)|선택 사항입니다. 배포 후 작업을 식별합니다.|없음|
|[&#60;postActionData&#62; 요소 &#40;Visual Studio에서 Office 개발&#41;](../vsto/postactiondata-element-office-development-in-visual-studio.md)|선택 사항입니다. 배포 후 작업에 대한 데이터를 구성합니다.|없음|
|[&#60;응용 프로그램&#62; 요소 &#40;Visual Studio에서 Office 개발&#41;](../vsto/application-element-office-development-in-visual-studio.md)|필수 요소. 애플리케이션 관련 정보를 단일 노드에 래핑합니다.|없음|
|[&#60;사용자 지정&#62; 요소 &#40;Visual Studio에서 Office 개발&#41;](../vsto/customizations-element-office-development-in-visual-studio.md)|필수 요소. 별도의 네임스페이스에 모든 애플리케이션 호스트 관련 정보를 저장합니다.|없음|
|[&#60;사용자 지정&#62; 요소 &#40;Visual Studio에서 Office 개발&#41;](../vsto/customization-element-office-development-in-visual-studio.md)|필수 요소. 별도의 네임스페이스에 애플리케이션 호스트 관련 정보를 저장합니다.|**xmlns**|
|[&#60;문서&#62; 요소 &#40;Visual Studio에서 Office 개발&#41;](../vsto/document-element-office-development-in-visual-studio.md)|문서 수준 솔루션에 대해서만 필수 요소. 사용자 지정 관련 정보를 저장합니다.|**solutionId**|
|[&#60;appAddin&#62; 요소 &#40;Visual Studio에서 Office 개발&#41;](../vsto/appaddin-element-office-development-in-visual-studio.md)|애플리케이션 수준 솔루션에 대해서만 필수 요소. 사용자 지정 관련 정보를 저장합니다.|**application**<br /><br /> **loadBehavior**<br /><br /> **keyName**|
|[&#60;friendlyName&#62; 요소 &#40;Visual Studio에서 Office 개발&#41;](../vsto/friendlyname-element-office-development-in-visual-studio.md)|선택 사항입니다. 설치된 VSTO 추가 기능 목록에 표시되는 VSTO 추가 기능의 이름을 저장합니다.|없음|
|[&#60;설명&#62; 요소 &#40;Visual Studio에서 Office 개발&#41;](../vsto/description-element-office-development-in-visual-studio.md)|VSTO 추가 기능에 대해서만 필수 요소. 설치된 프로그램 목록에 나타나는 설명을 저장합니다.|없음|
|[&#60;formRegions&#62; 요소 &#40;Visual Studio에서 Office 개발&#41;](../vsto/formregions-element-office-development-in-visual-studio.md)|양식 영역을 포함하는 Outlook VSTO 추가 기능에 대해서만 필수 요소.|없음|
|[&#60;formRegion&#62; 요소 &#40;Visual Studio에서 Office 개발&#41;](../vsto/formregion-element-office-development-in-visual-studio.md)|양식 영역을 포함하는 Outlook VSTO 추가 기능에 대해서만 필수 요소.|**이름**|
|[&#60;vstoRuntime&#62; 요소 &#40;Visual Studio에서 Office 개발&#41;](../vsto/vstoruntime-element-office-development-in-visual-studio.md)|필수 요소. Office 솔루션에서 지원되는 Visual Studio Tools for Office Runtime의 특정 버전을 설명합니다.|**release**<br /><br /> **version**<br /><br /> **supportUrl**|

## <a name="remarks"></a>설명
 Office 솔루션의 애플리케이션 및 배포 매니페스트를 수동으로 편집할 수 있습니다. 그런 다음 응용 프로그램에 다시 서명 해야 하 고 매니페스트 생성 및 편집 도구를 사용 하 여 배포 매니페스트 (*mage.exe* 하 고 *mageui.exe*). 자세한 내용은 [방법: 애플리케이션 및 배포 매니페스트 다시 서명](../deployment/how-to-re-sign-application-and-deployment-manifests.md)을 참조하세요.

## <a name="file-location"></a>파일 위치
 애플리케이션 매니페스트는 솔루션의 단일 버전에 따라 다릅니다. 이러한 이유로 애플리케이션 매니페스트를 배포 매니페스트와 분리하여 저장해야 합니다. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 는 버전별 파일을 게시 폴더의 *응용 프로그램 파일* 하위 디렉터리에 있는 관련 버전을 따라 명명된 하위 디렉터리에 배치합니다.

## <a name="file-name-syntax"></a>파일 이름 구문
 식별 한 대로 응용 프로그램 매니페스트 파일의 이름을 전체 이름 및 응용 프로그램의 확장을 이어야 합니다는 **assemblyIdentity** 요소 뒤에 확장명이 *.manifest*합니다. 예를 들어, 응용 프로그램 매니페스트를 참조 하는 *OutlookAddIn1.dll* 사용자 지정 다음 파일 이름 구문을 사용 합니다.

 `OutlookAddIn1.dll.manifest`

## <a name="see-also"></a>참고 항목

- [Office 솔루션의 배포 매니페스트](../vsto/deployment-manifests-for-office-solutions.md)
- [ClickOnce 애플리케이션 매니페스트](../deployment/clickonce-application-manifest.md)