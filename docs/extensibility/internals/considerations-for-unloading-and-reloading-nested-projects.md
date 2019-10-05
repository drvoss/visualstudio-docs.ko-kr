---
title: 언로드 및 다시 로드에 대 한 고려 사항 중첩 프로젝트 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- nested projects, unloading and reloading
- projects [Visual Studio SDK], unloading and reloading nested
ms.assetid: 06c3427e-c874-45b1-b9af-f68610ed016c
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0a45cf72f09ddf4e5ac1d68b59c2b13e64982744
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66335548"
---
# <a name="considerations-for-unloading-and-reloading-nested-projects"></a>중첩 된 프로젝트를 다시 로드 및 언로드 시 고려 사항

중첩 된 프로젝트 형식에서 구현 하는 경우에 언로드하고 프로젝트 다시 로드 하는 경우 추가 단계를 수행 해야 합니다. 올바르게 알리도록 솔루션 이벤트에 대 한 수신기를 올바르게 올려야 합니다 `OnBeforeUnloadProject` 고 `OnAfterLoadProject` 이벤트입니다.

이러한 이벤트를 발생 시키는 한 가지 이유는 소스 코드 제어 (SCC)입니다. 서버에서 항목을 삭제 한 다음에 추가 하는 SCC 하지 않으려면으로 다시 *새* 경우는 `Get` SCC에서 작업 합니다. 이 경우 새 파일을 SCC에서 로드 됩니다. 언로드하고 다른 지 알아두면 경우 모든 파일을 다시 로드 해야 합니다.

원본 코드 제어 호출 `ReloadItem`합니다. 구현 된 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents> 호출에 대 한 인터페이스 `OnBeforeUnloadProject` 및 `OnAfterLoadProject` 프로젝트를 삭제 하 고 다시 만들어야 합니다. 이러한 방식으로 인터페이스를 구현 하면 SCC는 프로젝트를 일시적으로 삭제 및 다시 추가 알림을 받습니다. 프로젝트 것 처럼 소스 코드 제어 프로젝트에서 작동 하지 않고는 따라서 *실제로* 삭제 되었다가 다시 추가 합니다.

## <a name="reload-projects"></a>프로젝트 다시 로드

중첩 된 프로젝트 다시 로드를 지원 하려면 구현 합니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> 메서드. 구현에서 `ReloadItem`, 중첩 된 프로젝트를 닫고 다시 만듭니다.

일반적으로 프로젝트를 다시 로드할 때 IDE 발생 합니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnBeforeUnloadProject%2A> 및 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterLoadProject%2A> 이벤트입니다. 그러나 부모 프로젝트는 삭제 되며 다시 로드 하는 중첩 된 프로젝트에 대 한 IDE 하지 프로세스를 시작 합니다. 부모 프로젝트 솔루션 이벤트를 발생 하지 않음 이므로 IDE에 프로세스의 초기화에 대 한 정보가 없으므로 이벤트가 발생 되지 않습니다.

부모 프로젝트 호출 하 여이 프로세스를 처리할 `QueryInterface` 에 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents> 인터페이스입니다. `IVsFireSolutionEvents` 시키려면 IDE에 지시 하는 함수에는 `OnBeforeUnloadProject` 중첩 된 프로젝트를 언로드하고 제기 이벤트는 `OnAfterLoadProject` 동일한 프로젝트를 다시 로드 하는 이벤트입니다.

## <a name="see-also"></a>참고자료

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>
- [중첩 프로젝트](../../extensibility/internals/nesting-projects.md)