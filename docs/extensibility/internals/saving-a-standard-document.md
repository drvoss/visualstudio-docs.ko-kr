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
ms.openlocfilehash: df93813d339a45689845b82fe4f5a185301b6c74
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72724093"
---
# <a name="saving-a-standard-document"></a>표준 문서 저장
환경에서는 저장, 다른 이름으로 저장 및 모두 저장 명령을 처리 합니다. 사용자가 **파일** 메뉴에서 **저장**, 다른 **이름으로 저장**또는 **모두** 저장을 선택 하거나 솔루션을 닫을 때 **모두 저장**을 선택 하면 다음 프로세스가 발생 합니다.

 ![표준 편집기](../../extensibility/internals/media/public.gif "Public") 표준 편집기에 대 한 저장, 다른 이름으로 저장 및 모든 명령 처리 저장

 이 프로세스는 다음 단계에 자세히 설명 되어 있습니다.

1. **저장** 및 다른 **이름으로 저장** 명령이 선택 되 면 환경에서는 <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> 서비스를 사용 하 여 활성 문서 창을 확인 하 여 저장 해야 하는 항목을 확인 합니다. 활성 문서 창을 알고 있으면 환경에서 실행 중인 문서 테이블의 문서에 대 한 계층 포인터 및 항목 식별자 (itemID)를 찾습니다. 자세한 내용은 [문서 테이블 실행](../../extensibility/internals/running-document-table.md)을 참조 하세요.

    **모두 저장** 명령을 선택 하면 환경에서 실행 중인 문서 테이블의 정보를 사용 하 여 저장할 모든 항목의 목록을 컴파일합니다.

2. 솔루션은 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> 호출을 받으면 선택 된 항목 집합을 반복 합니다. 즉, <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> 서비스에서 제공 하는 여러 선택 항목을 반복 합니다.

3. 솔루션에서는 선택 항목의 각 항목에 대해 계층 포인터를 사용 하 여 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.IsItemDirty%2A> 메서드를 호출 하 여 **저장** 메뉴 명령을 사용할지 여부를 결정 합니다. 하나 이상의 항목이 변경 된 경우 **저장** 명령이 사용 됩니다. 계층 구조에서 표준 편집기를 사용 하는 경우 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.IsDocDataDirty%2A> 메서드를 호출 하 여 변경 상태에 대 한 쿼리를 편집기에 위임 합니다.

4. 변경 된 각 항목에 대해 솔루션은 계층 포인터를 사용 하 여 해당 계층에 대 한 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.SaveItem%2A> 메서드를 호출 합니다.

    계층에서 표준 편집기를 사용 하 여 문서를 편집 하는 것이 일반적입니다. 이 경우 해당 편집기에 대 한 문서 데이터 개체는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> 인터페이스를 지원 해야 합니다. @No__t_0 메서드 호출을 받으면 프로젝트는 문서 데이터 개체에 대 한 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.SaveDocData%2A> 메서드를 호출 하 여 문서가 저장 되 고 있음을 편집기에 알려야 합니다. 편집기를 사용 하면 <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> 인터페이스에 대 한 `Query Service`를 호출 하 여 환경에서 **다른 이름으로 저장** 대화 상자를 처리할 수 있습니다. @No__t_0 인터페이스에 대 한 포인터를 반환 합니다. 그런 다음 편집기는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SaveDocDataToFile%2A> 메서드를 호출 하 여 `pPersistFile` 매개 변수를 통해 편집기의 <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> 구현에 대 한 포인터를 전달 해야 합니다. 그러면 환경에서 저장 작업을 수행 하 고 편집기에 대 한 다른 **이름으로 저장** 대화 상자를 제공 합니다. 그러면 환경에서 <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>를 사용 하 여 편집기를 다시 호출 합니다.

5. 사용자가 제목 없는 문서 (이전에 저장 하지 않은 문서)를 저장 하려는 경우에는 다른 이름으로 저장 명령이 실제로 수행 됩니다.

6. 다른 이름으로 저장 명령의 경우 환경에는 다른 이름으로 저장 대화 상자가 표시 되 고 사용자에 게 파일 이름을 입력 하 라는 메시지가 표시 됩니다.

    파일 이름이 변경 된 경우 계층 구조는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.SetProperty%2A> (VSFPROPID_MkDocument)를 호출 하 여 문서 프레임의 캐시 된 정보를 업데이트 하는 일을 담당 합니다.

   다른 **이름으로 저장** 명령이 문서 위치를 이동 하 고 계층 구조가 문서 위치를 구분 하는 경우 계층은 열린 문서 창의 소유권을 다른 계층에 전달 해야 합니다. 예를 들어 프로젝트가 프로젝트와 관련 하 여 파일이 내부 또는 외부 파일 (기타 파일) 인지 여부를 프로젝트에서 추적 하는 경우이 오류가 발생 합니다. 다음 절차를 사용 하 여 파일의 소유권을 기타 파일 프로젝트로 변경할 수 있습니다.

## <a name="changing-file-ownership"></a>파일 소유권 변경

#### <a name="to-change-file-ownership-to-the-miscellaneous-files-project"></a>기타 파일 프로젝트에 대 한 파일 소유권을 변경 하려면

1. @No__t_0 인터페이스에 대 한 쿼리 서비스입니다.

     @No__t_0에 대 한 포인터가 반환 됩니다.

2. @No__t_0 (`pszMkDocumentNew`, `punkWindowFrame`) 메서드를 호출 하 여 문서를 새 계층으로 전송 합니다. 다른 이름으로 저장 명령을 수행 하는 계층은이 메서드를 호출 합니다.

## <a name="see-also"></a>참조
- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>
- [프로젝트 항목 열기 및 저장](../../extensibility/internals/opening-and-saving-project-items.md)