---
title: 중첩 된 프로젝트에 대 한 항목 추가 대화 상자를 필터링 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- filtering, nested projects
- nested projects, AddItem dialog box filtering
ms.assetid: 5b3e352e-7f18-4f66-be16-b0ad55637ce5
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bc3ff1f85e8c8c71bf8ef16e6fe0c89bf3613f4d
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66328956"
---
# <a name="filter-the-additem-dialog-box-for-nested-projects"></a>중첩 된 프로젝트에 대 한 항목 추가 대화 상자를 필터링 합니다.
표시 하는 경우는 **AddItem** 중첩 된 프로젝트의 경우 부모 프로젝트 대화 상자 대화 상자에서 표시 되는 항목을 제어할 수 있습니다.

 합니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2> 인터페이스를 사용 하면 필터에 있는 노드를 **AddItem** 대화 상자. 자식 프로젝트 표시 되는 경우는 **AddItem** 대화 상자에서 부모를 구현할 수는 `IVsFilterAddProjectItemDlg` 자식 프로젝트에 표시 되는 인터페이스 및 필터 항목입니다.

 프로젝트는 특정 상위 프로젝트 기능별로 그룹화 됩니다, 경우 구현할 수 있습니다 `IVsFilterAddProjectItemDlg` 선택 하면 **프로젝트 항목 추가** 중첩 된 프로젝트의 바로 가기 메뉴. 구현 `IvsFilterAddProjectItemDlg displays` 항목 또는 해당 그룹에 특정 파일을 프로젝트에만 합니다. 다른 그룹에 대 한 프로젝트 항목은 동일한 디렉터리에 저장 되는 경우에 대화 상자에서 필터링 됩니다.

 열리는 경우 합니다 **AddItem** 부모 프로젝트의 구현 자식에 대 한 대화 상자는 `IVsFilterAddProjectItemDlg` 인터페이스 라고 합니다.

 `IVsFilterAddProjectItemDlg` 인터페이스 범주별으로 필터링을 구현할 수도 있습니다. 자세한 내용은 [새 항목 추가 대화 상자에 항목 추가](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md) 하 고 [프로젝트 및 항목 템플릿을 등록](../../extensibility/internals/registering-project-and-item-templates.md)합니다.

## <a name="see-also"></a>참고자료
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>
- [새 항목 추가 대화 상자에 항목 추가](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)
- [프로젝트 및 항목 템플릿을 등록합니다](../../extensibility/internals/registering-project-and-item-templates.md)
- [중첩 프로젝트](../../extensibility/internals/nesting-projects.md)