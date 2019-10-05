---
title: Interop 어셈블리를 사용 하 여 명령 상태 결정 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- interop assemblies, determining command status
- command handling with interop assemblies, status
ms.assetid: 2f5104d1-7b4c-4ca0-a626-50530a8f7f5c
caps.latest.revision: 19
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: fc67123e082258932ab5df6613941f869d6049a6
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68196783"
---
# <a name="determining-command-status-by-using-interop-assemblies"></a>Interop 어셈블리를 사용하여 명령 상태 결정
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

VSPackage 해야 기록해 상태의 명령 처리할 수 있습니다. VSPackage 내에서 처리 명령을 설정 또는 해제 하는 경우 환경이 확인할 수 없습니다. 이 명령은 상태에 대 한 환경에 알림을 보내야 VSPackage의 경우, 예를 들어 일반 상태 같은 명령은 **잘라내기**를 **복사본**, 및 **붙여넣기**합니다.  
  
## <a name="status-notification-sources"></a>상태 알림 원본  
 환경을 통해 Vspackage의 명령에 대 한 정보를 받는 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> VSPackage 구현에 참가 하는 메서드를의 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 인터페이스입니다. 환경은 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> 메서드의 VSPackage 두 가지 조건:  
  
- 환경을 실행 하는 사용자가 열면 주 메뉴 또는 상황에 맞는 메뉴 (마우스 오른쪽 단추로 클릭) 하 여,는 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> 메서드를 모든 해당 상태를 확인 하려면 해당 메뉴 명령이 있습니다.  
  
- VSPackage 환경 현재 사용자 인터페이스 (UI)를 업데이트 하는 요청 하는 경우 와 같은 사용자에 게 현재 표시 되는 명령으로 이런 합니다 **잘라내기**를 **복사본**, 및 **붙여넣기** 표준 도구 모음의 그룹화, 될 활성화 및 비활성화 컨텍스트 및 사용자 작업에 응답 합니다.  
  
  여러 Vspackage를 호스팅하는 셸 이므로 명령 상태를 확인 하려면 각 VSPackage를 폴링하여 요청 된 경우 셸 성능은 크게 저하 됩니다. 대신, VSPackage 적극적으로 알려야 환경 UI 변경 시 변경 될 때입니다. 업데이트 알림에 대 한 자세한 내용은 참조 하세요. [사용자 인터페이스 업데이트](../../extensibility/updating-the-user-interface.md)합니다.  
  
## <a name="status-notification-failure"></a>상태 알림 오류  
 명령 상태 변경의 환경에 알리기 위해 VSPackage의 오류는 일관성이 없는 상태에서 UI를 배치할 수 있습니다. 메뉴 또는 상황에 맞는 메뉴 명령을 중 하나에 배치할 수 도구 모음을 사용자가 해야 합니다. 따라서 UI를 업데이트 하 여 메뉴 또는 상황에 맞는 메뉴가 열리면 충분 하지 않습니다.  
  
## <a name="see-also"></a>관련 항목  
 [Vspackage에서 사용자 인터페이스 요소를 추가 하는 방법](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [구현](../../extensibility/internals/command-implementation.md)
