---
title: '방법: 소스 제어 플러그 인 설치 | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- installation [Visual Studio SDK], source control plug-ins
- source control plug-ins, installing
ms.assetid: 9e2e01d9-7beb-42b2-99b2-86995578afda
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9de10f1aebd47093a3cc3f41343e73cefdde473a
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66334920"
---
# <a name="how-to-install-a-source-control-plug-in"></a>방법: 소스 제어 플러그 인 설치
소스 제어 플러그 인을 만드는 세 가지 단계가 포함 됩니다.

1. 이 설명서의 원본 제어 플러그 인 API 참조 섹션에 정의 된 함수를 사용 하 여 DLL을 만듭니다.

2. 원본 제어 플러그 인 API 정의 함수를 구현 합니다. 때 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 호출 후에 대 한 인터페이스 및 대화 상자에서 사용할 수 있도록 플러그 인입니다.

3. 적절 한 레지스트리 항목을 만들어 DLL을 등록 합니다.

## <a name="integration-with-visual-studio"></a>Visual Studio와의 통합
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 원본 제어 플러그 인 소스 제어 플러그 인 API를 준수 하는 지원 합니다.

### <a name="register-the-source-control-plug-in"></a>소스 제어 플러그 인 등록
 먼저 원본 소스 제어 시스템에는 실행 중인 통합된 개발 환경 (IDE)를 호출 하기 전에 찾아야 내보내는 API 플러그 인 DLL을 제어 합니다.

#### <a name="to-register-the-source-control-plug-in-dll"></a>등록 하는 소스 제어 플러그 인 DLL

1. 아래 두 항목을 추가 합니다 **HKEY_LOCAL_MACHINE** 키를 **소프트웨어** 에 회사 이름 하위 키를 지정 하는 하위 키 뒤에 제품 이름 하위 키입니다. 패턴이 **HKEY_LOCAL_MACHINE\SOFTWARE\\\<회사 이름 >\\\<제품 이름 >\\\<항목 >**  =  *값*합니다. 두 항목은 항상 이라고 **SCCServerName** 하 고 **SCCServerPath**합니다. 각각 일반 문자열입니다.

    예를 들어, 회사 이름은 Microsoft 하 고 원본 제어 제품 이름이 SourceSafe 인 경우 다음이 레지스트리는 경로일 **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SourceSafe**합니다. 첫 번째 항목을이 하위 키 **SCCServerName**, 제품 이름 사용자를 읽을 수 있는 문자열입니다. 두 번째 항목은 **SCCServerPath**, IDE에 연결 해야 하는 플러그 인 DLL을 제어 하는 원본에 전체 경로입니다. 다음은 샘플 레지스트리 항목에 대 한 설명입니다.

   |샘플 레지스트리 항목|샘플 값|
   |---------------------------|------------------|
   |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SourceSafe\SCCServerName|Microsoft Visual SourceSafe|
   |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SourceSafe\SCCServerPath|*c:\vss\win32\ssscc.dll*|

   > [!NOTE]
   > SCCServerPath에 SourceSafe 플러그 인에 전체 경로입니다. 소스 제어 플러그 인 회사 및 제품 이름은 다르지만 동일한 레지스트리 항목 경로 사용 합니다.

2. 소스 제어 플러그 인의 동작을 수정 하려면 다음 선택적 레지스트리 항목을 사용할 수 있습니다. 이러한 항목으로 동일한 하위 키에서 이동 **SccServerName** 하 고 **SccServerPath**합니다.

   - 합니다 **HideInVisualStudioregistry** 원본 제어 플러그 인-에 표시 하지 않을 경우 항목을 사용할 수 있습니다 합니다 **플러그 인 선택** 목록을 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]합니다. 이 항목이 소스 제어 플러그 인으로 자동 전환 변경 됩니다. 이 항목에 대 한 한 가지 가능한 용도 경우 소스 제어 플러그 인을 대체 하는 원본 제어 패키지를 제공 하지만 소스 제어 플러그 인을 소스 제어 패키지를 사용 하 여 마이그레이션할 사용자가 보다 쉽게 확인 하려는 경우 원본 제어 패키지를 설치 하는 경우 플러그 인을 숨기는이 레지스트리 항목을 설정 합니다.

      **HideInVisualStudio** DWORD 값 이며로 설정 된 *1* 숨기려면 플러그 인 또는 *0* 플러그 인을 표시 합니다. 레지스트리 항목을 표시 되지 않는 경우 기본 동작은 플러그 인을 표시 합니다.

   - **DisableSccManager** 레지스트리 항목을 비활성화 하거나 숨길 수는 **시작 \<소스 제어 서버 >** 에 일반적으로 표시 되는 메뉴 옵션을 **파일**  >  **소스 제어** 하위 메뉴. 호출 옵션이 메뉴를 선택 하 여 [SccRunScc](../../extensibility/sccrunscc-function.md) 함수입니다. 소스 제어 플러그 인 외부 프로그램을 지원 하지 않을 수 및 사용 안 함 또는 숨기기도 해야 할 수 있습니다 합니다 **시작** 메뉴 옵션입니다.

      **DisableSccManager** DWORD 값 이며로 설정 된 *0* 사용 하도록 설정 합니다 **시작 \<소스 제어 서버 >** 메뉴 옵션을 설정 *1* 를 메뉴 옵션을 사용 하지 않도록 설정 하 고로 *2* 메뉴 옵션을 숨깁니다. 이 레지스트리 항목 표시 되지 않는 경우 기본 동작은 메뉴 옵션을 표시 합니다.

   | 샘플 레지스트리 항목 | 샘플 값 |
   | - |--------------|
   | HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SourceSafe\HideInVisualStudio | 1 |
   | HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SourceSafe\DisableSccManager | 1 |

3. 하위 키를 추가 **SourceCodeControlProvider**아래에 있는 합니다 **HKEY_LOCAL_MACHINE** 키를 **소프트웨어** 하위 키입니다.

    레지스트리 항목을이 하위 키 아래 **ProviderRegKey** 단계 1 레지스트리의에 배치 하는 하위 키를 나타내는 문자열로 설정 됩니다. 패턴이 **HKEY_LOCAL_MACHINE\SOFTWARE\SourceCodeControlProvider\ProviderRegKey** = *소프트웨어\\< 회사 이름\>\\< 제품 이름 \>* .

    이 하위 키에 대 한 샘플 콘텐츠는 다음과 같습니다.

   |레지스트리 항목|샘플 값|
   |--------------------|------------------|
   |HKEY_LOCAL_MACHINE\SOFTWARE\SourceCodeControlProvider\ProviderRegKey|SOFTWARE\Microsoft\SourceSafe|

   > [!NOTE]
   > 동일한 하위 키 및 항목 이름에 원본 제어 플러그 인을 사용 하지만 다른 값이 됩니다.

4. 명명 된 하위 키를 만듭니다 **InstalledSCCProviders** 아래를 **SourceCodeControlProvider** 하위, 키 및 해당 하위 키 아래에 있는 하나의 항목을 배치 합니다.

    이 항목의 이름 (동일 SCCServerName 항목에 대 한 지정 된 값), 공급자의 사용자가 읽을 수 있는 이름을 이며 값, 이번에 1 단계에서 만든 하위 키입니다. 패턴이 **HKEY_LOCAL_MACHINE\SOFTWARE\SourceCodeControlProvider\InstalledSCCProviders\\< 표시 이름\>**  = *소프트웨어\\< 회사 이름을\>\\< 제품 이름\>* 합니다.

    예를 들어:

   |샘플 레지스트리 항목|샘플 값|
   |---------------------------|------------------|
   |HKEY_LOCAL_MACHINE\SOFTWARE\SourceCodeControlProvider\InstalledSCCProviders\Microsoft Visual SourceSafe|SOFTWARE\Microsoft\SourceSafe|

   > [!NOTE]
   > 여러 원본 제어 플러그 인이 방식으로 등록 되어 있을 수 있습니다. 이것이 어떻게 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 찾은 모든 원본 제어 플러그 인 API 기반 플러그 인을 설치 합니다.

## <a name="how-an-ide-locates-the-dll"></a>IDE에서 DLL을 찾는 하는 방법
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE에는 두 개의 플러그 인 DLL을 제어 하는 소스를 찾는 방법.

- 기본 소스 제어 플러그 인 찾아 자동으로 연결 합니다.

- 찾을 등록 된 모든 원본 제어 플러그 인을 올 사용자 하나를 선택 합니다.

  첫 번째 방법은에서 DLL을 찾으려고 IDE에서 표시 합니다 **HKEY_LOCAL_MACHINE\Software\SourceCodeControlProvider** 항목에 대 한 하위 키 **ProviderRegKey**합니다. 이 항목의 값이 다른 하위 키를 가리킵니다. IDE 라는 항목이 다음 찾습니다 **SccServerPath** 아래에서 두 번째 하위 키 아래에 **HKEY_LOCAL_MACHINE**합니다. 이 항목의 값이 DLL을 IDE를 가리킵니다.

> [!NOTE]
> IDE 상대 경로에서 Dll을 로드 하지 않습니다 (예를 들어 *.\NewProvider.DLL*). DLL에 전체 경로 지정 해야 합니다 (예를 들어 *c:\Providers\NewProvider.DLL*). 이 무단 또는 가장 플러그 인 Dll의 로드를 방지 하 여 IDE의 보안을 강화 합니다.

 두 번째 방법은에서 DLL을 찾으려고 IDE에서 표시 합니다 **HKEY_LOCAL_MACHINE\Software\SourceCodeControlProvider\InstalledSCCProviders** 모든 항목에 대 한 하위 키입니다. 각 항목에는 이름 및 값입니다. IDE는 사용자에 게 이러한 이름 목록을 표시합니다. 사용자 이름을 선택 하는 경우 IDE는 하위 키를 가리키는 선택한 이름에 대 한 값을 찾습니다. IDE 라는 항목을 찾습니다 **SccServerPath** 아래에 있는 하위 키 아래에 **HKEY_LOCAL_MACHINE**합니다. 해당 항목의 값이 올바른 DLL을 IDE를 가리킵니다.

 소스 제어 플러그 인 DLL을 찾는 한 가지 방법을 모두 지원 하며, 결과적으로 설정 **ProviderRegKey**, 이전 설정을 덮어씁니다. 무엇 보다도 목록에 추가 자체 해야 **InstalledSccProviders** 하므로 사용자는 사용 하는 소스 제어 플러그 인 중에서 선택할 수 있습니다.

> [!NOTE]
> 그러나 때문에 합니다 **HKEY_LOCAL_MACHINE** 키를 지정된 된 컴퓨터에서 플러그 인 기본 소스 제어로 하나의 소스 제어 플러그 인을 등록할 수 있습니다 ( [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 사용자가 원본 제어 플러그 인을 확인할 수 실제로 사용 하려는 특정 솔루션에 대 한). 설치 프로세스 중 확인 하는 경우 소스 제어 플러그 인을 이미 설정 되어; 그렇다면 사용자에 게 요청 플러그 인을 기본적으로 설치 되 고 새 소스 제어를 설정할 것인지 여부입니다. 제거 하는 동안 모든 원본 제어 플러그 인에서 공통 되는 다른 레지스트리 하위 키를 제거 하지 마세요 **HKEY_LOCAL_MACHINE\SOFTWARE\SourceCodeControlProvider**;에 특정 SCC 하위 키만 제거 합니다.

## <a name="how-the-ide-detects-version-1213-support"></a>IDE 지원 버전 1.2/1.3을 검색 하는 방법
 어떻게 않습니다 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 되었는지 플러그 인에서 지 원하는 원본 제어 플러그 인 API 버전 1.2 및 1.3 기능을 검색할? 고급 기능을 선언 하는 소스 제어 플러그 인 해당 함수를 구현 해야 합니다.

 먼저 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 호출에서 반환 된 값을 확인 합니다 [SccGetVersion](../../extensibility/sccgetversion-function.md)합니다. 1.2 보다 크거나 이어야 합니다.

 다음으로, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 검사 하 여 특정 새 기능이 지원 되는지 여부를 결정 합니다 `lpSccCaps` 의 인수는 [SccInitialize](../../extensibility/sccinitialize-function.md)합니다.

 이러한 조건을 모두 만족 하는 경우 버전 1.2 및 1.3에서에서 지원 되는 새 함수를 호출할 수 있습니다.

## <a name="see-also"></a>참고자료
- [원본 제어 플러그 인 시작](../../extensibility/internals/getting-started-with-source-control-plug-ins.md)