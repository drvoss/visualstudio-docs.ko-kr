---
title: Interop 어셈블리 명령 처리기를 등록 합니다. | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- interop assemblies, command handlers
- command handling with interop assemblies, registering
ms.assetid: 303cd399-e29d-4ea1-8abe-5e0b59c12a0c
caps.latest.revision: 20
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 9d2822e9eef36806f5c251813925fb4244242519
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65705809"
---
# <a name="registering-interop-assembly-command-handlers"></a>Interop 어셈블리 명령 처리기를 등록
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

VSPackage를 등록 해야 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 는 통합된 개발 환경 (IDE)는 해당 명령을 올바르게 라우팅합니다.  
  
 수동 편집 하거나 등록자 (.rgs) 파일을 사용 하 여 레지스트리를 업데이트할 수 있습니다. 자세한 내용은 [Creating Registrar Scripts](https://msdn.microsoft.com/library/cbd5024b-8061-4a71-be65-7fee90374a35)을 참조하십시오.  
  
 관리 패키지 프레임 워크 (MPF)를 통해이 기능을 제공 합니다 <xref:Microsoft.VisualStudio.Shell.ProvideMenuResourceAttribute> 클래스입니다.  
  
 [명령 테이블 형식을 참조](https://msdn.microsoft.com/09e9c6ef-9863-48de-9483-d45b7b7c798f) 리소스가 관리 되지 않는 위성 dll UI에에서 있습니다.  
  
## <a name="command-handler-registration-of-a-vspackage"></a>VSPackage의 명령 처리기 등록  
 사용자 인터페이스 (UI)에 대 한 처리기 역할을 하는 VSPackage-기반된 명령을 VSPackage의 이름을 딴 하는 레지스트리 항목이 있어야 `GUID`합니다. 이 레지스트리 항목 VSPackage의 UI 리소스 파일과 해당 파일 내에서 메뉴 리소스의 위치를 지정 합니다. HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio 아래에 있는 레지스트리 항목 자체\\ *\<버전 >* \Menus, 여기서  *\<버전 >* 버전이 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]예를 들어 9.0, 합니다.  
  
> [!NOTE]
> HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio의 루트 경로\\ *\<버전 >* 대체를 사용 하 여 재정의할 수 있습니다 때 루트는 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 셸 초기화 됩니다. 루트 경로 대 한 자세한 내용은 참조 하세요. [Windows Installer를 사용 하 여 Vspackage 설치](../../extensibility/internals/installing-vspackages-with-windows-installer.md)합니다.  
  
### <a name="the-ctmenu-resource-registry-entry"></a>CTMENU 리소스 레지스트리 항목  
 레지스트리 항목의 구조는:  
  
```  
HKEY_LOCAL_MACHINE\Software\VisualStudio\<Version>\  
  Menus\  
    <GUID> = <Resource Information>  
```  
  
 \<*GUID*>는 `GUID` {XXXXXX-XXXX-XXXX-XXXX-XXXXXXXXX} 형태로 VSPackage의 합니다.  
  
 *\<리소스 정보 >* 쉼표로 구분 된 세 가지 요소로 구성 됩니다. 이러한 요소는 순서 대로:  
  
 \<*리소스 DLL에 대 한 경로*>, \< *메뉴 리소스 ID*>, \< *메뉴 버전*>  
  
 다음 표에서 설명 필드 \< *자원 정보*>.  
  
|요소|설명|  
|-------------|-----------------|  
|\<*리소스 DLL 경로*>|이 리소스 메뉴 리소스를 포함 하는 DLL의 전체 경로 또는이 비어 VSPackage의 리소스 DLL 임을 나타내는 데 사용할 (자체 VSPackage 등록 되어 있는 패키지 하위 키에 지정 된 대로).<br /><br /> 것에이 필드를 비워 둡니다.|  
|\<*메뉴 리소스 ID*>|리소스 id를 `CTMENU` 에서 컴파일된 VSPackage에 대 한 모든 UI 요소를 포함 하는 리소스를 [.vsct](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md) 파일입니다.|  
|\<*메뉴 버전*>|이 버전으로 사용 되는 숫자는 `CTMENU` 리소스입니다. [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 이 값을 사용 하 여 내용의 remerge 해야 하는지 확인 합니다 `CTMENU` 모든 캐시를 사용 하 여 리소스 `CTMENU` 리소스. remerge devenv 설치 명령을 실행 하 여 트리거됩니다.<br /><br /> 이 값을 1로 설정 및 변경 될 때마다 다음 증가 처음에 해야는 `CTMENU` 리소스는 remerge 발생 전에 합니다.|  
  
### <a name="example"></a>예제  
 두 리소스 항목의 예는 다음과 같습니다.  
  
```  
HKEY_LOCAL_MACHINE\Software\VisualStudio\9.0Exp\  
  Menus\  
    {019971D6-4685-11D2-B48A-0000F87572EB} = ,1, 10  
    {1b027a40-8f43-11d0-8d11-00a0c91bc942} = , 10211, 3  
```  
  
## <a name="see-also"></a>참고 항목  
 [Vspackage에서 사용자 인터페이스 요소를 추가 하는 방법](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Interop 어셈블리를 사용하는 명령 및 메뉴](../../extensibility/internals/commands-and-menus-that-use-interop-assemblies.md)
