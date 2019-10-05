---
title: '&lt;종속성&gt; 요소 (ClickOnce 배포) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
f1_keywords:
- urn:schemas-microsoft-com:asm.v2#osVersionInfo
- urn:schemas-microsoft-com:asm.v2#os
- http://www.w3.org/2000/09/xmldsig#Transform
- urn:schemas-microsoft-com:asm.v2#dependency
- http://www.w3.org/2000/09/xmldsig#DigestValue
- urn:schemas-microsoft-com:asm.v2#assemblyIdentity
- http://www.w3.org/2000/09/xmldsig#DigestMethod
- http://www.w3.org/2000/09/xmldsig#Transforms
- urn:schemas-microsoft-com:asm.v2#hash
- urn:schemas-microsoft-com:asm.v2#dependentAssembly
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <dependency> element [ClickOnce deployment manifest]
ms.assetid: 9b4d2082-0347-4922-ac70-85f11b913039
caps.latest.revision: 29
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f191b11dfce5b3877d0a31e260e092000a556a5a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68187778"
---
# <a name="ltdependencygt-element-clickonce-deployment"></a>&lt;종속성&gt; 요소 (ClickOnce 배포)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

를 설치 하려면 응용 프로그램의 버전 및 응용 프로그램 매니페스트의 위치를 식별 합니다.  
  
## <a name="syntax"></a>구문  
  
```  
  
      <dependency>   
   <dependentAssembly  
      preRequisite  
      visible  
      dependencyType  
      codeBase  
      size  
   >   
      <assemblyIdentity   
         name   
         version   
         publicKeyToken   
         processorArchitecture   
         language  
         type  
      />   
      <hash>  
         <dsig:Transforms>  
            <dsig:Transform  
                Algorithm  
            />  
         </dsig:Transforms>  
         <dsig:DigestMethod />  
         <dsig:DigestValue>  
         </dsig:DigestValue>  
      </hash>  
  
   </dependentAssembly>   
</dependency>  
```  
  
## <a name="elements-and-attributes"></a>요소 및 특성  
 `dependency` 요소는 필수입니다. 특성이 없습니다. 배포 매니페스트는 여러 개 있을 수 `dependency` 요소입니다.  
  
 `dependency` 요소 내에 포함 된 어셈블리에 기본 응용 프로그램에 대 한 종속성을 일반적으로 표현 된 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 응용 프로그램입니다. Main.exe 응용 프로그램 DotNetAssembly.dll 이라는 어셈블리를 사용 하는 경우 해당 어셈블리 종속성 섹션에 나열 되어야 합니다. 그러나 종속성은 전역 어셈블리 캐시 (GAC)에 어셈블리 또는 COM 개체에는 다른 유형의 종속성을 특정 버전의 공용 언어 런타임, 종속성 등를 표현할 수도 있습니다. 자동 배포 기술을 이므로 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 시작 다운로드 및 설치 종속성 하지만 이러한 유형의 않습니다를 막을 수 없습니다 실행에서 응용 프로그램에서 지정 된 종속성을 하나 이상 존재 하지 않는 경우.  
  
## <a name="dependentassembly"></a>dependentAssembly  
 필수 요소. 이 요소에 포함 된 `assemblyIdentity` 요소입니다. 다음 표에서 특성을 보여 줍니다.는 `dependentAssembly` 지원 합니다.  
  
|특성|Description|  
|---------------|-----------------|  
|`preRequisite`|선택 사항입니다. 이 어셈블리는 GAC에 이미 지정 합니다. 유효한 값은 `true` 및 `false`입니다. 경우 `true`, 지정된 된 어셈블리를 GAC에 없는 경우, 응용 프로그램을 실행 하지 못함.|  
|`visible`|선택 사항입니다. 해당 종속성을 포함 하 여 최상위 응용 프로그램 id를 식별 합니다. 내부적으로 사용 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 응용 프로그램 저장소 및 정품 인증을 관리 합니다.|  
|`dependencyType`|필수 요소. 이 종속성 및 응용 프로그램 간의 관계입니다. 유효한 값은<br /><br /> -   `install`. 구성 요소에는 현재 응용 프로그램에서 별도 설치를 나타냅니다.<br />-   `preRequisite`. 현재 응용 프로그램 구성 요소에 필요 합니다.|  
|`codebase`|선택 사항입니다. 응용 프로그램 매니페스트의 전체 경로입니다.|  
|`size`|선택 사항입니다. 크기 (바이트)를 사용 하는 응용 프로그램 매니페스트를입니다.|  
  
## <a name="assemblyidentity"></a>assemblyIdentity  
 필수 요소. 이 요소는 `dependentAssembly` 요소의 자식입니다. 내용의 `assemblyIdentity` 에 설명 된 대로 동일 해야 합니다 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 응용 프로그램 매니페스트 합니다. 다음 표에서 특성을 `assemblyIdentity` 요소입니다.  
  
|특성|설명|  
|---------------|-----------------|  
|`Name`|필수 요소. 응용 프로그램의 이름을 식별합니다.|  
|`Version`|필수 요소. 다음 형식으로 응용 프로그램의 버전 번호를 지정합니다. `major.minor.build.revision`|  
|`publicKeyToken`|필수 요소. 응용 프로그램이 나 어셈블리 서명에 사용 된 공개 키의 sha-1 해시의 마지막 8 바이트를 나타내는 16 자리의 16 진수 문자열을 지정 합니다. 로그인에 사용 된 공개 키 2048 비트 해야 합니다. 이상.|  
|`processorArchitecture`|필수 요소. 마이크로프로세서를 지정합니다. 유효한 값은 `x86` 32 비트 Windows에 대 한 및 `IA64` 64 비트 Windows에 대 한 합니다.|  
|`Language`|선택 사항입니다. 어셈블리의 두 부분 언어 코드를 식별합니다. 예를 들어, EN-US는 영어 (미국)에 대 한 합니다. 기본값은 `neutral`입니다. 이 요소는 여 `asmv2` 네임 스페이스입니다.|  
|`type`|선택 사항입니다. 이전 버전과 호환성 Windows-side-by-side를 사용 하 여 설치 기술에 대 한 합니다. 허용 된 값만 `win32`합니다.|  
  
## <a name="hash"></a>hash  
 합니다 `hash` 의 선택적 자식 요소입니다는 `file` 요소입니다. `hash` 요소에는 특성이 없습니다.  
  
 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 배포 후에 변경 된 파일이 없음을 확인 하기를 보안 검사는 응용 프로그램의 모든 파일의 해시를 알고리즘을 사용 합니다. 경우는 `hash` 요소가 포함 되지 않은,이 검사가 수행 되지 것입니다. 따라서 생략 된 `hash` 요소 권장 되지 않습니다.  
  
## <a name="dsigtransforms"></a>dsig:Transforms  
 합니다 `dsig:Transforms` 의 필수 자식 요소인는 `hash` 요소입니다. `dsig:Transforms` 요소에는 특성이 없습니다.  
  
## <a name="dsigtransform"></a>dsig:Transform  
 합니다 `dsig:Transform` 의 필수 자식 요소인는 `dsig:Transforms` 요소입니다. 다음 표에서 특성을 `dsig:Transform` 요소입니다.  
  
|특성|Description|  
|---------------|-----------------|  
|`Algorithm`|이 파일에 대 한 다이제스트를 계산 하는 데 사용 된 알고리즘입니다. 사용 하는 유일한 값 현재 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 는 `urn:schemas-microsoft-com:HashTransforms.Identity`합니다.|  
  
## <a name="dsigdigestmethod"></a>dsig:DigestMethod  
 합니다 `dsig:DigestMethod` 의 필수 자식 요소인는 `hash` 요소입니다. 다음 표에서 특성을 `dsig:DigestMethod` 요소입니다.  
  
|특성|Description|  
|---------------|-----------------|  
|`Algorithm`|이 파일에 대 한 다이제스트를 계산 하는 데 사용 된 알고리즘입니다. 사용 하는 유일한 값 현재 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 는 `http://www.w3.org/2000/09/xmldsig#sha1`합니다.|  
  
## <a name="dsigdigestvalue"></a>dsig:DigestValue  
 합니다 `dsig:DigestValue` 의 필수 자식 요소인는 `hash` 요소입니다. `dsig:DigestValue` 요소에는 특성이 없습니다. 요소의 텍스트 값은 지정된 된 파일에 대 한 계산 된 해시입니다.  
  
## <a name="remarks"></a>설명  
 배포 매니페스트는 일반적으로 단일 있습니다 `assemblyIdentity` 이름과 응용 프로그램 매니페스트 버전을 식별 하는 요소입니다.  
  
## <a name="example"></a>예제  
 다음 코드 예제는 `dependency` 요소에는 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 배포 매니페스트 합니다.  
  
```  
<!-- Identify the assembly dependencies -->  
<dependency>  
  <dependentAssembly dependencyType="install" allowDelayedBinding="true" codebase="MyApplication.exe" size="16384">  
    <assemblyIdentity name="MyApplication" version="0.0.0.0" cultural="neutral" processorArchitecture="msil" />  
    <hash>  
      <dsig:Transforms>  
        <dsig:Transform Algorithm="urn:schemas-microsoft-com:HashTransforms.Identity" />  
      </dsig:Transforms>  
      <dsig:DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1" />  
       <dsig:DigestValue>YzXYZJAvj9pgAG3y8jXUjC7AtHg=</dsig:DigestValue>  
    </hash>  
  </dependentAssembly>  
</dependency>  
```  
  
## <a name="example"></a>예제  
 다음 코드 예제는 GAC에 이미 설치 된 어셈블리에 종속성을 지정 합니다.  
  
```  
<dependency>  
  <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true">  
    <assemblyIdentity name="GACAssembly" version="1.0.0.0" language="neutral" processorArchitecture="msil" />  
  </dependentAssembly>  
</dependency>  
```  
  
## <a name="example"></a>예제  
 다음 코드 예제는 특정 버전의 공용 언어 런타임 종속성을 지정합니다.  
  
```  
<dependency>  
  <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true">  
    <assemblyIdentity name="Microsoft.Windows.CommonLanguageRuntime" version="2.0.50215.0" />  
  </dependentAssembly>  
</dependency>  
```  
  
## <a name="example"></a>예제  
 다음 코드 예제에는 운영 체제 종속성을 지정합니다.  
  
```  
<dependency>  
   <dependentOS supportUrl="http://www.microsoft.com" description="Microsoft Windows Operating System">  
      <osVersionInfo>  
         <os majorVersion="4" minorVersion="10" />  
      </osVersionInfo>  
   </dependentOS>  
</dependency>  
```  
  
## <a name="see-also"></a>관련 항목  
 [ClickOnce 배포 매니페스트](../deployment/clickonce-deployment-manifest.md)   
 [\<dependency> 요소](../deployment/dependency-element-clickonce-application.md)
