---
title: Windows 레지스트리에서 도구 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- tool windows, registering
ms.assetid: c4bb8add-7148-49e4-a377-01d059fd5524
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8cedb95ccd98c3d5bd5e05086cfd1b53b0f97cd9
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68186378"
---
# <a name="tool-windows-in-the-registry"></a>레지스트리의 도구 창
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

도구 창을 제공 하는 Vspackage를 등록 해야 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 으로 도구 창 공급자입니다. Visual Studio 패키지 템플릿을 사용 하 여 만든 도구 windows는 기본적으로이 작업을 수행 합니다. 도구 창 공급자는 기본 도구 창 크기 및 위치에 도구 창 및 도킹 스타일으로 사용 하는 창의 GUID 등의 표시 유형 특성을 지정 하는 시스템 레지스트리 키를 있습니다.  
  
 관리 되는 도구 창 공급자는 개발 하는 동안 소스 코드에 특성을 추가 하 고 다음 결과 어셈블리에서 RegPkg.exe 유틸리티가 실행 하 여 도구 창을 등록 합니다. 자세한 내용은 [도구 창 등록](../extensibility/registering-a-tool-window.md)합니다.  
  
## <a name="registering-unmanaged-tool-window-providers"></a>관리 되지 않는 도구 창 공급자 등록  
 관리 되지 않는 도구 창 공급자에 등록 해야 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 시스템 레지스트리 ToolWindows 섹션에서입니다. 다음.reg 파일 조각은 동적 도구 창을 등록 하는 방법을 보여 줍니다.  
  
```  
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\<version number>\ToolWindows\{f0e1e9a1-9860-484d-ad5d-367d79aabf55}]  
@="{01069cdd-95ce-4620-ac21-ddff6c57f012}"  
"Name"="Microsoft.Samples.VisualStudio.IDE.ToolWindow.DynamicWindowPane"  
"Float"="250, 250, 410, 430"  
"DontForceCreate"=dword:00000001  
  
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\ToolWindows\{f0e1e9a1-9860-484d-ad5d-367d79aabf55}\Visibility]  
"{f1536ef8-92ec-443c-9ed7-fdadf150da82}"=dword:00000000  
```  
  
 위의 예제에서 첫 번째 키, 버전 번호는 버전의 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]등 7.1 또는 8.0, 하위 키 {0} f0e1e9a1-9860-484d-ad5d-367d79aabf55} 도구 창 (DynamicWindowPane) 및 기본 값 {GUID입니다. 01069cdd-95ce-4620-ac21-ddff6c57f012}에 도구 창을 제공 하는 VSPackage의 GUID입니다. 에 대 한 설명은 Float 및 DontForceCreate 하위 키를 참조 하세요 [도구 창 표시 구성](../extensibility/tool-window-display-configuration.md)합니다.  
  
 두 번째 선택적 키 ToolWindows\Visibility, 도구 창 표시 되도록 해야 하는 명령의 Guid를 지정 합니다. 이 경우 지정 된 명령이 없는 경우 자세한 내용은 [도구 창 표시 구성](../extensibility/tool-window-display-configuration.md)합니다.  
  
## <a name="see-also"></a>참고 항목  
 [VSPackage Essentials](../misc/vspackage-essentials.md)
