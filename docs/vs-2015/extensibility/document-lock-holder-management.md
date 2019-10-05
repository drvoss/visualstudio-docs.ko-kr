---
title: 문서 잠금 소유자 관리 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - document locking
ms.assetid: fa1ce513-eb7d-42bc-b6e8-cb2433d051d5
caps.latest.revision: 22
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 73c6151b5c02cb81a10c2725091c16457db70e33
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68204626"
---
# <a name="document-lock-holder-management"></a>문서 잠금 소유자 관리
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

문서 테이블 실행 (RDT)는 열려 있는 문서 및 편집 잠금을의 개수를 유지 합니다. 문서 창에 열려 있는 문서를 표시 하는 사용자 없이 백그라운드에서 편집할 프로그래밍 방식으로 때 문서는 RDT에 대해 한 편집 잠금을 배치할 수 있습니다. 이 기능은 그래픽 사용자 인터페이스를 통해 여러 파일을 수정 하는 디자이너에서 자주 사용 됩니다.  
  
## <a name="document-lock-holder-scenarios"></a>문서 잠금 소유자 시나리오  
  
### <a name="file-a-has-a-dependence-on-file-b"></a>파일 "a"에 파일에 대 한 종속성 "b"  
 파일 형식에 대 한 표준 편집기 "A"를 구현 하는 상황을 가정해 보세요 "a"와 "a"에 대 한 참조 (또는에 대 한 종속성) 형식의 각 파일 "b" 형식의 파일입니다. 표준 편집기 "B" "b" 형식의 파일에 대 한 존재합니다. "A" 편집기 파일을 열 때 "a"는 "b"는 해당 파일에 대 한 참조를 검색 합니다. 파일 "b", 표시 되지 않습니다 하지만 "A" 편집기에서 수정할 수 있습니다. 편집기 "는" 파일의 문서 데이터에 대 한 참조 "b"에서 가져오는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.FindAndLockDocument%2A> 메서드 또한 "b" 파일에 대 한 편집 잠금을 유지 관리 합니다. 편집기 "A" 작업이 완료 되 면 파일 "b"에서 호출 하 여 계산 파일 "b" 편집 잠금 감소 시킬 수 있습니다를 수정 합니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnlockDocument%2A> 메서드. 마치 호출 하는 경우이 단계를 생략할 수 있습니다 합니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.FindAndLockDocument%2A> 매개 변수를 사용 하 여 메서드 `dwRDTLockType` 로 <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS>합니다.  
  
### <a name="file-b-is-opened-by-a-different-editor"></a>다른 편집기에서 "b" 파일을 열  
 파일 "b"가 이미 열어 놓은 편집기 "B" 편집기 "A"를 열려고 할 때는 두 가지 별도 시나리오를 처리 하:  
  
- 편집기 "A" 문서 편집 잠금을 사용 하 여 "b" 파일에 등록 해야 파일 "b" 호환 편집기에에서 열려 있는 경우는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.RegisterDocumentLockHolder%2A> 메서드. 등록 취소는 문서에 사용 하 여 잠금을 편집 수정 파일 "b" 편집기 "A" 완료 되 면를 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnregisterDocumentLockHolder%2A> 메서드.  
  
- 파일 "b"가 호환 되지 않는 방식으로 열려 있으면 "A" 실패 하거나 수 "A" 부분적으로 열고 적절 한 오류 메시지를 표시 하는 편집기와 연결 된 뷰 편집기에서 파일 "b"의 열기를 시도 하거나 시킬 수 있습니다. 오류 메시지에는 호환 되지 않는 편집기에서 파일 "b"를 닫은 다음 다시 "a"를 사용 하 여 파일을 엽니다 하도록 사용자에 게는 "A" 편집기입니다. 구현할 수도 있습니다는 [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] 메서드 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable2.QueryCloseRunningDocument%2A> 호환 되지 않는 편집기에 열려 있는 사용자 "b" 파일을 닫습니다. 사용자가 파일 "b", 파일 열기에 "a" 편집기 "A"는 일반적으로 계속 됩니다.  
  
## <a name="additional-document-edit-lock-considerations"></a>추가 문서 편집 잠금 고려 사항  
 편집기 "A"는 "B" 편집기도 문서를 저장 하는 것 보다 "b" 파일에 대 한 잠금을 편집 하는 문서에 있는 유일한 편집기 파일 "b"에 대 한 잠금을 편집 하는 경우 다른 동작을 가져옵니다. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], **클래스 디자이너** 은 예제 연결된 된 코드 파일에서 편집 잠금을 유지 하지 않습니다는 비주얼 디자이너입니다. 즉, 사용자가 디자인 뷰에서 엽니다 클래스 다이어그램 및 연결된 된 코드 파일을 동시에, 열 및 사용자 코드 파일을 수정 하지만 변경 내용을 저장 하지 않습니다 하는 경우 변경 내용이 손실 됩니다 클래스 다이어그램 (.cd) 파일. 경우는 **클래스 디자이너** 에 문서 편집 코드 파일에 대 한 잠금을 사용자 요청 하지 않습니다 코드 파일을 닫을 때 변경 내용을 저장 합니다. IDE 사용자를 닫은 후에 변경 내용을 저장 하는 사용자에 게 요청 합니다 **클래스 디자이너**합니다. 두 파일에 저장된 된 변경 사항은 반영 됩니다. 두 경우는 **클래스 디자이너** 코드 파일 편집기 코드 파일 또는 폼을 닫을 때 저장 하 라는 메시지가 다음 코드 파일에 대해 문서 편집 잠금을 보유 합니다. 이때 폼 및 코드 파일에서 저장된 된 변경 사항은 반영 됩니다. 클래스 다이어그램에 대 한 자세한 내용은 참조 하세요. [클래스 다이어그램 (클래스 디자이너)를 사용 하 여 작업](../ide/working-with-class-diagrams-class-designer.md)합니다.  
  
 비 편집기에 대 한 문서에 대 한 편집 잠금을 배치 해야 할 경우 구현 해야 한다는 점에 유의 합니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder> 인터페이스입니다.  
  
 여러 번 UI 디자이너 코드 파일을 프로그래밍 방식으로 수정 하는 둘 이상의 파일을 변경 합니다. 이러한 경우에는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell2.SaveItemsViaDlg%2A> 메서드를 이용 하 여 하나 이상의 문서를 저장 하는 처리 합니다 **다음 항목의 변경 내용을 저장 하 시겠습니까?** 대화 상자.  
  
## <a name="see-also"></a>참고 항목  
 [문서 테이블 실행](../extensibility/internals/running-document-table.md)   
 [지속성 및 실행 중인 문서 테이블](../extensibility/internals/persistence-and-the-running-document-table.md)
