---
title: '&lt;InstallChecks&gt; 요소 (부트스트래퍼) | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- <InstallChecks> element [bootstrapper]
ms.assetid: ad329c87-b0ad-4304-84de-ae9496514c42
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 79bbb413c31c77e59ec39b706d4937421096168f
ms.sourcegitcommit: 12f2851c8c9bd36a6ab00bf90a020c620b364076
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/06/2019
ms.locfileid: "66747527"
---
# <a name="ltinstallchecksgt-element-bootstrapper"></a>&lt;InstallChecks&gt; 요소 (부트스트래퍼)
`InstallChecks` 요소를 지 원하는 다양 한 응용 프로그램에 대 한 적절 한 필수 구성 요소가 모두 설치 되었는지 확인 하려면 로컬 컴퓨터에 대해 테스트를 시작 합니다.

## <a name="syntax"></a>구문

```xml
<InstallChecks>
    <AssemblyCheck
        Property
        Name
        PublicKeyToken
        Version
        Language
        ProcessorArchitecture
    />
    <RegistryCheck
        Property
        Key
        Value
    />
    <ExternalCheck
        PackageFile
        Property
        Arguments
    />
    <FileCheck
        Property
        FileName
        SearchPath
        SpecialFolder
        SearchDepth
    />
    <MsiProductCheck
        Property
        Product
        Feature
    />
    <RegistryFileCheck
        Property
        Key
        Value
        FileName
        SearchDepth
    />
</InstallChecks>
```

## <a name="assemblycheck"></a>AssemblyCheck
 이 요소는 선택적 자식 요소의 `InstallChecks`합니다. 각 인스턴스에 대해 `AssemblyCheck`, 부트스트래퍼 요소에서 식별 한 어셈블리를 전역 어셈블리 캐시 (GAC)에 있는지 확인 합니다. 요소를 포함 하지 하 고 다음과 같은 특성이 있습니다.

|특성|설명|
|---------------|-----------------|
|`Property`|필수 요소. 결과 저장 하는 속성의 이름입니다. 아래의 테스트에서이 속성을 참조할 수 있습니다 합니다 `InstallConditions` 자식 요소의는 `Command` 요소입니다. 자세한 내용은 [ \<명령 > 요소](../deployment/commands-element-bootstrapper.md)합니다.|
|`Name`|필수 요소. 확인할 어셈블리의 정규화 된 이름입니다.|
|`PublicKeyToken`|필수 요소. 강력한 이름의 어셈블리와 연결 된 공개 키의 약식입니다. GAC에 저장 된 모든 어셈블리 이름, 버전, 및 공개 키에 있어야 합니다.|
|`Version`|필수 요소. 어셈블리의 버전입니다.<br /><br /> 버전 번호의 형식은 \< *주 버전*>.\< *부 버전*>.\< *버전을 빌드합니다*>.\< *수정 버전*>.|
|`Language`|선택 사항입니다. 지역화 된 어셈블리의 언어입니다. 기본값은 `neutral`입니다.|
|`ProcessorArchitecture`|선택 사항입니다. 이 설치에서 대상 컴퓨터 프로세서입니다. 기본값은 `msil`입니다.|

## <a name="externalcheck"></a>ExternalCheck
 이 요소는 선택적 자식 요소의 `InstallChecks`합니다. 인스턴스마다 `ExternalCheck`, 부트스트래퍼는 별도 프로세스에서 명명된 된 외부 프로그램을 실행 하 고 종료 코드를 나타내는 속성에 저장 `Property`합니다. `ExternalCheck` 복잡 한 종속성 검사를 구현 또는 구성 요소의 존재 여부를 확인 하는 유일한 방법은를 인스턴스화해야 하는 경우 유용 합니다.

 `ExternalCheck` 요소를 포함 하지 하 고 다음과 같은 특성이 있습니다.

|특성|설명|
|---------------|-----------------|
|`Property`|필수 요소. 결과 저장 하는 속성의 이름입니다. 아래의 테스트에서이 속성을 참조할 수 있습니다 합니다 `InstallConditions` 자식 요소의는 `Command` 요소입니다. 자세한 내용은 [ \<명령 > 요소](../deployment/commands-element-bootstrapper.md)합니다.|
|`PackageFile`|필수 요소. 외부 프로그램을 실행 합니다. 프로그램 설치 배포 패키지의 일부 여야 합니다.|
|`Arguments`|선택 사항입니다. 으로 명명 된 실행 파일에 명령줄 인수를 제공 `PackageFile`합니다.|

## <a name="filecheck"></a>FileCheck
 이 요소는 선택적 자식 요소의 `InstallChecks`합니다. 각 인스턴스에 대해 `FileCheck`, 부트스트래퍼는 명명 된 파일이 있으면 및 파일의 버전 번호를 반환 하는지 여부를 확인 합니다. 부트스트래퍼에서 명명 한 속성 설정 파일에 버전 번호를 찾을 수 없는 경우 `Property` 0입니다. 파일이 없으면 `Property` 값으로 설정 되지 않은 합니다.

 `FileCheck` 요소를 포함 하지 하 고 다음과 같은 특성이 있습니다.

| 특성 | 설명 |
|-----------------| - |
| `Property` | 필수 요소. 결과 저장 하는 속성의 이름입니다. 아래의 테스트에서이 속성을 참조할 수 있습니다 합니다 `InstallConditions` 자식 요소의는 `Command` 요소입니다. 자세한 내용은 [ \<명령 > 요소](../deployment/commands-element-bootstrapper.md)합니다. |
| `FileName` | 필수 요소. 검색할 파일의 이름입니다. |
| `SearchPath` | 필수 요소. 디스크 또는 파일을 검색할 폴더입니다. 경우 상대 경로 여야 합니다이 `SpecialFolder` 할당 된이 고, 그렇지는 절대 경로 여야 합니다. |
| `SpecialFolder` | 선택 사항입니다. Windows 또는 특별 한 의미가 있는 폴더 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]합니다. 기본적으로 해석 됩니다 `SearchPath` 절대 경로로 합니다. 유효한 값은 다음과 같습니다.<br /><br /> `AppDataFolder`. 이 응용 프로그램 데이터 폴더 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 응용 프로그램; 현재 사용자에 게 특정 합니다.<br /><br /> `CommonAppDataFolder`. 모든 사용자가 사용 되는 응용 프로그램 데이터 폴더입니다.<br /><br /> `CommonFilesFolder`. 현재 사용자에 대 한 공용 파일 폴더입니다.<br /><br /> `LocalDataAppFolder`. 고정 된 응용 프로그램 데이터 폴더입니다.<br /><br /> `ProgramFilesFolder`. 32 비트 응용 프로그램에 대 한 표준 Program Files 폴더를 지정 합니다.<br /><br /> `StartUpFolder`. 시스템 시작 시 시작 하는 모든 응용 프로그램을 포함 하는 폴더입니다.<br /><br /> `SystemFolder`. 32 비트 시스템 Dll을 포함 하는 폴더입니다.<br /><br /> `WindowsFolder`. Windows 시스템 설치가 포함 된 폴더입니다.<br /><br /> `WindowsVolume`. 드라이브 또는 Windows 시스템 설치를 포함 하는 파티션입니다. |
| `SearchDepth` | 선택 사항입니다. 명명된 된 파일에 대 한 하위 폴더를 검색 하는 깊이입니다. 검색에는 깊이 우선 됩니다. 기본값은 0으로 지정 된 최상위 폴더에 검색을 제한 하는 `SpecialFolder` 하 고 **SearchPath**합니다. |

## <a name="msiproductcheck"></a>MsiProductCheck
 이 요소는 선택적 자식 요소의 `InstallChecks`합니다. 각 인스턴스에 대해 `MsiProductCheck`, 부트스트래퍼를 완료할 때까지 지정 된 Microsoft Windows Installer 설치에 실행 여부를 확인 합니다. 속성 값을 해당 설치 된 제품의 상태에 따라 설정 됩니다. 양수 값을 제품 설치 되었음을 나타내고, 0 또는-1을 설치 하지 않은 나타냅니다. (자세한 내용은 Windows Installer SDK 함수 MsiQueryFeatureState을 참조 하십시오.) . Windows Installer 컴퓨터에 설치 되어 있지 않으면 `Property` 설정 되지 않았습니다.

 `MsiProductCheck` 요소를 포함 하지 하 고 다음과 같은 특성이 있습니다.

|특성|설명|
|---------------|-----------------|
|`Property`|필수 요소. 결과 저장 하는 속성의 이름입니다. 아래의 테스트에서이 속성을 참조할 수 있습니다 합니다 `InstallConditions` 자식 요소의는 `Command` 요소입니다. 자세한 내용은 [ \<명령 > 요소](../deployment/commands-element-bootstrapper.md)합니다.|
|`Product`|필수 요소. 설치 된 제품에 대 한 GUID입니다.|
|`Feature`|선택 사항입니다. 설치 된 응용 프로그램의 특정 기능에 대 한 GUID입니다.|

## <a name="registrycheck"></a>RegistryCheck
 이 요소는 선택적 자식 요소의 `InstallChecks`합니다. 각 인스턴스에 대해 `RegistryCheck`, 부트스트래퍼가 지정된 된 레지스트리 키가 있는지 또는 지정 된 값이 있는지 여부를 확인 합니다.

 `RegistryCheck` 요소를 포함 하지 하 고 다음과 같은 특성이 있습니다.

|특성|설명|
|---------------|-----------------|
|`Property`|필수 요소. 결과 저장 하는 속성의 이름입니다. 아래의 테스트에서이 속성을 참조할 수 있습니다 합니다 `InstallConditions` 자식 요소의는 `Command` 요소입니다. 자세한 내용은 [ \<명령 > 요소](../deployment/commands-element-bootstrapper.md)합니다.|
|`Key`|필수 요소. 레지스트리 키의 이름입니다.|
|`Value`|선택 사항입니다. 검색할 레지스트리 값의 이름입니다. 기본값의 텍스트를 반환 하는 기본값은입니다. `Value` DWORD 또는 문자열이 있어야 합니다.|

## <a name="registryfilecheck"></a>RegistryFileCheck
 이 요소는 선택적 자식 요소의 `InstallChecks`합니다. 각 인스턴스에 대해 `RegistryFileCheck`, 부트스트래퍼는 먼저 지정된 된 레지스트리 키에서 파일의 경로 검색 하는 동안 지정된 된 파일의 버전 검색 합니다. 레지스트리에서 값으로 지정 된 디렉터리에서 파일을 조회 하려는 경우 특히 유용 합니다.

 `RegistryFileCheck` 요소를 포함 하지 하 고 다음과 같은 특성이 있습니다.

|특성|설명|
|---------------|-----------------|
|`Property`|필수 요소. 결과 저장 하는 속성의 이름입니다. 아래의 테스트에서이 속성을 참조할 수 있습니다 합니다 `InstallConditions` 자식 요소의는 `Command` 요소입니다. 자세한 내용은 [ \<명령 > 요소](../deployment/commands-element-bootstrapper.md)합니다.|
|`Key`|필수 요소. 레지스트리 키의 이름입니다. 있지 않으면 해당 값을 파일 경로로 해석 됩니다는 `File` 특성이 설정 되어 있습니다. 이 키가 없으면 `Property` 설정 되지 않았습니다.|
|`Value`|선택 사항입니다. 검색할 레지스트리 값의 이름입니다. 기본값의 텍스트를 반환 하는 기본값은입니다. `Value` 문자열 이어야 합니다.|
|`FileName`|선택 사항입니다. 파일의 이름입니다. 레지스트리 키에서 얻은 값 디렉터리 경로 간주 됩니다 지정 하는 경우 및이 이름에 추가 됩니다. 지정 하지 않으면 레지스트리에서 반환 된 값 파일의 전체 경로를 가정 합니다.|
|`SearchDepth`|선택 사항입니다. 명명된 된 파일에 대 한 하위 폴더를 검색 하는 깊이입니다. 검색에는 깊이 우선 됩니다. 기본값은 0으로, 레지스트리 키의 값으로 지정 된 최상위 폴더에 검색을 제한 합니다.|

## <a name="remarks"></a>설명
 요소 아래에 있는 동안 `InstallChecks` 해당 실행 되지, 실행할 테스트를 정의 합니다. 테스트를 실행 하려면 만들어야 `Command` 아래에 있는 요소는 `Commands` 요소입니다.

## <a name="example"></a>예제
 다음 코드 예제는 `InstallChecks` 되는 요소는.NET Framework에 대 한 제품 파일에서 사용 됩니다.

```xml
<InstallChecks>
    <ExternalCheck Property="DotNetInstalled" PackageFile="dotnetchk.exe" />
    <RegistryCheck Property="IEVersion" Key="HKLM\Software\Microsoft\Internet Explorer" Value="Version" />
</InstallChecks>
```

## <a name="installconditions"></a>InstallConditions
 때 `InstallChecks` 는 속성이 생성 계산 됩니다. 속성에서 사용 하는 다음 `InstallConditions` 패키지 해야 설치, 무시할 또는 실패 여부를 확인 하려면. 다음 표에서 `InstallConditions`:

|||
|-|-|
|`FailIf`|있는 경우 `FailIf` 조건이 true 인 경우 패키지가 실패 합니다. 나머지 조건 평가할 수 없습니다.|
|`BypassIf`|있는 경우 `BypassIf` 조건이 true 인 경우 패키지는 사용 되지 것입니다. 나머지 조건 평가할 수 없습니다.|

## <a name="predefined-properties"></a>미리 정의 된 속성
 다음 표에서 `BypassIf` 고 `FailIf` 요소:

|속성|노트|가능한 값|
|--------------|-----------|---------------------|
|`Version9X`|Windows 9 X 운영 체제의 버전 번호입니다.|4.10 = Windows 98|
|`VersionNT`|Windows NT 기반 운영 체제의 버전 번호입니다.|Major.Minor.ServicePack<br /><br /> 5.0 = Windows 2000<br /><br /> 5.1.0 = Windows XP<br /><br /> 5.1.2 = Windows XP Professional SP2<br /><br /> 5.2.0 = Windows Server 2003|
|`VersionNT64`|64 비트 Windows NT 기반 운영 체제의 버전 번호입니다.|앞서 언급 한 것 처럼 동일 합니다.|
|`VersionMsi`|Windows Installer 서비스의 버전 번호입니다.|2.0 = Windows Installer 2.0|
|`AdminUser`|사용자는 Windows NT 기반 운영 체제에 대 한 관리자 권한이 있는지 여부를 지정 합니다.|0 = 관리자 권한 없음<br /><br /> 1 = 관리자 권한|

 예를 들어, Windows 95를 실행 하는 컴퓨터에 설치를 차단 하려면 다음과 같은 코드를 사용 합니다.

```xml
<!-- Block install on Windows 95 -->
    <FailIf Property="Version9X" Compare="VersionLessThan" Value="4.10" String="InvalidPlatform"/>
```

## <a name="see-also"></a>참고자료
- [\<명령 > 요소](../deployment/commands-element-bootstrapper.md)
- [제품 및 패키지 스키마 참조](../deployment/product-and-package-schema-reference.md)