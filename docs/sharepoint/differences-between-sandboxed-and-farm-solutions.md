---
title: 차이점 샌드박스 솔루션과 팜 솔루션 | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
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
ms.openlocfilehash: 073e62b473ebfcec5f71ae1907e8f9e385333411
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62967548"
---
# <a name="differences-between-sandboxed-and-farm-solutions"></a>차이점 샌드박스 솔루션과 팜 솔루션
  SharePoint 솔루션을 컴파일할 때 SharePoint 서버에 배포 및 디버그 하는 디버거를 연결 합니다. 솔루션을 디버그 하는 데 사용 하는 프로세스를 샌드박스 솔루션 속성의 설정에 따라 달라 집니다: 샌드박스 솔루션 또는 팜 솔루션입니다.

 자세한 내용은 [샌드박스 솔루션 고려 사항](../sharepoint/sandboxed-solution-considerations.md)합니다.

## <a name="farm-solutions"></a>팜 솔루션
 IIS 작업자 프로세스 (W3WP.exe)에서 호스팅되는 팜 솔루션 전체 팜을 영향을 줄 수 있는 코드를 실행 합니다. 샌드박스 솔루션 속성이 "팜 솔루션"에 설정 된 SharePoint 프로젝트를 디버깅할 때 SharePoint을 제거 하거나 IIS 작업자 프로세스에 의해 잠긴 모든 파일을 해제 하기 위해 기능을 배포 하기 전에 시스템의 IIS 응용 프로그램 풀을 재활용 합니다. SharePoint 프로젝트의 사이트 URL 제공 IIS 응용 프로그램 풀 재활용 됩니다.

## <a name="sandboxed-solutions"></a>샌드박스 솔루션
 샌드박스 솔루션을 SharePoint 사용자 코드 솔루션 작업자 프로세스 (SPUCWorkerProcess.exe)에서 호스팅되는 솔루션의 사이트 모음에만 영향을 줄 수 있는 코드를 실행 합니다. 샌드박스 솔루션은 IIS 작업자 프로세스에서 실행 하지, IIS 응용 프로그램 풀도 아니고 IIS 서버 다시 시작 해야 합니다. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint에서 SPUserCodeV4 서비스가 자동으로 트리거하는 SPUCWorkerProcess 프로세스 및 컨트롤에 디버거를 연결 합니다. 솔루션의 최신 버전을 로드 하려고 재활용 SPUCWorkerProcess 프로세스에 대 한 필요는 없습니다.

## <a name="either-type-of-solution"></a>두 가지 형식의 솔루션
 두 가지 솔루션 형식 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 도 클라이언트 쪽 스크립트 디버깅을 사용 하려면 브라우저에 디버거를 연결 합니다. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 디버깅 엔진이이 목적을 위해 스크립트를 사용 합니다. 스크립트 디버깅을 사용 하려면 메시지가 표시 되 면 기본 브라우저 설정을 변경 해야 합니다.

 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 현재 사이트를 실행 중인 W3WP 또는 SPUCWorkerProcess 프로세스에만 디버거를 연결 합니다. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 또한 관리 되는 COM Plus 및 워크플로 디버깅 엔진을 연결 합니다.

## <a name="see-also"></a>참고자료
- [SharePoint 솔루션 디버깅](../sharepoint/debugging-sharepoint-solutions.md)
- [SharePoint 솔루션 빌드 및 디버그](../sharepoint/building-and-debugging-sharepoint-solutions.md)
- [샌드박스 솔루션 고려 사항](../sharepoint/sandboxed-solution-considerations.md)
