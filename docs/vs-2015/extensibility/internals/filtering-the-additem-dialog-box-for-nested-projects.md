---
title: 중첩 된 프로젝트에 대 한 항목 추가 대화 상자를 필터링 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- filtering, nested projects
- nested projects, AddItem dialog box filtering
ms.assetid: 5b3e352e-7f18-4f66-be16-b0ad55637ce5
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7bb98eac2bc481aa5e3652144dfbcadf70430d04
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62538098"
---
# <a name="filtering-the-additem-dialog-box-for-nested-projects"></a>중첩된 프로젝트에 대한 AddItem 필터링 대화 상자
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

표시 하는 경우는 **AddItem** 중첩 된 프로젝트의 경우 부모 프로젝트 대화 상자 대화 상자에서 표시 되는 항목을 제어할 수 있습니다.  
  
 합니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2> 인터페이스를 사용 하면 필터에 있는 노드를 **AddItem** 대화 상자. 자식 프로젝트 표시 되는 경우는 **AddItem** 대화 상자에서 부모를 구현할 수는 `IVsFilterAddProjectItemDlg` 자식 프로젝트에 표시 되는 인터페이스 및 필터 항목입니다.  
  
 프로젝트는 특정 상위 프로젝트 기능별로 그룹화 됩니다, 경우 구현할 수 있습니다 `IVsFilterAddProjectItemDlg` 선택 하면 **프로젝트 항목 추가** 중첩 된 프로젝트의 바로 가기 메뉴. 구현 `IvsFilterAddProjectItemDlg displays` 항목 또는 해당 그룹에 특정 파일을 프로젝트에만 합니다. 다른 그룹에 대 한 프로젝트 항목은 동일한 디렉터리에 저장 되는 경우에 대화 상자에서 필터링 됩니다.  
  
 열리는 경우 합니다 **AddItem** 부모 프로젝트의 구현 자식에 대 한 대화 상자는 `IVsFilterAddProjectItemDlg` 인터페이스 라고 합니다.  
  
 `IVsFilterAddProjectItemDlg` 인터페이스 범주별으로 필터링을 구현할 수도 있습니다. 자세한 내용은 [새 항목 추가 대화 상자에 항목 추가](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md) 하 고 [등록 프로젝트 및 항목 템플릿](../../extensibility/internals/registering-project-and-item-templates.md)합니다.  
  
## <a name="see-also"></a>참고 항목  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>   
 [항목에 추가 된 새 항목 추가 대화 상자](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)   
 [프로젝트 및 항목 템플릿 등록](../../extensibility/internals/registering-project-and-item-templates.md)   
 [프로젝트 중첩](../../extensibility/internals/nesting-projects.md)
