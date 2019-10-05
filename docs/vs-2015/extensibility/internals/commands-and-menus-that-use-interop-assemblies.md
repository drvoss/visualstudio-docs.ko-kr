---
title: 명령 및 Interop 어셈블리를 사용 하는 메뉴 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- menus, using interop assemblies
- interop assemblies, using in commands and menus
- commands, handling using interop assemblies
- command handling with interop assemblies
ms.assetid: 8f4af525-39e5-4e69-92c8-d3efabe80bb2
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ad6b324953914df7103d0dec7371199e3cbbd937
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68195043"
---
# <a name="commands-and-menus-that-use-interop-assemblies"></a>Interop 어셈블리를 사용하는 명령 및 메뉴
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Interop 어셈블리를 사용 하 여 도구 모음 및 메뉴 명령을 구현 하는 VSPackage는 다음 작업을 수행 해야 합니다.  
  
- 알릴는 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 지 원하는 명령 및 현재 사용 여부에 대 한 통합된 개발 환경 (IDE)입니다.  
  
- 명령 처리에 대 한 규칙 (계약)을 준수 합니다.  
  
- 명시적으로 사용 하 여 명령 처리를 구현 합니다 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 또는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> 인터페이스입니다.  
  
  다음은 이러한 작업을 수행 하는 방법을 설명 합니다.  
  
## <a name="in-this-section"></a>섹션 내용  
 [Interop 어셈블리를 사용하여 명령 상태 결정](../../extensibility/internals/determining-command-status-by-using-interop-assemblies.md)  
 VSPackage IDE에 게 알리는 방법을 설명 합니다. 현재 사용 여부 및는 명령에 대 한 지원.  
  
 [Interop 어셈블리의 명령 계약](../../extensibility/internals/command-contracts-in-interop-assemblies.md)  
 Interop 어셈블리를 사용 하 여 명령을 구현 하는 모든 Vspackage에서 사용 하는 기본 명령 계약의 정의 제공 합니다.  
  
 [구현](../../extensibility/internals/command-implementation.md)  
 VSPackage의 명령을 구현 하는 방법의 개요를 제공 합니다.  
  
 [Interop 어셈블리 명령 처리기를 등록](../../extensibility/internals/registering-interop-assembly-command-handlers.md)  
 알림 IDE는 VSPackage 명령 처리기를 제공 하는 데 필요한 레지스트리 항목을 설명 합니다.  
  
## <a name="related-sections"></a>관련 단원  
 [가용성](../../extensibility/internals/command-availability.md)  
 VSPackage 명령을 사용할 수 있고 어떤 개체를 처리 하 고 확인 하려면 IDE에서 사용 되는 조건을 설명 합니다.  
  
 [VSPackage에서 사용자 인터페이스 요소를 추가하는 방법](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)  
 사용 하는 UI를 만드는 방법에 대 한 세부 정보를 제공 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 명령을 지원 합니다.  
  
 [VSPackage의 명령 라우팅](../../extensibility/internals/command-routing-in-vspackages.md)  
 올바른 명령 요청을 사용 하 여 개체를 연결 하는 데 사용 하는 프로세스를 간략하게 설명 합니다.
