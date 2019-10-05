---
title: Interop 어셈블리의 계약 명령 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- command handling with interop assemblies, command contracts
- interop assemblies, command contracts
ms.assetid: 57245708-f539-42dc-8963-2754a48f0189
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 50d48d3a8ff55559cce1c3a40142e31b8eebd85f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68195130"
---
# <a name="command-contracts-in-interop-assemblies"></a>Interop 어셈블리의 명령 계약
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

통해 명령을 처리 하는 것에 대 한 기본 계약 합니다 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 인터페이스 호출 하는 환경입니다는 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> 메서드를 확인 하는 명령을 지원 되는지 여부를 고 지원 되는 경우, 해당 상태 및 텍스트를 확인 하려면. 그런 다음 환경은 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> 명령을 실행 하는 방법입니다.  
  
 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> 메서드는 모든 명령에 대 한 동일 하 게 처리 됩니다. 호출 하 여 관리 (예를 들어 드롭 다운 목록)가 필요한 경우 추가 통신을 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> 적절 한 매개 변수를 사용 하 여 메서드. 이러한 매개 변수의 해석은 지정 된 명령에 따라 달라 집니다.  
  
 명령 대상에서 출력 매개 변수 값을 반환 하는 경우 호출자에 게 담당 항상 할당 하는 모든 리소스를 해제 합니다. 이 매개 변수는 variant 이기 때문에 리소스를 해제 변형 선택을 취소 합니다.  
  
 명령을 계층 구조 창 내에서 작동 해야 하는 경우에는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> 인터페이스를 사용 해야 합니다. 합니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> 인터페이스에는 이와 유사한 메서드를 사용 하 여 비슷한 계약: <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> 및 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A>합니다.  
  
## <a name="see-also"></a>관련 항목  
 [Vspackage에서 사용자 인터페이스 요소를 추가 하는 방법](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Vspackage의 명령 라우팅](../../extensibility/internals/command-routing-in-vspackages.md)   
 [구현](../../extensibility/internals/command-implementation.md)
