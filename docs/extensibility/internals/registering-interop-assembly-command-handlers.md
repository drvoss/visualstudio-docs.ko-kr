---
title: Interop 어셈블리 명령 처리기를 등록 하는 중 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- interop assemblies, command handlers
- command handling with interop assemblies, registering
ms.assetid: 303cd399-e29d-4ea1-8abe-5e0b59c12a0c
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cbc0d162a11df034bec4d1f357ef8abd106da401
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72724697"
---
# <a name="registering-interop-assembly-command-handlers"></a>Interop 어셈블리 명령 처리기를 등록
VSPackage는 IDE (통합 개발 환경)가 해당 명령을 제대로 라우팅하도록 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]에 등록 해야 합니다.

 레지스트리는 수동으로 편집 하거나 등록자 (.rgs) 파일을 사용 하 여 업데이트할 수 있습니다. 자세한 내용은 [Creating Registrar Scripts](/cpp/atl/creating-registrar-scripts)을 참조하십시오.

 MPF (관리 되는 패키지 프레임 워크)는 <xref:Microsoft.VisualStudio.Shell.ProvideMenuResourceAttribute> 클래스를 통해이 기능을 제공 합니다.

- [명령 테이블 형식 참조](https://msdn.microsoft.com/library/09e9c6ef-9863-48de-9483-d45b7b7c798f) 리소스는 관리 되지 않는 위성 UI dll에 있습니다.

## <a name="command-handler-registration-of-a-vspackage"></a>VSPackage의 명령 처리기 등록
 UI (사용자 인터페이스) 기반 명령에 대 한 처리기 역할을 하는 VSPackage에는 VSPackage `GUID` 뒤에 이름이 지정 된 레지스트리 항목이 필요 합니다. 이 레지스트리 항목은 VSPackage UI 리소스 파일의 위치와 해당 파일 내의 메뉴 리소스를 지정 합니다. 레지스트리 항목 자체는 HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio \\ *\<Version >* \menus에 있습니다. 여기서 *\<Version >* 는 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 버전입니다 (예: 9.0).

> [!NOTE]
> @No__t_3 셸이 초기화 될 때 대체 루트를 사용 하 여 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio \\ *\<Version >* 의 루트 경로를 재정의할 수 있습니다. 루트 경로에 대 한 자세한 내용은 [Windows Installer를 사용 하 여 Vspackage 설치](../../extensibility/internals/installing-vspackages-with-windows-installer.md)를 참조 하세요.

### <a name="the-ctmenu-resource-registry-entry"></a>CTMENU 리소스 레지스트리 항목
 레지스트리 항목의 구조는 다음과 같습니다.

```
HKEY_LOCAL_MACHINE\Software\VisualStudio\<Version>\
  Menus\
    <GUID> = <Resource Information>
```

 *GUID*> \< {XXXXXX-XXXX-XXXXXXXXX} 형식의 VSPackage `GUID`입니다.

 *\<Resource 정보 >* 은 쉼표로 구분 된 세 개의 요소로 구성 됩니다. 이러한 요소는 순서 대로 다음과 같습니다.

 *리소스 DLL에 대 한 경로*\< > 메뉴*리소스 ID*> \< 메뉴*버전* \<

 다음 표에서는 \<*리소스 정보*>의 필드에 대해 설명 합니다.

| 요소 | 설명 |
|---------------------------| - |
| *리소스 DLL에 대 한 \< 경로* > | 이는 메뉴 리소스를 포함 하는 리소스 DLL의 전체 경로 이거나 비어 있습니다 .이 경로는 VSPackage의 리소스 DLL이 사용 됨을 나타냅니다 (VSPackage 자체가 등록 된 패키지 하위 키에 지정 된 대로).<br /><br /> 이 필드는 비워 둘 수 있습니다. |
| \<*Menu 리소스 ID* > | VSPackage 파일에서 컴파일된 것 처럼에 대 한 모든 UI 요소를 포함 하는 `CTMENU` 리소스의 리소스 ID입니다 [.](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md) |
| \<*메뉴 버전* > | @No__t_0 리소스에 대 한 버전으로 사용 되는 숫자입니다. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]는이 값을 사용 하 여 `CTMENU` 리소스의 콘텐츠를 모든 `CTMENU` 리소스의 캐시와 다시 병합 해야 하는지 여부를 확인 합니다. 다시 병합은 devenv setup 명령을 실행 하 여 트리거됩니다.<br /><br /> 처음에는이 값을 1로 설정 하 고 `CTMENU` 리소스의 모든 변경 후 다시 병합이 발생 하기 전에 증가 해야 합니다. |

### <a name="example"></a>예제
 다음은 몇 가지 리소스 항목의 예입니다.

```
HKEY_LOCAL_MACHINE\Software\VisualStudio\9.0Exp\
  Menus\
    {019971D6-4685-11D2-B48A-0000F87572EB} = ,1, 10
    {1b027a40-8f43-11d0-8d11-00a0c91bc942} = , 10211, 3
```

## <a name="see-also"></a>참조
- [VSPackage에서 사용자 인터페이스 요소를 추가하는 방법](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Interop 어셈블리를 사용하는 명령 및 메뉴](../../extensibility/internals/commands-and-menus-that-use-interop-assemblies.md)