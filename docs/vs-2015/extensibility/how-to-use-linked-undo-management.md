---
title: '방법: 연결 된 실행 취소 관리를 사용 하 여 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - linked undo management
ms.assetid: af5cc22a-c9cf-45b1-a894-1022d563f3ca
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 67d0d173909b8cdfe2eaf0d56aa5c99c437d5ad8
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63441549"
---
# <a name="how-to-use-linked-undo-management"></a>방법: 연결 된 실행 취소 관리 사용
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

연결 된 실행 취소 사용자를가 동시에 여러 파일에 같은 편집 작업을 취소할 수 있습니다. 예를 들어, 헤더 파일 및 시각적 개체와 같은 여러 프로그램 파일에 걸쳐 동시 텍스트가 변경 C++ 파일에서 연결 된 실행 취소 트랜잭션이 있습니다. 환경의 구현의 실행 취소 관리자에 연결 된 실행 취소 기능이 내장 되어 및 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkedUndoTransactionManager> 이 기능을 조작할 수 있습니다. 연결 된 실행 취소는 별도 실행 취소 스택을 단일 실행 취소 단위를 처리 하는 함께 연결할 수 있는 부모 실행 취소 단위를 통해 구현 됩니다. 연결 된 실행 취소를 사용 하는 절차는 다음 섹션에 자세히 설명 되어 있습니다.  
  
### <a name="to-use-linked-undo"></a>연결 된 실행 취소를 사용 하려면  
  
1. 호출 `QueryService` 대 `SVsLinkedUndoManager` 에 대 한 포인터를 가져오려면 `IVsLinkedUndoTransactionManager`합니다.  
  
2. 호출 하 여 초기 부모 연결 된 실행 취소 단위를 만들고 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkedUndoTransactionManager.OpenLinkedUndo%2A>합니다. 이 연결 된 실행 취소 스택을으로 그룹화 하기 위해 실행 취소 스택 집합에 대 한 시작 지점을 설정 합니다. 에 `OpenLinkedUndo` 메서드 strict 또는 엄격한 연결 된 실행 취소 여부를 지정 해야 합니다. 비-엄격 하 게 연결 된 실행 취소 동작 일부 연결 된 실행 취소 형제가 있는 문서를 닫아도 두고 다른 연결 된 해당 스택에 형제를 취소 하는 여전히 있음을 의미 합니다. 엄격 하 게 연결 된 실행 취소 동작 모든 연결 된 실행 취소 형제 스택을 함께 또는 전혀 취소할 수 있도록 지정 합니다. 연결 된 후속 실행 취소 스택을 호출 하 여 추가 [IOleUndoManager::Add](/windows/desktop/api/ocidl/nf-ocidl-ioleundomanager-add) 메서드.  
  
3. 호출 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkedUndoTransactionManager.CloseLinkedUndo%2A> 롤 모든 하나로 연결 된 실행 취소 단위입니다.  
  
    > [!NOTE]
    > 편집기에서 연결 된 실행 취소 관리를 구현 하려면 실행 취소 관리를 추가 합니다. 연결 된 실행 취소 관리 구현에 대 한 자세한 내용은 참조 하세요. [방법: 실행 취소 관리 구현](../extensibility/how-to-implement-undo-management.md)합니다.  
  
## <a name="see-also"></a>참고 항목  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>   
 [IOleParentUndoUnit](/windows/desktop/api/ocidl/nn-ocidl-ioleparentundounit)   
 [IOleUndoUnit](/windows/desktop/api/ocidl/nn-ocidl-ioleundounit)   
 [방법: 실행 취소 관리 구현](../extensibility/how-to-implement-undo-management.md)
