---
title: ClickOnce 캐시 개요 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- Windows applications, ClickOnce deployemtn
- ClickOnce applications, cache
- ClickOnce deployment, cache
ms.assetid: e379921e-9ef1-4326-bbf3-53ba67925526
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 58ea758ea10e2c58ff123a2bc991f14191db0aa1
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68151662"
---
# <a name="clickonce-cache-overview"></a>ClickOnce 캐시 개요
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

모든 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 응용 프로그램을 로컬로 설치 인지 온라인 호스팅 저장 되는지 여부를 클라이언트 컴퓨터에 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]응용 프로그램 *캐시*합니다. [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 캐시는 현재 사용자의 Documents and Settings 폴더의 로컬 설정 디렉터리 아래에 숨겨진된 디렉터리의 집합입니다. 이 캐시에 어셈블리, 구성 파일, 응용 프로그램 및 사용자 설정 및 데이터 디렉터리를 포함 하 여 응용 프로그램의 모든 파일을 포함 합니다. 캐시는 응용 프로그램의 데이터 디렉터리를 최신 버전으로 마이그레이션하는 데 이기도 합니다. 데이터 마이그레이션에 대 한 자세한 내용은 참조 하세요. [로컬 및 ClickOnce 응용 프로그램의 원격 데이터 액세스](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md)합니다.  
  
 응용 프로그램 저장소에 대 한 단일 위치를 제공 하 여 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 사용자의 응용 프로그램의 실제 설치 관리 작업을 맡습니다. 캐시 하기도 어셈블리 및 모든 응용 프로그램에 대 한 데이터 파일을 유지 하 여 응용 프로그램을 격리 하 고 해당 고유 버전을 서로 구분 합니다. 예를 들어, 업그레이드 하는 경우는 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 응용 프로그램을 자체 캐시 디렉터리를 사용 하 여 버전 및 해당 데이터 리소스가 제공 됩니다.  
  
## <a name="cache-storage-quota"></a>캐시 저장소 할당량  
 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 온라인에 호스트 되는 응용 프로그램의 크기를 제한 하는 할당량으로 공간을 차지할 수 제한 됩니다는 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 캐시 합니다. 캐시 크기를 모든 사용자의 온라인 응용 프로그램에 적용 됩니다. 단일 부분적으로 신뢰할 수 있는, 온라인 응용 프로그램을 차지 하는 할당량 공간의 절반으로 제한 됩니다. 설치 된 응용 프로그램 캐시 크기에 따라 제한 되지 않습니다 및 캐시 제한에 포함 되지 않습니다. 모든 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 이전에 설치 된 버전과 현재 버전만 응용 프로그램의 경우 캐시를 유지 합니다.  
  
 클라이언트 컴퓨터 기본적으로 저장소의 크기가 250mb 온라인에 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 응용 프로그램입니다. 데이터 파일은이 제한에 대해 계산 되지 않습니다. 시스템 관리자를 확대 하거나 레지스트리 키 DWORD 값인 HKEY_CURRENT_USER\Software\Classes\Software\Microsoft\Windows\CurrentVersion\Deployment\OnlineAppQuotaInKB를 변경 하 여 특정 클라이언트 컴퓨터에이 할당량을 줄일 수 있습니다. 킬로바이트의 캐시 크기를 표현합니다. 예를 들어 캐시 크기를 50MB 줄이려면 51200에이 값을 변경할는 있습니다.  
  
## <a name="see-also"></a>참고 항목  
 [ClickOnce 응용 프로그램의 로컬 및 원격 데이터 액세스](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md)
