---
title: '방법: 표준 편집기 열기 | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], opening
- projects [Visual Studio SDK], opening standard editors
ms.assetid: d5ce10f9-047a-4b74-aa1d-295128898b89
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1c85ab7f10881d76fbefea471851007f3d13da9b
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66325455"
---
# <a name="how-to-open-standard-editors"></a>방법: 표준 편집기 열기
표준 편집기를 열면 IDE 파일에 대 한 프로젝트별 편집기를 지정 하는 대신 지정 된 파일 형식에 대해 표준 편집기를 확인 하 게 있습니다.

 구현 하려면 다음 절차를 완료 합니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A> 메서드. 프로젝트 파일을 표준 편집기에서 열립니다.

## <a name="to-implement-the-openitem-method-with-a-standard-editor"></a>표준 편집기를 사용 하 여 OpenItem 메서드를 구현 합니다.

1. 호출 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable> (`RDT_EditLock`) 문서 데이터 개체 파일은 이미 열려 있는지 여부를 확인 하려면.

2. 파일이 이미 열려 있으면 파일을 호출 하 여 resurface 합니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.IsDocumentOpen%2A> 값을 지정 하는 메서드를 `IDO_ActivateIfOpen` 에 대 한는 `grfIDO` 매개 변수입니다.

     열려 있는 파일 및 문서 호출 프로젝트에 보다 다양 한 프로젝트에서 소유 하 고, 프로젝트가 다른 프로젝트에서 열려 있는 편집기는 경고를 받습니다. 파일 창이 다음 표시 됩니다.

3. 문서가 열려 있지 않으면, 실행 중인 문서 테이블에 없는 호출을 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> 메서드 (`OSE_ChooseBestStdEditor`) 파일에 대 한 표준 편집기를 엽니다.

     메서드를 호출 하는 경우 IDE는 다음 작업을 수행 합니다.

    1. IDE 편집기 검색 / {guidEditorType}는 편집기를 확인 하려면 레지스트리에서 하위 키 확장 파일을 열 수와이 작업을 수행 하는 것에 대 한 가장 높은 우선 순위를 갖습니다.

    2. IDE를 호출 하는 IDE에는 편집기 파일을 열 수를 확인 후 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>합니다. 편집기의이 메서드 구현은 IDE에서이 호출에 필요한 정보를 반환 합니다. <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.CreateDocumentWindow%2A> 및 새로 열린된 문서 사이트입니다.

    3. IDE와 같은 일반적인 지 속성 인터페이스를 사용 하 여 문서를 로드 하는 마지막으로, <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2>합니다.

    4. IDE를 호출 하는 IDE가 이전에 계층 항목을 계층 구조를 사용할 수 있는지 결정 했을 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.GetItemContext%2A> 메서드는 프로젝트 수준 컨텍스트를 얻으려면 프로젝트 <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> 에 다시 전달에 대 한 포인터를 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.CreateDocumentWindow%2A> 메서드를 호출 합니다.

4. 반환을 <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> IDE를 호출 하는 경우 IDE에 대 한 포인터 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.GetItemContext%2A> 프로젝트에서 편집기 가져오기 컨텍스트를 활용할 수 있도록 하려면 프로젝트입니다.

     이 단계를 수행 프로젝트 제품 추가 서비스를 편집기를 수 있습니다.

     개체를 호출 하 여 해당 데이터를 사용 하 여 초기화 문서 뷰 개체를 문서 보기 창 프레임에 성공적으로 배치 된, 경우 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.LoadDocData%2A>합니다.

## <a name="see-also"></a>참고자료
- <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>
- [열기 및 프로젝트 항목 저장](../extensibility/internals/opening-and-saving-project-items.md)
- [방법: 프로젝트별 편집기 열기](../extensibility/how-to-open-project-specific-editors.md)
- [방법: 열린 문서에 대 한 편집기 열기](../extensibility/how-to-open-editors-for-open-documents.md)
- [파일 열기 명령을 사용 하 여 파일을 표시 합니다.](../extensibility/internals/displaying-files-by-using-the-open-file-command.md)