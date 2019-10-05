---
title: '방법: 제품 매니페스트 만들기 | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- product files [ClickOnce]
- product files [Windows Installer]
- prerequisites, custom bootstrapper package
- dependencies, custom bootstrapper package
ms.assetid: 2d316aaa-8bc0-4ce5-90ab-23b3eac0b5dd
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 68f3006104b50876f6d2716ff4eb1efe0a705284
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62928367"
---
# <a name="how-to-create-a-product-manifest"></a>방법: 제품 매니페스트 만들기
응용 프로그램에 대 한 필수 구성 요소를 배포 하려면 부트스트래퍼 패키지를 만들 수 있습니다. 부트스트래퍼 패키지는 각 로캘에 대해 없지만 패키지 매니페스트를 단일 제품 매니페스트 파일을 포함합니다. 패키지 매니페스트 지역화 관련 부분은 패키지를 포함합니다. 문자열, 최종 사용자 사용권 계약 및 언어 팩이 포함 됩니다.

 패키지 매니페스트에 대 한 자세한 내용은 참조 하세요. [방법: 패키지 매니페스트 만들기](../deployment/how-to-create-a-package-manifest.md)를 참조하세요.

## <a name="create-the-product-manifest"></a>제품 매니페스트 만들기

#### <a name="to-create-the-product-manifest"></a>제품 매니페스트를 만들려면

1. 부트스트래퍼 패키지에 대 한 디렉터리를 만듭니다. 이 예제에서는 C:\package를 사용 합니다.

2. Visual Studio에서 라는 새 XML 파일을 만듭니다 *product.xml*에 저장 하 고는 *C:\package* 폴더입니다.

3. 패키지에 대 한 XML 네임 스페이스 및 제품 코드를 설명 하는 다음 XML을 추가 합니다. 패키지에 대 한 고유 식별자가 있는 제품 코드를 바꿉니다.

    ```xml
    <Product
    xmlns="http://schemas.microsoft.com/developer/2004/01/bootstrapper"
    ProductCode="Custom.Bootstrapper.Package">
    ```

4. 패키지에 종속성을 지정 하는 XML을 추가 합니다. 이 예제에서는 Microsoft Windows Installer 3.1에서 종속성을 사용 합니다.

    ```xml
    <RelatedProducts>
        <DependsOnProduct Code="Microsoft.Windows.Installer.3.1" />
      </RelatedProducts>
    ```

5. 부트스트래퍼 패키지에 있는 모든 파일을 나열 하는 XML을 추가 합니다. 이 예에서는 패키지 파일 이름 *CorePackage.msi*합니다.

    ```xml
    <PackageFiles>
        <PackageFile Name="CorePackage.msi"/>
    </PackageFiles>
    ```

6. 복사 하거나 이동 합니다 *CorePackage.msi* 파일을 합니다 *C:\package* 폴더입니다.

7. 부트스트래퍼 명령을 사용 하 여 패키지를 설치 하는 XML을 추가 합니다. 부트스트래퍼가 자동으로 추가 합니다 **/qn** 플래그를 *.msi* 자동으로 설치 하는 파일. 파일이 있으면를 *.exe*, 부트스트래퍼를 실행 합니다 *.exe* 셸을 사용 하 여 파일입니다. 다음 XML 표시 인수 없이 *CorePackage.msi*를 명령줄 인수를 넣을 수 있지만 `Arguments` 특성입니다.

    ```xml
    <Commands>
        <Command PackageFile="CorePackage.msi" Arguments="">
    ```

8. 이 부트스트래퍼 패키지가 설치 되어 있는지 확인 하려면 다음 XML을 추가 합니다. 재배포 가능 구성 요소에 대 한 GUID를 사용 하 여 제품 코드를 바꿉니다.

    ```xml
    <InstallChecks>
        <MsiProductCheck
            Property="IsMsiInstalled"
            Product="{XXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX}"/>
    </InstallChecks>
    ```

9. 부트스트래퍼 구성 요소를 이미 설치한 경우에 따라 부트스트래퍼 동작을 변경 하는 XML을 추가 합니다. 요소를 설치 하는 경우 부트스트래퍼 패키지가 실행 되지 않습니다. 다음 XML이 구성이 요소 관리 권한이 필요 하므로 현재 사용자가 관리자 인지 확인 합니다.

    ```xml
    <InstallConditions>
        <BypassIf
           Property="IsMsiInstalled"
           Compare="ValueGreaterThan" Value="0"/>
        <FailIf Property="AdminUser"
            Compare="ValueNotEqualTo" Value="True"
            String="NotAnAdmin"/>
    </InstallConditions>
    ```

10. 설치가 완료 되 고 다시 부팅이 필요한 경우 종료 코드를 설정 하는 XML을 추가 합니다. 다음 XML 실패 하 고 FailReboot 부트스트래퍼 패키지 설치 계속 되지 것입니다 나타내는 코드를 종료 하는 방법을 보여 줍니다.

    ```xml
    <ExitCodes>
        <ExitCode Value="0" Result="Success"/>
        <ExitCode Value="1641" Result="SuccessReboot"/>
        <ExitCode Value="3010" Result="SuccessReboot"/>
        <DefaultExitCode Result="Fail" String="GeneralFailure"/>
    </ExitCodes>
    ```

11. 부트스트래퍼 명령에 대 한 섹션을 종료 하려면 다음 XML을 추가 합니다.

    ```xml
        </Command>
    </Commands>
    ```

12. 이동 합니다 *C:\package* Visual Studio 부트스트래퍼 디렉터리에는 폴더입니다. 이것이 Visual Studio 2010에 대 한 합니다 *\Program Files\Microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages* 디렉터리입니다.

## <a name="example"></a>예제
 제품 매니페스트는 사용자 지정 필수 구성 요소에 대 한 설치 지침이 포함 되어 있습니다.

```xml
<?xml version="1.0" encoding="utf-8" ?>
<Product
  xmlns="http://schemas.microsoft.com/developer/2004/01/bootstrapper"
  ProductCode="Custom.Bootstrapper.Package">

  <RelatedProducts>
    <DependsOnProduct Code="Microsoft.Windows.Installer.3.1" />
  </RelatedProducts>

  <PackageFiles>
    <PackageFile Name="CorePackage.msi"/>
  </PackageFiles>

  <InstallChecks>
    <MsiProductCheck Product="IsMsiInstalled"
      Property="{XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX}"/>
  </InstallChecks>

  <Commands>
    <Command PackageFile="CorePackage.msi" Arguments="">

      <InstallConditions>
        <BypassIf Property="IsMsiInstalled"
          Compare="ValueGreaterThan" Value="0"/>
        <FailIf Property="AdminUser"
          Compare="ValueNotEqualTo" Value="True"
         String="NotAnAdmin"/>
      </InstallConditions>

      <ExitCodes>
        <ExitCode Value="0" Result="Success"/>
        <ExitCode Value="1641" Result="SuccessReboot"/>
        <ExitCode Value="3010" Result="SuccessReboot"/>
        <DefaultExitCode Result="Fail" String="GeneralFailure"/>
      </ExitCodes>
    </Command>
  </Commands>
</Product>
```

## <a name="see-also"></a>참고자료
- [제품 및 패키지 스키마 참조](../deployment/product-and-package-schema-reference.md)