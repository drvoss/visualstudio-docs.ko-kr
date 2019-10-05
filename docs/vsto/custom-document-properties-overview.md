---
title: 사용자 지정 문서 속성 개요
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], custom properties
- custom document properties
- document-level customizations [Office development in Visual Studio], custom properties
- Office documents [Office development in Visual Studio], custom properties
- _AssemblyLocation property
- _AssemblyName property
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 7b3f4038a05478d8e2d747efa700c7ece02e4827
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62951175"
---
# <a name="custom-document-properties-overview"></a>사용자 지정 문서 속성 개요

문서 수준 프로젝트를 빌드할 때 Visual Studio 프로젝트의 문서에 두 개의 사용자 지정 속성을 추가 합니다. \_AssemblyLocation 및 \_AssemblyName 합니다. 사용자가 문서를 열면, 이러한 사용자 지정 문서 속성에 대 한 Microsoft Office 응용 프로그램 확인 합니다. 문서에 존재 하는 경우 응용 프로그램이 로드 된 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)], 사용자 지정을 시작 하는 합니다. 자세한 내용은 [Visual Studio에서 아키텍처의 Office 솔루션](../vsto/architecture-of-office-solutions-in-visual-studio.md)합니다.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

## <a name="assemblyname"></a>\_AssemblyName

이 속성의 Office 솔루션 로더 구성 요소에서 인터페이스의 CLSID가 포함 된 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]합니다. CLSID 값은 4E3C66D5-58 D 4-491E-A7D4-64AF99AF6E8B. 이 값을 변경 하지 해야 합니다.

## <a name="assemblylocation"></a>\_AssemblyLocation

이 속성을 사용자 지정에 대 한 배포 매니페스트에 대 한 세부 정보를 제공 하는 문자열을 포함 합니다. 매니페스트에 대 한 자세한 내용은 참조 하세요. [Office 솔루션에서 응용 프로그램 및 배포 매니페스트](../vsto/application-and-deployment-manifests-in-office-solutions.md)합니다.

 \_AssemblyLocation 속성 값에는 솔루션은 배포 하는 방법에 따라 서로 다른 형식으로 가질 수 있습니다.

- _AssemblyLocation 속성 형식은 솔루션으로 웹 사이트, UNC 경로 또는 USB 또는 CD 드라이브를 설치 하도록 게시 된 경우 *DeploymentManifestPath*|*solutionid 특성이 있으며,* 합니다. 다음 문자열 예제입니다.

     file://deployserver/MyShare/ExcelWorkbook1.vsto|74744e4b-e4d6-41eb-84f7-ad20346fe2d9

- _AssemblyLocation 속성 형식은 실행 하거나 Visual Studio에서 솔루션을 디버깅 하는 경우 *DeploymentManifestName*|*solutionid 특성이 있으며,*| vstolocal 합니다. 다음 문자열 예제입니다.

     ExcelWorkbook1.vsto|74744e4b-e4d6-41eb-84f7-ad20346fe2d9|vstolocal

  *solutionid 특성이 있으며,* guid는 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 솔루션 식별을 위해 사용 합니다. 합니다 *solutionid 특성이 있으며,* 프로젝트를 빌드할 때 자동으로 생성 됩니다. 합니다 **vstolocal** 용어를 나타냅니다는 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 문서와 동일한 폴더에서 어셈블리를 로드할 수 해야 합니다.

## <a name="see-also"></a>참고자료

- [Visual Studio에서 Office 솔루션의 아키텍처](../vsto/architecture-of-office-solutions-in-visual-studio.md)
- [문서 수준 사용자 지정 아키텍처](../vsto/architecture-of-document-level-customizations.md)
- [Office 솔루션에서 응용 프로그램 및 배포 매니페스트](../vsto/application-and-deployment-manifests-in-office-solutions.md)
- [방법: ClickOnce를 사용 하 여 Office 솔루션 게시](https://msdn.microsoft.com/2b6c247e-bc04-4ce4-bb64-c4e79bb3d5b8)
- [방법: 사용자 지정 문서 속성 만들기 및 수정](../vsto/how-to-create-and-modify-custom-document-properties.md)
