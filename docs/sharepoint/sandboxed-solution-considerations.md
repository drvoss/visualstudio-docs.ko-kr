---
title: 샌드박스 솔루션 고려 사항 | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.Project.SandboxedSolutions
- VS.SharePointTools.Security.SandboxedSolutions
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, sandboxed solutions
- sandboxed solutions [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, farm solutions
- farm solutions [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 3f6345e7627549c672aa28fac8cba5f6d9658a23
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63435441"
---
# <a name="sandboxed-solution-considerations"></a>샌드박스 솔루션 고려 사항
  *샌드박스 솔루션* 는 사이트 컬렉션 사용자가 자신의 사용자 지정 코드 솔루션을 업로드할 수 있도록 Microsoft SharePoint 2010의 기능입니다. 일반적인 샌드박스가 적용 된 솔루션은 사용자가 자신의 웹 파트를 업로드 합니다.

 샌드박스 SharePoint 응용 프로그램을 웹 팜의 제한 된 부분에 액세스할 수 있는 안전 하 고 모니터링 대상 프로세스에서 실행 됩니다. Microsoft SharePoint 2010 기능, 솔루션 갤러리, 모니터링, 솔루션 및 유효성 검사 프레임 워크의 조합을 사용 하 여 샌드박스 솔루션을 사용 하도록 설정.

## <a name="specify-project-trust-level"></a>프로젝트 신뢰 수준을 지정 합니다.
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 라고 하는 부울 프로젝트 속성을 통해 샌드 박싱된 솔루션 지원 *샌드박스 솔루션*합니다. 언제 든 지 프로젝트에서이 속성을 설정할 수 있습니다 또는에서 프로젝트를 만들 때 지정할 수 있습니다 합니다 **SharePoint 사용자 지정 마법사**합니다.

> [!NOTE]
> 변경 된 *샌드박스 솔루션* 만들어진 후 프로젝트의 속성 유효성 검사 오류가 발생할 수 있습니다.

 솔루션은 팜 범위 솔루션이 것으로 간주 됩니다는 *샌드박스 솔루션* 속성이로 설정 되어 **false** 선택 하면 또는 **팜 솔루션으로 배포** 옵션. 그러나 솔루션은 다르게 처리 팜 솔루션의 경우는 *샌드박스 솔루션* 속성이 **true** 선택 하면 또는 **샌드박스 솔루션으로 배포** 마법사의 옵션입니다.

## <a name="sharepoint-site-hierarchy"></a>SharePoint 사이트 계층 구조
 어떻게 샌드박스 솔루션을 이해 하려면 작업을 수 있도록 SharePoint 사이트는 계층적 범위 인지 알고 있어야 합니다. 맨 위에 있는 요소 웹 팜의 이라고 하며 다른 요소에 종속 됩니다.

 웹 팜

 웹 응용 프로그램 A

 사이트 컬렉션 A1

 사이트 A1a

 웹 응용 프로그램 B

 사이트 컬렉션 B1

 사이트 B1a

 사이트 B1b

 사이트 컬렉션 B2

 사이트 B2a

 알 수 있듯이 웹 팜에서 하나 이상의 웹 응용 프로그램에 하위 사이트 수 있고 등 하는 하나 이상의 사이트 컬렉션을 포함할 수 있는 포함할 수 있습니다. 다른 및 한 사이트 컬렉션에 영향을 해당 사이트 컬렉션을 변경 합니다. 그러나 웹 팜 수준에서 변경 팜의 모든 사이트 모음을 영향을 줍니다.

 Windows SharePoint Services (WSS) 3.0을 사용 하면 팜 수준에만 솔루션을 배포할 수 있습니다 하지만 [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] 팜 수준 (팜 솔루션) 또는 사이트 모음 수준 (샌드박스 솔루션) 배포할 수 있습니다.

## <a name="why-sandboxed-solutions"></a>이유는 샌드박스 솔루션?
 WSS 3.0에는 팜 수준에만 솔루션을 배포할 수 있었습니다. 이 잠재적으로 유해한 불안정 솔루션 배포할 수는 전체 웹 팜 및 다른 사이트 모음 및 그 아래에서 실행 되는 응용 프로그램의 모든 받는 것을 의미 합니다. 그러나 샌드박스 솔루션을 사용 하 여 팜의 특정 사이트 모음을 하위 영역에 솔루션을 배포할 수 있습니다. 추가 보호를 제공 하기는 솔루션의 어셈블리는 기본 로드 [!INCLUDE[TLA2#tla_iis5](../sharepoint/includes/tla2sharptla-iis5-md.md)] 프로세스 (*w3wp.exe*). 대신, 별도 프로세스로 로드 됩니다 (*SPUCWorkerProcess.exe*). 이 프로세스를 모니터링 하 고 할당량 및 제한 팜을 보호 하기 위해 CPU 사이클을 소비 하는 타이트 루프를 실행 하는 등 위험한 동작을 수행 하는 샌드박스 솔루션에서를 구현 합니다.

## <a name="site-collection-solution-gallery"></a>사이트 컬렉션 솔루션 갤러리
 [!INCLUDE[sharepointShort](../sharepoint/includes/sharepointshort-md.md)] 2010에는 "사이트 컬렉션 솔루션 갤러리"라는 기능이 있습니다. 열어 또는 SharePoint 2010 중앙 관리 페이지에서이 기능에 액세스할 수 있습니다 합니다 **사이트 작업** 메뉴에서 선택 **사이트 설정**를 선택한 후는 **솔루션** 링크 **갤러리** SharePoint 사이트에서. 솔루션 갤러리는 해당 사이트 컬렉션에서 솔루션을 관리 하려면 사이트 모음 관리자를 사용 하도록 설정 하는 솔루션의 리포지토리입니다.

 솔루션 갤러리는 SharePoint 사이트의 웹 루트에 저장 된 문서 라이브러리입니다. 솔루션 갤러리 사이트 템플릿을 대체 하 고 솔루션 패키지를 지원 합니다. 경우는 SharePoint 솔루션 패키지 (*.wsp*) 파일을 업로드, 샌드박스 솔루션으로 처리 됩니다.

## <a name="sandboxed-solution-limitations"></a>샌드박스 솔루션의 제한 사항
 샌드박스 솔루션을 배포 하면 SharePoint 기능을 사용할 수 있는 배열의 있을 보안 취약점을 줄이는 데 도움이 제한 됩니다. 이러한 제한 중 일부는 다음과 같습니다.

- 샌드박스 솔루션 배포 가능한 솔루션 요소에 사용 가능한 제한 된 하위 집합을 포함 합니다. 사이트 정의 워크플로 등의 잠재적으로 취약 한 SharePoint 프로젝트 템플릿은 제공 되지 않습니다.

- 프로세스에서 샌드박스 솔루션 코드를 실행 하는 SharePoint (*SPUCWorkerProcess.exe*) 주 별도로 [!INCLUDE[TLA2#tla_iis5](../sharepoint/includes/tla2sharptla-iis5-md.md)] 응용 프로그램 풀 (*w3wp.exe*) 프로세스입니다.

- 프로젝트에 매핑된 폴더를 추가할 수 없습니다.

- 형식은 [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] 어셈블리 Microsoft.Office.Server 샌드박스 솔루션에서 사용할 수 없습니다. 또한의 형식만 [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] 어셈블리 Microsoft.SharePoint 샌드박스 솔루션에서 사용할 수 있습니다.

  지정 하면 SharePoint 솔루션을 SharePoint 서버에 영향을 미치지 않습니다를 샌드박스 솔루션으로 반드시 SharePoint 프로젝트에서 SharePoint에 배포 되는 방식을 결정만 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 어떤 어셈블리에 바인딩합니다. 생성 된 변경 되지 않습니다 *.wsp* 파일 및 *.wsp* 파일에 직접 상관 관계에 있는 데이터가 없습니다. 합니다 *샌드박스 솔루션* 속성입니다.

## <a name="capabilities-and-elements-in-sandboxed-solutions"></a>샌드박스 솔루션의 기능 및 요소
 샌드박스 솔루션은 다음 기능과 요소를 지원합니다.

- 콘텐츠 형식/필드

- 사용자 지정 작업

- 선언적 워크플로

- 이벤트 수신자

- 기능 설명선

- 목록 정의

- 목록 인스턴스

- 모듈/파일

- 탐색

- *Onet.xml*

- SPItemEventReceiver

- SPListEventReceiver

- SPWebEventReceiver

- 파생 되는 모든 웹 파트에 대 한 지원 `System.Web.UI.WebControls.WebParts.WebPart`

- 웹 파트

- 기능 요소 웹 서식 파일 (대신 *Webtemp.xml*)

- 비주얼 웹 파트

  샌드박스 솔루션은 다음 기능과 요소를 지원 하지 않습니다.

- 응용 프로그램 페이지

- 사용자 지정 작업 그룹

- 팜 범위 기능

- `HideCustomAction` 요소

- 웹 응용 프로그램 범위 기능

- 코드를 사용 하 여 워크플로

## <a name="see-also"></a>참고자료
- [차이점 샌드박스 솔루션과 팜 솔루션](../sharepoint/differences-between-sandboxed-and-farm-solutions.md)
- [SharePoint 솔루션 개발](../sharepoint/developing-sharepoint-solutions.md)
