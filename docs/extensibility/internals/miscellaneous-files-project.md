---
title: 기타 파일 프로젝트 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- files, adding existing files to solutions
- Miscellaneous Files project
- Solution Items folder
- files, opening with Miscellaneous Files project
ms.assetid: 93a278a8-d4f4-400b-8945-4f1b0a2b5bac
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dd3cf792b10905d0f124266601e791dc91259ce2
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66349285"
---
# <a name="miscellaneous-files-project"></a>기타 파일 프로젝트
사용자가 프로젝트 항목을 열면 IDE 솔루션의 모든 프로젝트의 멤버가 아닌 모든 항목을 기타 파일 프로젝트에 할당 합니다.

 프로젝트는 사용자 프로젝트 항목을 열면 편집기 사용 되었는지 확인 하는 데 중요 한 역할을 재생 합니다. 프로젝트별 편집기 또는 표준 편집기를 사용 하 여 특정 파일을 열려는 프로젝트를 디자인할 수 있습니다.

 프로젝트별 편집기는 일반적으로 사용자 한 전문 지식이 있거나 프로젝트에서 특별 한 인터페이스를 사용 해야 합니다. 자세한 내용은 [방법: 프로젝트별 편집기 열기](../../extensibility/how-to-open-project-specific-editors.md)합니다.

 표준 편집기 프로젝트에서 특정 확장명의 파일을 열 수 있습니다. 사용자는와 같은 일부 표준 편집기를 지정할 수 있습니다는 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 프로젝트에 대 한 텍스트 편집기에는 있지만 해당 공용 문자 유지 합니다. 표준 편집기를 사용 하 여 만들어진 여 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> 메서드.

 솔루션에 프로젝트가 없습니다. 프로젝트 항목을 열 수 있도록이 응답 하는 경우 IDE는 모든 파일을 엽니다는 기타 파일 프로젝트 라는 특수 프로젝트를 제공 합니다.

 이 특수 프로젝트를 프로젝트의 컨텍스트 외부에서 파일 열기를 제공합니다. 처리 하는 동안는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenDocumentViaProject%2A> 메서드, 기타 파일 프로젝트에는 매우 낮은 우선 순위를 사용 하 여 항상 응답 합니다. 따라서 항상 기타 파일 프로젝트 파일을 열 수 있는 우선 순위가 높은 프로젝트에 생성 합니다.

 기타 파일 프로젝트에 사용자가 명시적으로 사용 하 여 만들 수 않아도 합니다 **새 프로젝트** 대화 상자. 또한 기타 파일 프로젝트 프로젝트 멤버 목록의 영구적으로 관리 하지 않습니다. 선택적 기능을 사용 하 여 각 사용자에 대해 가장 최근에 사용한 파일 목록이 기록.

## <a name="see-also"></a>참고 항목
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument>
- <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY>
- [방법: 프로젝트별 편집기 열기](../../extensibility/how-to-open-project-specific-editors.md)
- [방법: 표준 편집기 열기](../../extensibility/how-to-open-standard-editors.md)
- [프로젝트 및 프로젝트 항목 템플릿 추가](../../extensibility/internals/adding-project-and-project-item-templates.md)
- [프로젝트 및 프로젝트 항목 템플릿 추가](../../extensibility/internals/adding-project-and-project-item-templates.md)