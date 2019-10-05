---
title: '방법: 패키지 매니페스트 만들기 | Microsoft Docs'
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
- package files [Windows Installer]
- package files [ClickOnce]
- prerequisites, custom bootstrapper package
- dependencies, custom bootstrapper packages
ms.assetid: 5aecc507-2764-42f2-ae6f-c227971cf0af
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c711c50ab484cc88b1d6aff5c8e3018cead69953
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68153831"
---
# <a name="how-to-create-a-package-manifest"></a>방법: 패키지 매니페스트 만들기
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

응용 프로그램에 대 한 필수 구성 요소를 배포 하려면 부트스트래퍼 패키지를 사용할 수 있습니다. 부트스트래퍼 패키지는 각 로캘에 대해 없지만 패키지 매니페스트를 단일 제품 매니페스트 파일을 포함합니다. 다양 한 지역화 된 버전 간에 공유 되는 기능은 제품 매니페스트로 이동 해야 합니다.  
  
 패키지 매니페스트에 대 한 자세한 내용은 참조 하세요. [방법: 제품 매니페스트 만들기](../deployment/how-to-create-a-product-manifest.md)합니다.  
  
## <a name="creating-the-package-manifest"></a>패키지 매니페스트 만들기  
  
#### <a name="to-create-the-package-manifest"></a>패키지 매니페스트를 만들려면  
  
1. 부트스트래퍼 패키지에 대 한 디렉터리를 만듭니다. 이 예제에서는 C:\package를 사용 합니다.  
  
2. 로캘의 en 영어와 같은 이름의 하위 디렉터리를 만듭니다.  
  
3. Visual Studio에서 이라고 하는 XML 파일을 만듭니다 `package.xml`, C:\package\en 폴더에 저장 합니다.  
  
4. 부트스트래퍼 패키지의 이름,이 지역화 된 패키지 매니페스트 및 선택적 사용권 계약에 대 한 문화권을 나열 하는 XML을 추가 합니다. 다음 XML에서는 변수를 사용 `DisplayName` 고 `Culture`, 뒷부분에 나오는 요소에 정의 된 합니다.  
  
    ```  
    <Package  
        xmlns="http://schemas.microsoft.com/developer/2004/01/bootstrapper"  
        Name="DisplayName"  
        Culture="Culture"  
        LicenseAgreement="eula.txt">  
    ```  
  
5. 로캘 관련 디렉터리에 있는 모든 파일을 나열 하는 XML을 추가 합니다. 다음 XML에 적용할 수 있는 eula.txt 라는 파일을 사용 하 여 **en** 로캘.  
  
    ```  
    <PackageFiles>  
      <PackageFile Name="eula.txt"/>  
    </PackageFiles>  
    ```  
  
6. 부트스트래퍼 패키지에 대 한 지역화 가능한 문자열을 정의 하는 XML을 추가 합니다. 다음 XML en 로캘 오류 문자열을 추가합니다.  
  
    ```  
      <Strings>  
        <String Name="DisplayName">Custom Bootstrapper Package</String>  
        <String Name="CultureName">en</String>  
        <String Name="NotAnAdmin">You must be an administrator to install   
    this package.</String>  
        <String Name="GeneralFailure">A general error has occurred while   
    installing this package.</String>  
    </Strings>  
    ```  
  
7. Visual Studio 부트스트래퍼 디렉터리로 C:\package 폴더를 복사 합니다. Visual Studio 2010 용 \Program Files\Microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages 디렉터리입니다.  
  
## <a name="example"></a>예제  
 패키지 매니페스트는 오류 메시지, 소프트웨어 사용 조건 및 언어 팩 등의 로캘별 정보를 포함합니다.  
  
```  
<?xml version="1.0" encoding="utf-8" ?>  
<Package  
  xmlns="http://schemas.microsoft.com/developer/2004/01/bootstrapper"  
  Name="DisplayName"  
  Culture="Culture"  
  LicenseAgreement="eula.txt">  
  
  <PackageFiles>  
    <PackageFile Name="eula.txt"/>  
  </PackageFiles>  
  
  <Strings>  
    <String Name="DisplayName">Custom Bootstrapper Package</String>  
    <String Name="Culture">en</String>  
    <String Name="NotAnAdmin">You must be an administrator to install this package.</String>  
    <String Name="GeneralFailure">A general error has occurred while   
installing this package.</String>  
  </Strings>  
</Package>  
```  
  
## <a name="see-also"></a>관련 항목  
 [제품 및 패키지 스키마 참조](../deployment/product-and-package-schema-reference.md)
