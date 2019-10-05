---
title: '&lt;파일&gt; 요소 (ClickOnce 응용 프로그램) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
f1_keywords:
- http://www.w3.org/2000/09/xmldsig#Transform
- urn:schemas-microsoft-com:asm.v2#file
- http://www.w3.org/2000/09/xmldsig#DigestValue
- http://www.w3.org/2000/09/xmldsig#DigestMethod
- http://www.w3.org/2000/09/xmldsig#Transforms
- urn:schemas-microsoft-com:asm.v2#hash
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <file> element [ClickOnce application manifest]
- manifests [ClickOnce], file element
ms.assetid: 56e3490c-eed5-4841-b1bf-eefe778b6ac9
caps.latest.revision: 26
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 88fce548d5adbd6d4dc930db767fd3e52690490b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68148773"
---
# <a name="ltfilegt-element-clickonce-application"></a>&lt;파일&gt; 요소 (ClickOnce 응용 프로그램)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

다운로드 하 고 응용 프로그램에서 사용 하는 어셈블리 이외의 모든 파일을 식별 합니다.  
  
## <a name="syntax"></a>구문  
  
```  
<file  
    name  
    size  
    group  
    optional  
    writeableType  
>  
    <typelib  
        tlbid  
        version  
        helpdir  
        resourceid  
        flags  
    />  
    <comClass  
        clsid  
        description  
        threadingModel  
        tlbid  
        progid  
        miscStatus  
        miscStatusIcon  
        miscStatusContent  
        miscStatusDocPrint  
        miscStatusThumbnail  
    />  
    <comInterfaceExternalProxyStub  
        iid  
        baseInterface  
        numMethods  
        name  
        tlbid  
        proxyStubClass32  
    />  
    <comInterfaceProxyStub  
        iid  
        baseInterface  
        numMethods  
        name  
        tlbid  
        proxyStubClass32  
    />  
    <windowClass  
        versioned  
    />  
</file>  
```  
  
## <a name="elements-and-attributes"></a>요소 및 특성  
 `file` 요소는 선택적입니다. 요소에는 다음 특성이 있습니다.  
  
|특성|설명|  
|---------------|-----------------|  
|`name`|필수 요소. 파일의 이름을 식별합니다.|  
|`size`|필수 요소. 파일의 바이트에서 크기를 지정합니다.|  
|`group`|옵션에는 `optional` 특성은 지정 하지 않거나로 설정 하지 않습니다 `false`; 필요한 경우 `optional` 는 `true`합니다. 이 파일이 속한 그룹의 이름입니다. 이름, 개발자가 선택한 모든 유니코드 문자열 값일 수 있습니다 및 요청 시 파일 다운로드에 사용 되는 <xref:System.Deployment.Application.ApplicationDeployment> 클래스입니다.|  
|`optional`|선택 사항입니다. 이 파일은 응용 프로그램은 첫 번째 다운로드를 실행 또는 응용 프로그램이 필요에 따라 요청 될 때까지 파일 서버에만 상주 하는 여부를 지정 합니다. 경우 `false` 되거나 정의 되지 않은 파일은 다운로드 한 응용 프로그램은 처음 실행 하거나 설치 합니다. 하는 경우 `true`, `group` 유효 하도록 응용 프로그램 매니페스트를 지정 해야 합니다. `optional` true가 될 수 있으면 `writeableType` 값을 사용 하 여 지정 된 `applicationData`합니다.|  
|`writeableType`|선택 사항입니다. 이 파일을 데이터 파일 임을 지정 합니다. 현재 유효한 값은 `applicationData`뿐입니다.|  
  
## <a name="typelib"></a>typelib  
 `typelib` file 요소의 선택적 자식 요소입니다. 요소는 COM 구성 요소에 속하는 형식 라이브러리를 설명 합니다. 요소에는 다음 특성이 있습니다.  
  
|특성|설명|  
|---------------|-----------------|  
|`tlbid`|필수 요소. 형식 라이브러리에 할당 된 GUID입니다.|  
|`version`|필수 요소. 형식 라이브러리의 버전 번호입니다.|  
|`helpdir`|필수 요소. 구성 요소에 대 한 도움말 파일이 포함 된 디렉터리입니다. 길이가 0 인 수도 있습니다.|  
|`resourceid`|선택 사항입니다. 로캘 식별자 (LCID)의 16 진수 문자열 표현입니다. 0x 접두사를 앞에 오는 0 없이 16 진수를 1 ~ 4 개의 것입니다. LCID는 보조 중립 언어 식별자가 있을 수 있습니다.|  
|`flags`|선택 사항입니다. 이 형식 라이브러리에 대 한 형식 라이브러리 플래그의 문자열 표현입니다. 특히 "RESTRICTED", "컨트롤", "HIDDEN" 및 "HASDISKIMAGE" 중 하나 여야 합니다.|  
  
## <a name="comclass"></a>comClass  
 `comClass` 의 선택적 자식 요소입니다 합니다 `file` 요소인 하지만 필요한 경우는 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 등록-COM을 사용 하 여 배포 하려는 COM 구성 요소를 포함 하는 응용 프로그램 요소에는 다음 특성이 있습니다.  
  
|특성|설명|  
|---------------|-----------------|  
|`clsid`|필수 요소. 클래스의 ID는 GUID로 표시 하는 COM 구성 요소입니다.|  
|`description`|선택 사항입니다. 클래스 이름입니다.|  
|`threadingModel`|선택 사항입니다. In process COM 클래스에 의해 사용 되는 스레딩 모델입니다. 이 속성이 null 인 경우에 스레딩 모델이 사용 됩니다. 구성 요소는 클라이언트의 주 스레드에서 만들어지고이 스레드가 다른 스레드에서 호출 마샬링됩니다. 다음은 유효한 값을 보여 줍니다.<br /><br /> `Apartment`, `Free`, `Both`및 `Neutral`가 있습니다.|  
|`tlbid`|선택 사항입니다. 이 COM 구성 요소에 대 한 형식 라이브러리에 대 한 GUID입니다.|  
|`progid`|선택 사항입니다. COM 구성 요소와 연결 된 버전별 프로그래밍 식별자입니다. 형식의 `ProgID` 는 `<vendor>.<component>.<version>`합니다.|  
|`miscStatus`|선택 사항입니다. 어셈블리에 중복 매니페스트 제공 하는 정보는 `MiscStatus` 레지스트리 키입니다. 경우에 대 한 값을 `miscStatusIcon`, `miscStatusContent`, `miscStatusDocprint`, 또는 `miscStatusThumbnail` 특성을 찾을 수 없는, 해당 기본값에 나열 된 `miscStatus` 누락 된 특성에 사용 됩니다. 다음 표에서 특성 값의 쉼표로 구분 된 목록을 값일 수 있습니다. COM 클래스는 OCX 클래스에 필요한 경우이 특성을 사용할 수 있는 `MiscStatus` 레지스트리 키 값입니다.|  
|`miscStatusIcon`|선택 사항입니다. 어셈블리에 중복 매니페스트 DVASPECT_ICON 제공 하는 정보입니다. 개체의 아이콘을 제공할 수 있습니다. 다음 표에서 특성 값의 쉼표로 구분 된 목록을 값일 수 있습니다. COM 클래스는 OCX 클래스에 필요한 경우이 특성을 사용할 수 있는 `Miscstatus` 레지스트리 키 값입니다.|  
|`miscStatusContent`|선택 사항입니다. 어셈블리에 중복 매니페스트 DVASPECT_CONTENT 제공 하는 정보입니다. 표시할 수 있는 복합 문서 화면 또는 프린터에 대해 제공할 수 있습니다. 다음 표에서 특성 값의 쉼표로 구분 된 목록을 값일 수 있습니다. COM 클래스는 OCX 클래스에 필요한 경우이 특성을 사용할 수 있는 `MiscStatus` 레지스트리 키 값입니다.|  
|`miscStatusDocPrint`|선택 사항입니다. 어셈블리에 중복 매니페스트 DVASPECT_DOCPRINT 제공 하는 정보입니다. 프린터에 인쇄 하는 경우에 따라 화면에 표시할 수 있는 개체 표현을 제공할 수 있습니다. 다음 표에서 특성 값의 쉼표로 구분 된 목록을 값일 수 있습니다. COM 클래스는 OCX 클래스에 필요한 경우이 특성을 사용할 수 있는 `MiscStatus` 레지스트리 키 값입니다.|  
|`miscStatusThumbnail`|선택 사항입니다. 어셈블리에 중복 매니페스트 DVASPECT_THUMBNAIL 제공 하는 정보입니다. 검색 도구에 표시할 수 있는 개체의 미리 보기를 제공할 수 있습니다. 다음 표에서 특성 값의 쉼표로 구분 된 목록을 값일 수 있습니다. COM 클래스는 OCX 클래스에 필요한 경우이 특성을 사용할 수 있는 `MiscStatus` 레지스트리 키 값입니다.|  
  
## <a name="cominterfaceexternalproxystub"></a>comInterfaceExternalProxyStub  
 `comInterfaceExternalProxyStub` 의 선택적 자식 요소입니다 합니다 `file` 요소 이지만 경우에 필요할 수 있습니다는 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 등록-COM을 사용 하 여 배포 하려는 COM 구성 요소를 포함 하는 응용 프로그램 요소는 다음 특성을 포함 합니다.  
  
|특성|설명|  
|---------------|-----------------|  
|`iid`|필수 요소. ID (IID)이이 프록시에 의해 제공 되는 인터페이스입니다. IID에는 중괄호가 있어야 합니다.|  
|`baseInterface`|선택 사항입니다. 인터페이스에서 참조 된 인터페이스의 IID `iid` 파생 됩니다.|  
|`numMethods`|선택 사항입니다. 인터페이스를 구현한 방법의 수입니다.|  
|`name`|선택 사항입니다. 인터페이스의 이름을 코드에 표시 됩니다.|  
|`tlbid`|선택 사항입니다. 으로 지정한 인터페이스의 설명을 포함 하는 형식 라이브러리를 `iid` 특성입니다.|  
|`proxyStubClass32`|선택 사항입니다. 32 비트 프록시 Dll의에서 CLSID를 IID를 매핑합니다.|  
  
## <a name="cominterfaceproxystub"></a>comInterfaceProxyStub  
 `comInterfaceProxyStub` 의 선택적 자식 요소입니다 합니다 `file` 요소 이지만 경우에 필요할 수 있습니다는 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 등록-COM을 사용 하 여 배포 하려는 COM 구성 요소를 포함 하는 응용 프로그램 요소는 다음 특성을 포함 합니다.  
  
|특성|설명|  
|---------------|-----------------|  
|`iid`|필수 요소. ID (IID)이이 프록시에 의해 제공 되는 인터페이스입니다. IID에는 중괄호가 있어야 합니다.|  
|`baseInterface`|선택 사항입니다. 인터페이스에서 참조 된 인터페이스의 IID `iid` 파생 됩니다.|  
|`numMethods`|선택 사항입니다. 인터페이스를 구현한 방법의 수입니다.|  
|`Name`|선택 사항입니다. 인터페이스의 이름을 코드에 표시 됩니다.|  
|`Tlbid`|선택 사항입니다. 으로 지정한 인터페이스의 설명을 포함 하는 형식 라이브러리를 `iid` 특성입니다.|  
|`proxyStubClass32`|선택 사항입니다. 32 비트 프록시 Dll의에서 CLSID를 IID를 매핑합니다.|  
|`threadingModel`|선택 사항입니다. 선택 사항입니다. In process COM 클래스에 의해 사용 되는 스레딩 모델입니다. 이 속성이 null 인 경우에 스레딩 모델이 사용 됩니다. 구성 요소는 클라이언트의 주 스레드에서 만들어지고이 스레드가 다른 스레드에서 호출 마샬링됩니다. 다음은 유효한 값을 보여 줍니다.<br /><br /> `Apartment`, `Free`, `Both`및 `Neutral`가 있습니다.|  
  
## <a name="windowclass"></a>windowClass  
 `windowClass` 의 선택적 자식 요소입니다 합니다 `file` 요소 이지만 경우에 필요할 수 있습니다는 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 등록-COM을 사용 하 여 배포 하려는 COM 구성 요소를 포함 하는 응용 프로그램 요소에 적용 되는 버전을 포함 해야 하는 COM 구성 요소에 의해 정의 되는 창 클래스를 가리킵니다. 요소는 다음 특성을 포함 합니다.  
  
|특성|Description|  
|---------------|-----------------|  
|`versioned`|선택 사항입니다. 창 클래스를 포함 하는 어셈블리의 버전을 포함 여부는 내부 창 클래스 등록에 사용 되는 이름을 제어 합니다. 이 특성의 값이 될 수 있습니다 `yes` 또는 `no`합니다. 기본값은 `yes`입니다. 값 `no` side-by-side-구성 요소 및 해당 하는 비--side-by-side 구성 요소를 동일한 창 클래스 정의 되어 있고 동일한 창 클래스 동일 하 게 취급 하려는 경우에 사용 해야 합니다. 창 클래스 등록에 대한 일반적인 규칙이 적용됩니다. 창 클래스에 적용되는 버전이 없기 때문에 창 클래스를 등록하는 첫 번째 구성 요소만 해당 클래스를 등록할 수 있습니다.|  
  
## <a name="hash"></a>hash  
 합니다 `hash` 의 선택적 자식 요소입니다는 `file` 요소입니다. `hash` 요소에는 특성이 없습니다.  
  
 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 배포 후에 변경 된 파일이 없음을 확인 하기를 보안 검사는 응용 프로그램의 모든 파일의 해시를 알고리즘을 사용 합니다. 경우는 `hash` 요소가 포함 되지 않은,이 검사가 수행 되지 것입니다. 따라서 생략 된 `hash` 요소 권장 되지 않습니다.  
  
 해당 매니페스트 디지털 안 매니페스트 해시 되지 않은 파일에 있으면 해시 되지 않은 파일의 내용을 확인할 수 없습니다 때문에 서명 합니다.  
  
## <a name="dsigtransforms"></a>dsig:Transforms  
 합니다 `dsig:Transforms` 의 필수 자식 요소인는 `hash` 요소입니다. `dsig:Transforms` 요소에는 특성이 없습니다.  
  
## <a name="dsigtransform"></a>dsig:Transform  
 합니다 `dsig:Transform` 의 필수 자식 요소인는 `dsig:Transforms` 요소입니다. `dsig:Transform` 요소에는 다음 특성이 있습니다.  
  
|특성|Description|  
|---------------|-----------------|  
|`Algorithm`|이 파일에 대 한 다이제스트를 계산 하는 데 사용 된 알고리즘입니다. 사용 하는 유일한 값 현재 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 는 `urn:schemas-microsoft-com:HashTransforms.Identity`합니다.|  
  
## <a name="dsigdigestmethod"></a>dsig:DigestMethod  
 합니다 `dsig:DigestMethod` 의 필수 자식 요소인는 `hash` 요소입니다. `dsig:DigestMethod` 요소에는 다음 특성이 있습니다.  
  
|특성|Description|  
|---------------|-----------------|  
|`Algorithm`|이 파일에 대 한 다이제스트를 계산 하는 데 사용 된 알고리즘입니다. 사용 하는 유일한 값 현재 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 는 `http://www.w3.org/2000/09/xmldsig#sha1`합니다.|  
  
## <a name="dsigdigestvalue"></a>dsig:DigestValue  
 합니다 `dsig:DigestValue` 의 필수 자식 요소인는 `hash` 요소입니다. `dsig:DigestValue` 요소에는 특성이 없습니다. 요소의 텍스트 값은 지정된 된 파일에 대 한 계산 된 해시입니다.  
  
## <a name="remarks"></a>설명  
 이 요소는 응용 프로그램을 구성 하는 모든 어셈블리 이외의 파일을 식별 하 고 특히 파일 확인에 대 한 해시 값입니다. 이 요소는 파일에 연결 된 구성 요소 개체 모델 (COM) 격리 데이터를 포함할 수도 있습니다. 사용자가 파일을 변경 하는 경우 응용 프로그램 매니페스트 파일은 또한 변경 내용을 반영 하도록 업데이트 되어야 합니다.  
  
## <a name="example"></a>예제  
 다음 코드 예제를 보여 줍니다 `file` 응용 프로그램의 요소를 사용 하 여 배포 된 응용 프로그램에 대 한 매니페스트 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]합니다.  
  
```  
<file name="Icon.ico" size="9216">  
  <hash>  
    <dsig:Transforms>  
      <dsig:Transform Algorithm="urn:schemas-microsoft-com:HashTransforms.Identity" />  
    </dsig:Transforms>  
    <dsig:DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1" />  
    <dsig:DigestValue>lVoj+Rh6RQ/HPNLOdayQah5McrI=</dsig:DigestValue>  
  </hash>  
</file>  
```  
  
## <a name="see-also"></a>관련 항목  
 [ndptecclick](../deployment/clickonce-application-manifest.md)
