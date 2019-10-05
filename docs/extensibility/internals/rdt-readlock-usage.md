---
title: RDT_ReadLock 사용법 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- RDT_ReadLock
- visible
- RDT_EditLock
- invisible
ms.assetid: b935fc82-9d6b-4a8d-9b70-e9a5c5ad4a55
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8c11cee4c1f8c150fc8bcf42b3dbc1a193d3441a
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66341352"
---
# <a name="rdtreadlock-usage"></a>RDT_ReadLock 사용법

[_VSRDTFLAGS 합니다. RDT_ReadLock](<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS.RDT_ReadLock>) 는 Visual Studio IDE에서 현재 열려 있는 모든 문서 목록에는 실행 중인 문서 테이블 RDT (), 문서를 잠그기 위한 논리를 제공 하는 플래그입니다. 이 플래그는 문서를 열 때 및 사용자 인터페이스에 표시 되거나 켜지 메모리에에서 보관 된 문서 인지 확인 합니다.

일반적으로 사용할 [_VSRDTFLAGS 합니다. RDT_ReadLock](<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS.RDT_ReadLock>) 다음 중 하나가 true 인 경우:

- 문서를 시각적으로 열려고 할 읽기 전용 및 해당 되지 않으므로 설정 하지만 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> 소유 해야 합니다.

- 사용자가 시각적으로 열려 있는 하지 사용자 UI에 표시 하 고 닫습니다 하려고 하기 전에 문서를 저장 하 라는 메시지가 표시 해야 합니다.

## <a name="how-to-manage-visible-and-invisible-documents"></a>표시 되 고 보이지 않는 문서를 관리 하는 방법

사용자가 ui에서 문서를 열면를 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> 문서에 대 한 소유자를 설정 해야 및 [_VSRDTFLAGS 합니다. RDT_EditLock](<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS.RDT_EditLock>) 플래그를 설정 해야 합니다. 없으면 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> 소유자를 설정할 수 있습니다, 다음 문서를 클릭할 때 저장 되지 것입니다 **모두 저장** 또는 IDE를 닫습니다. 이 경우는 문서가 열려 있지 않으면 보이지 않게 메모리에서 수정 및 사용자가 종료 시 문서를 저장 하 라는 메시지가 표시 하거나 저장 하는 경우 의미 **모두 저장** 을 선택 하면는 `RDT_ReadLock` 사용할 수 없습니다. 대신 사용 해야 합니다는 `RDT_EditLock` 등록 하 고는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder> 경우는 [__VSREGDOCLOCKHOLDER 합니다. RDLH_WeakLockHolder](<xref:Microsoft.VisualStudio.Shell.Interop.__VSREGDOCLOCKHOLDER.RDLH_WeakLockHolder>) 플래그입니다.

## <a name="rdteditlock-and-document-modification"></a>RDT_EditLock 및 문서 수정

언급 된 이전 플래그를 나타내는 문서를 여는 보이지 않는 양보할 해당 `RDT_EditLock` 문서를 열면 사용자에 표시 되 **참조 하시기 바랍니다**합니다. 이 문제가 발생 하면 사용자가 사용 하 여 표시 됩니다는 **저장** 경우 프롬프트를 표시 **참조 하시기 바랍니다** 닫혀 합니다. `Microsoft.VisualStudio.Package.Automation.OAProject.CodeModel` 구현을 사용 하는 합니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsInvisibleEditorManager> 때만 처음에 서비스 작업을 `RDT_ReadLock` 때 수행 되 (즉, 문서가 열려 있지 시각적으로 정보를 구문 분석). 나중에 문서를 수정 해야 하는 경우 다음 잠금을 업그레이드 됩니다 약한 **RDT_EditLock**합니다. 표시 되 후 문서를 열 경우 **참조 하시기 바랍니다**의 `CodeModel`의 약한 `RDT_EditLock` 해제 됩니다.

후 닫으면 합니다 **참조 하시기 바랍니다** 를 선택 하 고 **없음** 열린 문서를 저장 하 라는 메시지가 나타나면 해당 `CodeModel` 구현 문서에서 모든 정보를 삭제 및 다시 열립니다는 문서에 대 한 자세한 내용은 반드시 다음 시간 켜지 디스크에서 문서입니다. 이 동작의 미묘한 문제가 있는 사용자가 인스턴스가 합니다 **참조 하시기 바랍니다** 수정 보이지 않는 열린 문서의 닫고 및 그런 다음 선택 **No** 문서를 저장 하 라는 메시지가 나타나면 합니다. 이 경우 문서에는 `RDT_ReadLock`, 다음 문서 실제로 닫히지 것입니다 및 사용자가 문서를 저장할 필요가 있는 경우에 수정된 된 문서를 메모리에서 켜지 열기 유지 됩니다.

문서를 여는 보이지 않는 약한을 사용 하는 경우 `RDT_EditLock`, 사용자 문서를 시각적으로 열고, 다른 잠금이 보유 되지 경우에 해당 잠금의 생성 합니다. 사용자가 닫을 때 합니다 **참조 하시기 바랍니다** 를 선택 하 고 **No** 문서를 저장 하는 메시지가 표시 되 면 다음 문서를 닫아야 합니다. 메모리에서. 즉, 보이지 않는 클라이언트 RDT 추적할 이벤트를이 발생에 대 한 수신 대기 해야 합니다. 문서는 필요한 경우 다음에 문서 다시 열 수 있어야 합니다.