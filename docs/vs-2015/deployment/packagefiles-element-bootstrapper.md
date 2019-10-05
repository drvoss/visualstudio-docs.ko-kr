---
title: '&lt;PackageFiles&gt; 요소 (부트스트래퍼) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- <PackageFiles> element [bootstrapper]
ms.assetid: 3ea252d7-18a3-47d8-af83-47feebcfe82b
caps.latest.revision: 18
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 382689dada13adce1ee530e66fef6ba78452efaa
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68188977"
---
# <a name="ltpackagefilesgt-element-bootstrapper"></a>&lt;PackageFiles&gt; 요소 (부트스트래퍼)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

합니다 `PackageFiles` 요소에 포함 되어 `PackageFile` 의 결과로 실행 설치 패키지를 정의 하는 요소는 `Command` 요소입니다.  
  
## <a name="syntax"></a>구문  
  
```  
<PackageFiles  
    CopyAllPackageFiles  
>  
    <PackageFile   
        Name  
        HomeSite  
        CopyOnBuild  
        PublicKey  
        Hash  
    />  
</PackageFiles>  
```  
  
## <a name="elements-and-attributes"></a>요소 및 특성  
 `PackageFiles` 요소에는 다음 특성이 있습니다.  
  
|특성|Description|  
|---------------|-----------------|  
|`CopyAllPackageFiles`|선택 사항입니다. 경우로 `false`, 설치 관리자에서 참조 하는 파일을 다운로드만 `Command` 요소입니다. 경우 설정 `true`, 모든 파일이 다운로드 됩니다.<br /><br /> 경우로 `IfNotHomesite`, 설치 관리자는 동일 하 게 처럼 `False` 경우 `ComponentsLocation` 로 설정 되어 `HomeSite`, 그렇지 않으면 동일 하 게 동작 합니다 및 처럼 `True`. 이 설정은 HomeSite 시나리오에서 고유한 동작을 실행 하는 부트스트래퍼 패키지를 허용 하도록 유용할 수 있습니다.<br /><br /> 기본값은 `true`입니다.|  
  
## <a name="packagefile"></a>PackageFile  
 합니다 `PackageFile` 요소인 자식은 `PackageFiles` 요소입니다. A `PackageFiles` 요소 하나 이상이 있어야 `PackageFile` 요소입니다.  
  
 `PackageFile` 다음과 같은 특성이 있습니다.  
  
|특성|설명|  
|---------------|-----------------|  
|`Name`|필수 요소. 패키지 파일의 이름입니다. 이 이름은는 `Command` 요소는 패키지를 설치 하는 조건을 정의 될 때 참조 합니다. 이 값은 키로 사용 합니다 `Strings` 와 같은 도구는 지역화 된 이름을 검색할 테이블 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 패키지를 설명 하는 데 사용할 합니다.|  
|`HomeSite`|선택 사항입니다. 원격 서버에 설치 관리자를 사용 하 여 포함 되지 않은 경우 패키지의 위치입니다.|  
|`CopyOnBuild`|선택 사항입니다. 부트스트래퍼 빌드 시 패키지 파일을 디스크를 복사 해야 하는지 여부를 지정 합니다. 기본값은 true입니다.|  
|`PublicKey`|패키지의 인증서 서명자의 공개 키 암호화입니다. 필요한 경우 `HomeSite` 사용 되는, 그렇지 않으면 선택적입니다.|  
|`Hash`|선택 사항입니다. 패키지 파일의 SHA1 해시를 합니다. 설치 시 파일의 무결성을 확인 하는이 사용 됩니다. 패키지 파일에서 동일한 해시를 계산할 수 없습니다 패키지가 설치 되지 않습니다.|  
  
## <a name="example"></a>예제  
 다음 코드 예제에 대 한 패키지 정의 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 재배포 가능 패키지 및 해당 종속성, Windows Installer 등입니다.  
  
```  
<PackageFiles>  
    <PackageFile Name="instmsia.exe" HomeSite="InstMsiAExe" PublicKey="3082010A0282010100AA99BD39A81827F42B3D0B4C3F7C772EA7CBB5D18C0DC23A74D793B5E0A04B3F595ECE454F9A7929F149CC1A47EE55C2083E1220F855F2EE5FD3E0CA96BC30DEFE58C82732D08554E8F09110BBF32BBE19E5039B0B861DF3B0398CB8FD0B1D3C7326AC572BCA29A215908215E277A34052038B9DC270BA1FE934F6F335924E5583F8DA30B620DE5706B55A4206DE59CBF2DFA6BD154771192523D2CB6F9B1979DF6A5BF176057929FCC356CA8F440885558ACBC80F464B55CB8C96774A87E8A94106C7FF0DE968576372C36957B443CF323A30DC1BE9D543262A79FE95DB226724C92FD034E3E6FB514986B83CD0255FD6EC9E036187A96840C7F8E203E6CF050203010001"/>  
    <PackageFile Name="WindowsInstaller-KB884016-v2-x86.exe" HomeSite="Msi30Exe" PublicKey="3082010A0282010100B22D8709B55CDF5599EB5262E7D3F4E34571A932BF94F20EE90DADFE9DC7046A584E9CA4D1D84441FB647E0F65EEC817DA4DDBD9D650B40C565B6C16884BBF03EE504883EC4F88939A51E394197FFAB397A5CE606D9FDD4C9338BDCD345971E686CEE98399A096B8EAE0445B1342B93A484E5472F70896E400C482017643AF61C2DBFAE5C5F00213DDF835B40F0D5236467443B1A2CA9CDD7E99F1351177FB1526018ECFE0B804782A15FD72C66076910CE74FB218181B6989B4F12F211B66EACA91C7460DB91758715856866523D10232AE64A06FDA5295FDFBDD8D34F5C10C35A347D7E91B6AFA0F45B4E8321D7019BDD1F9E5641FEB8737EA6FD40D838FFD0203010001"/>  
    <PackageFile Name="dotnetfx.exe" HomeSite="DotNetFXExe" PublicKey="3082010A0282010100B22D8709B55CDF5599EB5262E7D3F4E34571A932BF94F20EE90DADFE9DC7046A584E9CA4D1D84441FB647E0F65EEC817DA4DDBD9D650B40C565B6C16884BBF03EE504883EC4F88939A51E394197FFAB397A5CE606D9FDD4C9338BDCD345971E686CEE98399A096B8EAE0445B1342B93A484E5472F70896E400C482017643AF61C2DBFAE5C5F00213DDF835B40F0D5236467443B1A2CA9CDD7E99F1351177FB1526018ECFE0B804782A15FD72C66076910CE74FB218181B6989B4F12F211B66EACA91C7460DB91758715856866523D10232AE64A06FDA5295FDFBDD8D34F5C10C35A347D7E91B6AFA0F45B4E8321D7019BDD1F9E5641FEB8737EA6FD40D838FFD0203010001"/>  
    <PackageFile Name="dotnetchk.exe"/>  
</PackageFiles>  
```  
  
## <a name="see-also"></a>참고 항목  
 [\<제품 > 요소](../deployment/product-element-bootstrapper.md)   
 [\<패키지 > 요소](../deployment/package-element-bootstrapper.md)   
 [제품 및 패키지 스키마 참조](../deployment/product-and-package-schema-reference.md)
