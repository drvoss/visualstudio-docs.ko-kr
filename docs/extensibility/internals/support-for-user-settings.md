---
title: 사용자 설정에 대 한 지원 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Custom Settings Points
- user settings [Visual Studio SDK], registering persistence support
- persistence, registering settings
ms.assetid: ad9beac3-4f8d-4093-ad0e-6fb00444a709
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 90f04d5657fb6f680139ee6de5a47625304b5dbd
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66309754"
---
# <a name="support-for-user-settings"></a>사용자 설정 지원
VSPackage를 사용자가 유지 되는 상태 변수 그룹이 있는 하나 이상의 설정 범주를 정의할 수 있습니다 합니다 **설정 가져오기/내보내기** 명령을 합니다 **도구** 메뉴. 이 지 속성을 사용 하려면 설정을 Api 사용에 [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]합니다.

 사용자 지정 설정 지점 및 GUID 라고 하는 레지스트리 항목을 VSPackage의 설정 범주를 정의 합니다. VSPackage는 여러 설정 범주를 지원할 수 있습니다, 그리고 각각 사용자 지정 설정 지점으로 정의 합니다.

- Interop 어셈블리를 기반으로 하는 설정의 구현 (사용 하 여는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings> 인터페이스) 레지스트리를 편집 하거나 등록자 스크립트 (.rgs 파일)를 사용 하 여 사용자 지정 설정 지점 만들어야 합니다. 자세한 내용은 [Creating Registrar Scripts](/cpp/atl/creating-registrar-scripts)을 참조하십시오.

- 관리 패키지 프레임 워크 (MPF)를 사용 하는 코드를 연결 하 여 사용자 지정 설정 지점을 만들어야는 <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> 각 사용자 지정 설정 지점에 대 한 vspackage입니다.

     단일 VSPackage는 여러 사용자 지정 설정 지점을 지원, 각 사용자 지정 설정 지점은 별도 클래스로 구현 되 고 각각의 고유 인스턴스를 등록 된 경우는 <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> 클래스입니다. 따라서 클래스를 구현 하는 설정을 여러 개 설정 범주를 지원할 수 있습니다.

## <a name="custom-settings-point-registry-entry-details"></a>사용자 지정 설정 지점 레지스트리 항목 세부 정보
 다음 위치에 레지스트리 항목을 사용자 지정 설정 지점은 생성 됩니다. HKLM\Software\Microsoft\VisualStudio\\ *\<버전 >* \UserSettings\\`<CSPName>`여기서 `<CSPName>` 에서 VSPackage에서 지 원하는 사용자 지정 설정 지점 이름으로는 및  *\<버전 >* 의 버전이 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], 예를 들어 8.0입니다.

> [!NOTE]
> 루트 경로의 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\\ *\<버전 >* 대체를 사용 하 여 재정의할 수 있습니다 때 루트는 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 통합된 개발 환경 (IDE)가 초기화 합니다. 자세한 내용은 [명령줄 스위치](../../extensibility/command-line-switches-visual-studio-sdk.md)합니다.

 레지스트리 항목의 구조는 아래 나와 있습니다.

 HKLM\Software\Microsoft\VisualStudio\\ *\<Version>* \UserSettings\

 `<CSPName`> = ' #12345 ' s

 패키지 = ' {XXXXXX XXXX XXXX XXXX XXXXXXXXX}'

 범주 = ' {YYYYYY YYYY YYYY YYYY YYYYYYYYY}'

 ResourcePackage = '{ZZZZZZ ZZZZ ZZZZ ZZZZ ZZZZZZZZZ}'

 AlternateParent CategoryName =

| 이름 | 형식 | 데이터 | 설명 |
|-----------------|--------| - | - |
| (기본값) | REG_SZ | 사용자 지정 설정 지점 이름 | 키의 이름, `<CSPName`>을 사용자 지정 설정 지점의 지역화 되지 않은 이름입니다.<br /><br /> MPF 기반 구현에 대 한 키의 이름을 결합 하 여 가져온 합니다 `categoryName` 및 `objectName` 인수를 <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> 생성자에 `categoryName_objectName`입니다.<br /><br /> 키를 비워 둘 수, 또는 위성 DLL에서에서 지역화 된 문자열에 대 한 참조 ID를 포함할 수 있습니다. 이 값에서 가져온 합니다 `objectNameResourceID` 인수는 <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> 생성자. |
| Package | REG_SZ | GUID | 사용자 지정 설정 지점 구현 하는 VSPackage의 GUID입니다.<br /><br /> 구현 MPF를 사용 하 여 기반를 <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> 클래스, 생성자를 사용 `objectType` VSPackage를 포함 하는 인수 <xref:System.Type> 및이 값을 얻는 리플렉션 합니다. |
| 범주 | REG_SZ | GUID | 설정 범주를 식별 하는 GUID입니다.<br /><br /> Interop 어셈블리 기반 구현에 대 한이 값을 임의로 선택한 수 GUID는를 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE를 전달 합니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ExportSettings%2A> 및 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ImportSettings%2A> 메서드. 이러한 두 가지 방법의 모든 구현이 해당 GUID 인수를 확인 해야 합니다.<br /><br /> MPF 기반 구현에 대 한이 GUID에서 가져온 합니다 <xref:System.Type> 구현 하는 클래스의는 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 설정 메커니즘입니다. |
| ResourcePackage | REG_SZ | GUID | 선택 사항입니다.<br /><br /> VSPackage 구현에서 제공 하지 않는 경우 문자열을 지역화 하는 위성 DLL에 포함 된 경로입니다.<br /><br /> MPF 리플렉션을 사용 하 여 VSPackage를 올바른 리소스를 가져와야 하므로 <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> 클래스는이 인수를 설정 하지 않습니다. |
| AlternateParent | REG_SZ | 이 사용자 지정 설정 지점이 포함 된 도구 옵션 페이지 아래에 있는 폴더의 이름입니다. | 선택 사항입니다.<br /><br /> 설정 구현을 지 원하는 경우에이 값을 설정 해야 **도구 옵션** 의 지 속성 메커니즘을 사용 하는 페이지는 [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] 상태를 저장 하도록 자동화 모델의 메커니즘을 대신 합니다.<br /><br /> AlternateParent 키 값이 이러한 경우에는 `topic` 의 섹션을 `topic.sub-topic` 문자열 특정을 식별 하는 데 **ToolsOptions** 페이지. 예를 들어 합니다 **ToolsOptions** 페이지 `"TextEditor.Basic"` AlternateParent 값 `"TextEditor"`합니다.<br /><br /> 때 <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> 생성 사용자 지정 설정 지점 범주 이름으로 동일 합니다. |
