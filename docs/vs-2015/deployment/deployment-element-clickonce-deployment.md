---
title: '&lt;배포&gt; 요소 (ClickOnce 배포) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
f1_keywords:
- urn:schemas-microsoft-com:asm.v2#subscription
- urn:schemas-microsoft-com:asm.v2#beforeApplicationStartup
- urn:schemas-microsoft-com:asm.v2#deploymentProvider
- urn:schemas-microsoft-com:asm.v2#update
- urn:schemas-microsoft-com:asm.v2#deployment
- urn:schemas-microsoft-com:asm.v2#expiration
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <deployment> element [ClickOnce deployment manifest]
ms.assetid: 4fafa9c2-97a0-4cea-b8fd-9746dca33af4
caps.latest.revision: 32
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a55b5519d5abb7b40aeca23fed1bc2f8ea2cc33d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68194651"
---
# <a name="ltdeploymentgt-element-clickonce-deployment"></a>&lt;배포&gt; 요소 (ClickOnce 배포)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

업데이트를 배포하고 시스템에 노출하는 데 사용되는 특성을 식별합니다.  
  
## <a name="syntax"></a>구문  
  
```  
  
      <deployment   
   install  
   minimumRequiredVersion  
   mapFileExtensions  
   disallowUrlActivation  
   trustUrlParameters  
>   
   <subscription>   
         <update>   
            <beforeApplicationStartup/>   
            <expiration  
               maximumAge  
               unit  
            />  
         </update>    
   </subscription>   
   <deploymentProvider   
      codebase   
   />   
</deployment>  
```  
  
## <a name="elements-and-attributes"></a>요소 및 특성  
 `deployment` 요소는 필수이며 `urn:schemas-microsoft-com:asm.v1` 네임스페이스에 있습니다. 요소에는 다음 특성이 있습니다.  
  
|특성|설명|  
|---------------|-----------------|  
|`install`|필수 요소. Windows에서이 응용 프로그램 정의 하는지 여부를 지정 **시작** 메뉴와 제어판 **프로그램 추가 / 제거** 응용 프로그램입니다. 유효한 값은 `true` 및 `false`입니다. 하는 경우 `false`, [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 네트워크에서이 응용 프로그램의 최신 버전을 항상 실행 됩니다 및 인식 하지는 `subscription` 요소입니다.|  
|`minimumRequiredVersion`|선택 사항입니다. 클라이언트에서 실행할 수 있는이 응용 프로그램의 최소 버전을 지정 합니다. 응용 프로그램의 버전 번호를 배포 매니페스트에 지정 된 버전 번호 보다 작은 경우에 응용 프로그램이 실행 되지 않습니다. 버전 번호 형식으로 지정 해야 합니다 `N.N.N.N`여기서 `N` 는 부호 없는 정수입니다. 경우는 `install` 특성이 `false`, `minimumRequiredVersion` 설정 해서는 안 됩니다.|  
|`mapFileExtensions`|선택 사항입니다. 기본값은 `false`입니다. 경우 `true`, 배포의 모든 파일에.deploy 확장명이 있어야 합니다. [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 웹 서버에서 다운로드 하는 즉시이 확장명 이러한 파일을 제거 됩니다. 사용 하 여 응용 프로그램을 게시 하는 경우 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], 모든 파일에이 확장을 자동으로 추가 합니다. 이 매개 변수를 사용 하면 내 모든 파일이 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 배포.exe와 같은 "unsafe" 확장명으로 끝나는 파일의 전송을 차단 하는 웹 서버에서 다운로드 합니다.|  
|`disallowUrlActivation`|선택 사항입니다. 기본값은 `false`입니다. 경우 `true`, 설치 된 응용 프로그램 URL을 클릭 하거나 Internet Explorer에 URL을 입력 하 여 시작 하는 것을 방지 합니다. 경우는 `install` 특성이 있는,이 특성이 무시 됩니다.|  
|`trustURLParameters`|선택 사항입니다. 기본값은 `false`입니다. 경우 `true`응용 프로그램에 전달 되는 쿼리 문자열 매개 변수를 포함 하도록 URL을 사용 하면, 많은 like 명령줄 인수는 명령줄 응용 프로그램에 전달 됩니다. 자세한 내용은 [방법: 온라인 ClickOnce 애플리케이션에서 쿼리 문자열 정보 검색](../deployment/how-to-retrieve-query-string-information-in-an-online-clickonce-application.md)을 참조하세요.<br /><br /> 경우는 `disallowUrlActivation` 특성이 `true`를 `trustUrlParameters` 매니페스트에서 제외 이거나 명시적으로 설정 `false`합니다.|  
  
 `deployment` 다음 자식 요소를 포함 합니다.  
  
## <a name="subscription"></a>구독  
 선택 사항입니다. 포함 된 `update` 요소입니다. `subscription` 요소에는 특성이 없습니다. 경우는 `subscription` 요소가 없는 경우는 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 응용 프로그램 업데이트를 검색 하지 것입니다. 경우는 `install` 특성을 `deployment` 요소는 `false`, `subscription` 요소가 무시 하기 때문에 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 최신 버전을 사용 하는 네트워크에서 항상 실행 되는 응용 프로그램.  
  
## <a name="update"></a>업데이트  
 필수 요소. 이 요소는 자식 합니다 `subscription` 요소 중 하나를 포함 합니다 `beforeApplicationStartup` 또는 `expiration` 요소. `beforeApplicationStartup` 및 `expiration` 둘 다 같은 배포 매니페스트에서 지정할 수 없습니다.  
  
 `update` 요소에는 특성이 없습니다.  
  
## <a name="beforeapplicationstartup"></a>beforeApplicationStartup  
 선택 사항입니다. 이 요소는 자식은 `update` 요소 특성이 없습니다. 경우는 `beforeApplicationStartup` 요소가 있으면 응용 프로그램이 됩니다 때 차단 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 클라이언트 온라인 상태 이면 업데이트를 확인 합니다. 이 요소가 없으면 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 먼저 지정 된 값에 따라 업데이트 검색을 `expiration` 요소입니다. `beforeApplicationStartup` 및 `expiration` 둘 다 같은 배포 매니페스트에서 지정할 수 없습니다.  
  
## <a name="expiration"></a>만료  
 선택 사항입니다. 이 요소는 자식은 `update` 요소인 고 자식이 없습니다. `beforeApplicationStartup` 및 `expiration` 둘 다 같은 배포 매니페스트에서 지정할 수 없습니다. 업데이트 확인이 발생 하 고 업데이트 된 버전이 검색 될, 새 버전이 기존 버전을 실행 하는 동안 캐시 합니다. 새 버전의 다음 시작 시 다음 설치를 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 응용 프로그램입니다.  
  
 `expiration` 요소는 다음 특성을 지원 합니다.  
  
|특성|설명|  
|---------------|-----------------|  
|`maximumAge`|필수 요소. 얼마나 오래 된 현재 업데이트를 유지할 응용 프로그램 업데이트 확인을 수행 하기 전에 식별 합니다. 시간 단위에 의해 결정 됩니다는 `unit` 특성입니다.|  
|`unit`|필수 요소. 에 대 한 시간 단위를 식별 `maximumAge`합니다. 유효한 단위 `hours`, `days`, 및 `weeks`합니다.|  
  
## <a name="deploymentprovider"></a>deploymentProvider  
 .NET Framework 2.0의 경우이 요소는 필수 배포 매니페스트를 포함 하는 경우는 `subscription` 섹션입니다. .NET Framework 3.5 이상에서는이 요소는 선택 사항이 고 기본적으로 서버 및 배포 매니페스트 발견 하는 파일 경로.  
  
 이 요소는 `deployment` 요소의 자식이며 다음과 같은 특성이 있습니다.  
  
|특성|설명|  
|---------------|-----------------|  
|`codebase`|필수 요소. 위치를 식별,으로 리소스 URI (Uniform Identifier)를 업데이트 하는 데 사용 되는 배포 매니페스트는 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 응용 프로그램입니다. 이 요소는 CD 기반 설치에 대 한 업데이트 위치를 전달할 수도 있습니다. 유효한 URI 여야 합니다.|  
  
## <a name="remarks"></a>설명  
 구성할 수 있습니다 프로그램 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 시작 시에 업데이트를 검색 하려면 응용 프로그램 시작 후 업데이트를 검색 또는 업데이트 확인 안 함. 시작 시 업데이트를 검색 하려면 합니다 `beforeApplicationStartup` 요소가 아래는 `update` 요소입니다. 시작 후 업데이트를 검색 하려면 합니다 `expiration` 요소가 아래는 `update` 요소와 업데이트 간격을 지정 합니다.  
  
 업데이트 확인을 사용 하지 않으려면 제거는 `subscription` 요소입니다. 업데이트 검색 하지 않도록 하려면 배포 매니페스트를 지정 하면 확인할 수 있습니다 수동으로 업데이트를 사용 하 여를 <xref:System.Deployment.Application.ApplicationDeployment.CheckForUpdate%2A> 메서드.  
  
 DeploymentProvider 업데이트와 어떻게 관련 되는지에 대 한 자세한 내용은 참조 하세요. [ClickOnce 업데이트 전략 선택](../deployment/choosing-a-clickonce-update-strategy.md)합니다.  
  
## <a name="examples"></a>예  
 다음 코드 예제는 `deployment` 요소에는 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 배포 매니페스트 합니다. 이 예제에서는 사용을 `deploymentProvider` 기본 업데이트 위치를 나타내는 요소입니다.  
  
```  
<deployment install="true" minimumRequiredVersion="2.0.0.0" mapFileExtension="true" trustUrlParameters="true">  
    <subscription>  
      <update>  
        <expiration maximumAge="6" unit="hours" />  
      </update>  
    </subscription>  
    <deploymentProvider codebase="http://www.adatum.com/MyApplication.application" />  
  </deployment>  
```  
  
## <a name="see-also"></a>관련 항목  
 [ClickOnce 배포 매니페스트](../deployment/clickonce-deployment-manifest.md)
