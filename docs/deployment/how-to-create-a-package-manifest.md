---
title: '방법: 패키지 매니페스트 만들기 | Microsoft Docs'
ms.date: 11/04/2016
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d8083ca9a8d3025b1760edde96279a0cd557f722
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62899742"
---
# <a name="how-to-create-a-package-manifest"></a>방법: 패키지 매니페스트 만들기
응용 프로그램에 대 한 필수 구성 요소를 배포 하려면 부트스트래퍼 패키지를 사용할 수 있습니다. 부트스트래퍼 패키지는 각 로캘에 대해 없지만 패키지 매니페스트를 단일 제품 매니페스트 파일을 포함합니다. 다양 한 지역화 된 버전 간에 공유 되는 기능은 제품 매니페스트로 이동 해야 합니다.

 제품 매니페스트 하는 방법에 대 한 자세한 내용은 참조 하세요. [방법: 제품 매니페스트 만들기](../deployment/how-to-create-a-product-manifest.md)합니다.

## <a name="create-the-package-manifest"></a>패키지 매니페스트 만들기

#### <a name="to-create-the-package-manifest"></a>패키지 매니페스트를 만들려면

1. 부트스트래퍼 패키지에 대 한 디렉터리를 만듭니다. 이 예제에서는 *C:\package*합니다.

2. 와 같은 로캘 이름의 하위 디렉터리를 만듭니다 *en* 영어입니다.

3. Visual Studio에서 이라고 하는 XML 파일을 만듭니다 *package.xml*를 저장 합니다 *C:\package\en* 폴더입니다.

4. 부트스트래퍼 패키지의 이름,이 지역화 된 패키지 매니페스트 및 선택적 사용권 계약에 대 한 문화권을 나열 하는 XML을 추가 합니다. 다음 XML에서는 변수를 사용 `DisplayName` 고 `Culture`, 뒷부분에 나오는 요소에 정의 된 합니다.

    ```xml
    <Package
        xmlns="http://schemas.microsoft.com/developer/2004/01/bootstrapper"
        Name="DisplayName"
        Culture="Culture"
        LicenseAgreement="eula.txt">
    ```

5. 로캘 관련 디렉터리에 있는 모든 파일을 나열 하는 XML을 추가 합니다. 라는 파일을 사용 하는 다음 XML *eula.txt* 에 적용 되는 **en** 로캘.

    ```xml
    <PackageFiles>
      <PackageFile Name="eula.txt"/>
    </PackageFiles>
    ```

6. 부트스트래퍼 패키지에 대 한 지역화 가능한 문자열을 정의 하는 XML을 추가 합니다. 다음 XML에 대 한 오류 문자열을 추가 합니다 **en** 로캘.

    ```xml
      <Strings>
        <String Name="DisplayName">Custom Bootstrapper Package</String>
        <String Name="CultureName">en</String>
        <String Name="NotAnAdmin">You must be an administrator to install
    this package.</String>
        <String Name="GeneralFailure">A general error has occurred while
    installing this package.</String>
    </Strings>
    ```

7. 복사 합니다 *C:\package* Visual Studio 부트스트래퍼 디렉터리에는 폴더입니다. 이것이 Visual Studio 2010에 대 한 합니다 *\Program Files\Microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages* 디렉터리입니다.

## <a name="example"></a>예제
 패키지 매니페스트는 오류 메시지, 소프트웨어 사용 조건 및 언어 팩 등의 로캘별 정보를 포함합니다.

```xml
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

## <a name="see-also"></a>참고자료
- [제품 및 패키지 스키마 참조](../deployment/product-and-package-schema-reference.md)