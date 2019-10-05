---
title: ClickOnce 관리 되지 않는 API 참조 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- LaunchApplication [ClickOnce unmanaged]
- ClickOnce, unmanaged APIs
- CleanOnlineAppCache [ClickOnce unmanaged]
- CleanOnlineAppCacheW interface [ClickOnce unmanaged]
- GetDeploymentDataFromManifest [ClickOnce unmanaged]
ms.assetid: ec002138-4054-456d-bcc1-79ac2f4a4fd7
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 714d7b18995bf1ad51b07e02227e440879f73c9e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68192314"
---
# <a name="clickonce-unmanaged-api-reference"></a>ClickOnce 관리되지 않는 API 참조
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 관리 되지 않는 dfshim.dll에서 Api를 공개 합니다.  
  
## <a name="cleanonlineappcache"></a>CleanOnlineAppCache  
 모든 온라인 응용 프로그램 제거 또는 정리를 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 응용 프로그램 캐시 합니다.  
  
### <a name="return-value"></a>반환 값  
 성공 하면 S_OK를 반환 합니다. 그렇지 않으면 실패를 나타내는 HRESULT를 반환 합니다. 관리 되는 예외를 발생 하는 경우 0x80020009 (DISP_E_EXCEPTION)를 반환 합니다.  
  
### <a name="remarks"></a>설명  
 CleanOnlineAppCache 호출 시작 된 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 아직 실행 하지 않은 경우 서비스입니다.  
  
## <a name="getdeploymentdatafrommanifest"></a>GetDeploymentDataFromManifest  
 매니페스트 및 활성화 URL에서 배포 정보를 검색합니다.  
  
### <a name="parameters"></a>매개 변수  
  
|매개 변수|설명|형식|  
|---------------|-----------------|----------|  
|`pcwzActivationUrl`|에 대 한 포인터를 `ActivationURL`입니다.|LPCWSTR|  
|`pcwzPathToDeploymentManifest`|에 대 한 포인터를 `PathToDeploymentManifest`입니다.|LPCWSTR|  
|`pwzApplicationIdentity`|반환 되는 전체 응용 프로그램 id를 지정 하는 NULL로 끝나는 문자열을 받기 위한 버퍼에 대 한 포인터입니다.|LPWSTR|  
|`pdwIdentityBufferLength`|길이가 DWORD에 대 한 포인터를 `pwzApplicationIdentity` WCHARs 버퍼입니다. NULL 종료 문자에 대 한 공간을 포함합니다.|LPDWORD|  
|`pwzProcessorArchitecture`|응용 프로그램 배포 매니페스트에서 프로세서 아키텍처를 지정 하는 NULL로 끝나는 문자열을 받기 위한 버퍼에 대 한 포인터입니다.|LPWSTR|  
|`pdwArchitectureBufferLength`|길이가 DWORD에 대 한 포인터를 `pwzProcessorArchitecture` WCHARs 버퍼입니다.|LPDWORD|  
|`pwzApplicationManifestCodebase`|응용 프로그램 매니페스트의 매니페스트에서 코드 베이스를 지정 하는 NULL로 끝나는 문자열을 받기 위한 버퍼에 대 한 포인터입니다.|LPWSTR|  
|`pdwCodebaseBufferLength`|길이가 DWORD에 대 한 포인터를 `pwzApplicationManifestCodebase` WCHARs 버퍼입니다.|LPDWORD|  
|`pwzDeploymentProvider`|NULL로 끝나는 문자열을 받기 위한 버퍼에 대 한 포인터 공급자를 지정 하는 배포 매니페스트에서 있는 경우. 그렇지 않은 경우 빈 문자열이 반환 됩니다.|LPWSTR|  
|`pdwProviderBufferLength`|길이가 DWORD에 대 한 포인터를 `pwzProviderBufferLength`입니다.|LPDWORD|  
  
### <a name="return-value"></a>반환 값  
 성공 하면 S_OK를 반환 합니다. 그렇지 않으면 실패를 나타내는 HRESULT를 반환 합니다. 버퍼가 너무 작은 경우 HRESULTFROMWIN32(ERROR_INSUFFICIENT_BUFFER)를 반환 합니다.  
  
### <a name="remarks"></a>설명  
 포인터를 null 이어야 합니다. `pcwzActivationUrl` 및 `pcwzPathToDeploymentManifest` 비어 있지 않아야 합니다.  
  
 활성화 URL을 정리 해야 하는 호출자의 경우 예를 들어, 이스케이프 문자를 추가 필요한 위치 또는 쿼리 문자열을 제거 합니다.  
  
 것은 입력된 길이 제한 하는 호출자의 책임입니다. 예를 들어 최대 URL 길이 2입니다.  
  
## <a name="launchapplication"></a>LaunchApplication  
 시작 하거나 배포 URL을 사용 하 여 응용 프로그램을 설치 합니다.  
  
### <a name="parameters"></a>매개 변수  
  
|매개 변수|Description|형식|  
|---------------|-----------------|----------|  
|`deploymentUrl`|배포 매니페스트의 URL이 포함 된 NULL로 끝나는 문자열에 대 한 포인터입니다.|LPCWSTR|  
|`data`|나중에 사용하도록 예약되어 있습니다. Null이어야 합니다.|LPVOID|  
|`flags`|나중에 사용하도록 예약되어 있습니다. 0이어야 합니다.|DWORD|  
  
### <a name="return-value"></a>반환 값  
 성공 하면 S_OK를 반환 합니다. 그렇지 않으면 실패를 나타내는 HRESULT를 반환 합니다. 관리 되는 예외를 발생 하는 경우 0x80020009 (DISP_E_EXCEPTION)를 반환 합니다.  
  
## <a name="see-also"></a>참고 항목  
 <xref:System.Deployment.Application.DeploymentServiceCom.CleanOnlineAppCache%2A>
