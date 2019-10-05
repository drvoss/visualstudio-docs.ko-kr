---
title: 언로드 및 다시 로드에 대 한 고려 사항 중첩 프로젝트 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- nested projects, unloading and reloading
- projects [Visual Studio SDK], unloading and reloading nested
ms.assetid: 06c3427e-c874-45b1-b9af-f68610ed016c
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 65145530c8cd6b68b82391a09b395bb8c9a61117
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68197007"
---
# <a name="considerations-for-unloading-and-reloading-nested-projects"></a>중첩된 프로젝트 언로드 및 다시 로드에 대한 고려 사항
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

중첩 된 프로젝트 형식에서 구현 하는 경우에 언로드하고 프로젝트 다시 로드 하는 경우 추가 단계를 수행 해야 합니다. 올바르게 알리도록 솔루션 이벤트에 대 한 수신기를 올바르게 올려야 합니다 `OnBeforeUnloadProject` 고 `OnAfterLoadProject` 이벤트입니다.  
  
 이 방식으로 이러한 이벤트를 발생 시켜야 하는 한 가지 이유는 소스 코드 제어 (SCC) 서버에서 항목을 삭제 하 고 다음 없는 경우 새로운로 하 고 다시 추가 하지 않을 `Get` SCC에서 작업 합니다. 이런 경우 소스 코드 제어에서 새 파일을 로드할 수는 있으며 언로드하고 다른 경우 모든 파일을 다시 로드 해야 합니다. SCC 호출 `ReloadItem`합니다. 해당 호출의 구현 프로젝트를 삭제 하 고 다시 구현 하 여 다시 만들어야 하는 것 `IVsFireSolutionEvents` 호출할 `OnBeforeUnloadProject` 및 `OnAfterLoadProject`합니다. 이 이것을 수행 하면 SCC는 프로젝트를 일시적으로 삭제 및 다시 추가 알림을 받습니다. 따라서 SCC 프로젝트 서버에서 실제로 삭제 되었으며 다시 추가 하는 경우에 따라 프로젝트에서 작동 하지 않습니다.  
  
## <a name="reloading-projects"></a>프로젝트 다시 로드  
 중첩 된 프로젝트 다시 로드를 지원 하려면 구현 합니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> 메서드. 구현에서 `ReloadItem`, 중첩 된 프로젝트를 닫고 다시 만듭니다.  
  
 일반적으로 프로젝트를 다시 로드할 때 IDE 발생 합니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnBeforeUnloadProject%2A> 하며 `M:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterLoadProject(Microsoft.VisualStudio.Shell.Interop.IVsHierarchy,Microsoft.VisualStudio.Shell.Interop.IVsHierarchy)` 이벤트입니다. 그러나 부모 프로젝트를 삭제 하 고 다시 로드 하는 중첩 된 프로젝트에 대 한 IDE 하지 프로세스를 시작 합니다. 부모 프로젝트 솔루션 이벤트를 발생 시 키 지 않습니다 이므로 IDE에 프로세스의 초기화에 대 한 정보가 없으므로 이벤트를 발생 하지 않습니다.  
  
 부모 프로젝트 호출 하 여이 프로세스를 처리 하 `QueryInterface` 에 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents> 해제 인터페이스는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution> 인터페이스입니다. `IVsFireSolutionEvents` 시키려면 IDE에 지시 하는 함수에는 `OnBeforeUnloadProject` 중첩 된 프로젝트를 언로드하고 제기 이벤트는 `OnAfterLoadProject` 동일한 프로젝트를 다시 로드 하는 이벤트입니다.  
  
## <a name="see-also"></a>관련 항목  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>   
 [프로젝트 중첩](../../extensibility/internals/nesting-projects.md)
