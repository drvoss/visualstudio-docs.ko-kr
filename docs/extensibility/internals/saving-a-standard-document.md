---
title: 표준 문서 저장 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], saving standard documents
- projects [Visual Studio SDK], saving standard documents
- persistence, saving standard documents
ms.assetid: d692fedf-b46e-4d60-84bd-578635042235
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4f46d63e9f1145711bd3a32f6fd24e7b61814922
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66318672"
---
# <a name="saving-a-standard-document"></a>표준 문서 저장
환경 저장, 다른 이름으로 저장 및 모두 저장 명령을 처리합니다. 사용자가 선택 하는 경우 **저장**, **다른 이름으로 저장**, 또는 **모두 저장** 에서 **파일** 메뉴에 솔루션을 닫습니다는  **모두 저장**, 다음 프로세스가 발생 합니다.

 ![표준 편집기](../../extensibility/internals/media/public.gif "공용") 저장, 다른 이름으로 저장 및 표준 편집기를 처리 하는 모든 저장 명령

 다음 단계에서는이 프로세스를 자세히 설명 합니다.

1. 때를 **저장** 및 **다른 이름으로 저장** 명령을 선택한 경우이 환경에서는 <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> 활성 문서 창이 확인 하려면 서비스와 따라서 항목 저장 해야 합니다. 활성 문서 창이 확인 되 면 환경을 문서 테이블 실행에서 문서에 대 한 계층 포인터 및 항목 식별자 (itemID)를 찾습니다. 자세한 내용은 [문서 테이블 실행](../../extensibility/internals/running-document-table.md)합니다.

    경우는 **모두 저장** 명령을 선택, 환경 정보를 사용 하는 실행 중인 document 테이블에 저장 하는 모든 항목 목록을 컴파일합니다.

2. 솔루션 받으면를 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> 호출을 반복 하는 선택한 항목 집합 (의해 노출 되는, 여러 선택 항목을 <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> 서비스).

3. 선택 영역에 있는 각 항목을 솔루션 계층 포인터가 호출을 사용 합니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.IsItemDirty%2A> 결정 하는 방법 여부를 **저장** 메뉴 명령을 활성화 해야 합니다. 항목이 하나 이상의 손상 된 경우 해당 **저장할** 명령이 활성화 됩니다. 계층에서 표준 편집기를 사용 하는 경우 다음에 대 한 쿼리 계층 구조 대리자 더티 상태 편집기를 호출 하 여는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.IsDocDataDirty%2A> 메서드.

4. 변경 된 각 선택 항목을 솔루션 계층 포인터가 호출을 사용 합니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.SaveItem%2A> 적절 한 계층 메서드.

    표준 편집기를 사용 하 여 문서를 편집 하려면 계층에 대 한 일반적인 것입니다. 해당 편집기를 지원 해야 문서 데이터 개체,이 경우에 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> 인터페이스입니다. 수신 시 합니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.SaveItem%2A> 메서드 호출에서 프로젝트를 호출 하 여 문서가 저장 되는 편집기를 알려야 합니다는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.SaveDocData%2A> 문서 데이터 개체의 메서드. 편집기 환경을 처리할 수는 **다른 이름으로 저장** 를 호출 하 여 대화 상자에서 `Query Service` 에 대 한는 <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> 인터페이스입니다. 이에 대 한 포인터를 반환 합니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> 인터페이스입니다. 편집기를 호출 해야 합니다는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SaveDocDataToFile%2A> 메서드를 편집기에 대 한 포인터를 전달 <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> 이용 하 여 구현 된 `pPersistFile` 매개 변수입니다. 환경에서 다음 저장 작업을 수행 하 고 제공 된 **다른 이름으로 저장** 편집기 대화 상자. 환경 다시 호출 하 고 편집기를 <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>입니다.

5. 사용자 (즉, 이전에 저장 되지 않은 문서) 문서를 저장 하려고 하는 경우 다른 이름으로 저장 명령은 실제로 수행 됩니다.

6. 다른 이름으로 저장 명령에 대 한 환경 파일 이름에 대 한 사용자에 게 다른 이름으로 저장 대화 상자를 표시 합니다.

    파일의 이름이 변경 된 경우 계층 구조는 호출 하 여 캐시 된 정보는 문서 프레임의 업데이트에 대해 책임이 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.SetProperty%2A>(VSFPROPID_MkDocument).

   경우는 **다른 이름으로 저장** 명령 문서의 위치를 이동 하 고 계층 구조는 문서 위치에 중요 한 계층이 다른 계층으로 열려 있는 문서 창의 소유권을 전달 하는 일을 담당 합니다. 예를 들어이 프로젝트는 내부 또는 외부 파일 (기타) 프로젝트와 관련 하 여 파일이 있는지 여부를 추적 하는 경우 발생 합니다. 기타 파일 프로젝트에 파일의 소유권을 변경 하려면 다음 절차를 따르십시오.

## <a name="changing-file-ownership"></a>파일 소유권 변경

#### <a name="to-change-file-ownership-to-the-miscellaneous-files-project"></a>기타 파일 프로젝트에 파일 소유권을 변경 하려면

1. 서비스에 대 한 쿼리는 <xref:Microsoft.VisualStudio.Shell.Interop.SVsExternalFilesManager> 인터페이스입니다.

     에 대 한 포인터 <xref:Microsoft.VisualStudio.Shell.Interop.IVsExternalFilesManager2> 반환 됩니다.

2. 호출 된 <xref:Microsoft.VisualStudio.Shell.Interop.IVsExternalFilesManager2.TransferDocument%2A> (`pszMkDocumentNew`, `punkWindowFrame`) 문서를 새 계층으로 전송 하는 방법입니다. 다른 이름으로 저장 명령을 수행 하는 계층 구조는이 메서드를 호출 합니다.

## <a name="see-also"></a>참고 항목
- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>
- [프로젝트 항목 열기 및 저장](../../extensibility/internals/opening-and-saving-project-items.md)