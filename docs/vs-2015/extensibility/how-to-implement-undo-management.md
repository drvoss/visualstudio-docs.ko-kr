---
title: '방법: 실행 취소 관리 구현 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - undo management
ms.assetid: 1942245d-7a1d-4a11-b5e7-a3fe29f11c0b
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0f3d56ae02718f5dfdf373eeeb6aff774d11931e
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63435950"
---
# <a name="how-to-implement-undo-management"></a>방법: 실행 취소 관리 구현
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

실행 취소 관리에 사용 되는 기본 인터페이스는 <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager>, 환경에서 구현 되는 합니다. 실행 취소 관리를 지원 하려면 별도 실행 취소 단위를 구현 합니다. (즉, <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoUnit>, 여러 개별 단계로 포함할 수 있습니다.  
  
 실행 취소 관리를 구현 하는 방법을 여부 편집기 뷰를 여러 개를 지원 하는지 여부에 따라 달라 집니다. 각 구현에 대 한 절차는 다음 섹션에서 자세히 설명 합니다.  
  
## <a name="cases-where-an-editor-supports-a-single-view"></a>여기서 편집기 단일 보기를 지원 되는 경우  
 이 시나리오에서는 편집기는 여러 뷰를 지원 하지 않습니다. 하나의 편집기와 문서 하나 이며 실행 취소를 지원 합니다. 실행 취소 관리를 구현 하려면 다음 절차를 따르십시오.  
  
#### <a name="to-support-undo-management-for-a-single-view-editor"></a>단일 뷰 편집기에 대 한 실행 취소 관리를 지원 하려면  
  
1. 호출 `QueryInterface` 에 `IServiceProvider` 인터페이스에 대 한 창 프레임 `IOleUndoManager`, 실행 취소 관리자에 액세스 하려면 문서 보기 개체에서 (`IID_IOLEUndoManager`).  
  
2. 뷰는 창 프레임에 배치 됩니다, 경우 호출 하는 데 사용할 수 있는 사이트 포인터를 가져옵니다 `QueryInterface` 에 대 한 `IServiceProvider`합니다.  
  
## <a name="cases-where-an-editor-supports-multiple-views"></a>여기서 편집기에서는 여러 보기를 사용할 경우  
 문서 및 뷰 분리에 있는 경우 다음 일반적으로 하나의 실행 취소 관리자가 문서 자체와 연결 된입니다. 모든 실행 취소 단위 문서 데이터 개체와 연결 된 하나의 실행 취소 관리자에 배치 됩니다.  
  
 하나인 각 보기에 대 한 실행 취소 관리자의 보기 쿼리 하는 대신 문서 데이터 개체가 호출 <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A> 실행 취소 관리자를 인스턴스화할 때 CLSID_OLEUndoManager의 클래스 식별자를 지정 합니다. 클래스 식별자 OCUNDOID.h 파일에 정의 됩니다.  
  
 사용 하는 경우 <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A> 실행 취소 관리자에 게 환경에 연결할 사용자 고유의 실행 취소 관리자 인스턴스를 만들려면 다음 절차를 따르십시오.  
  
#### <a name="to-hook-your-undo-manager-into-the-environment"></a>실행 취소 관리자에 게 환경에 연결  
  
1. 호출 `QueryInterface` 에서 반환 되는 개체에 <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2> 에 대 한 `IID_IOleUndoManager`합니다. 에 대 한 포인터를 저장 <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager>합니다.  
  
2. 호출 `QueryInterface` 대 `IOleUndoManager` 에 대 한 `IID_IOleCommandTarget`합니다. 에 대 한 포인터를 저장 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>합니다.  
  
3. 릴레이 하 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> 하 고 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> 에 저장 된 호출 `IOleCommandTarget` 다음 StandardCommandSet97 명령에 대 한 인터페이스:  
  
   - cmdidUndo  
  
   - cmdidMultiLevelUndo  
  
   - cmdidRedo  
  
   - cmdidMultiLevelRedo  
  
   - cmdidMultiLevelUndoList  
  
   - cmdidMultiLevelRedoList  
  
4. 호출 `QueryInterface` 대 `IOleUndoManager` 에 대 한 `IID_IVsChangeTrackingUndoManager`합니다. 에 대 한 포인터를 저장 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager>합니다.  
  
    에 대 한 포인터를 사용 하 여 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager> 를 호출 하는 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager.MarkCleanState%2A>의 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager.AdviseTrackingClient%2A>, 및 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager.UnadviseTrackingClient%2A> 메서드.  
  
5. 호출 `QueryInterface` 대 `IOleUndoManager` 에 대 한 `IID_IVsLinkCapableUndoManager`합니다.  
  
6. 호출 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkCapableUndoManager.AdviseLinkedUndoClient%2A> 문서와 함께 있는 구현 해야 합니다 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkedUndoClient> 인터페이스입니다. 문서를 닫을 때 호출 `IVsLinkCapableUndoManager::UnadviseLinkedUndoClient`합니다.  
  
7. 문서를 닫을 때 호출할 `QueryInterface` 에 대해 실행 취소 관리자에 게 `IID_IVsLifetimeControlledObject`합니다.  
  
8. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLifetimeControlledObject.SeverReferencesToOwner%2A>를 호출합니다.  
  
9. 문서 변경 될 때 호출할 <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager.Add%2A> 사용 하 여 관리자에는 `OleUndoUnit` 클래스입니다. 합니다 <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager.Add%2A> 방법을 사용 하면 개체에 대 한 참조를 일반적으로 릴리스할 바로 뒤의 <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager.Add%2A>합니다.  
  
   `OleUndoManager` 클래스 하나의 실행 취소 스택 인스턴스를 나타냅니다. 따라서 취소 또는 다시 실행에 대 한 추적 되는 데이터 엔터티 당 하나의 실행 취소 관리자 개체가 됩니다.  
  
> [!NOTE]
> 실행 취소 관리자 개체는 텍스트 편집기에서 광범위 하 게 사용 하는 동안 구성 요소인 일반 있는 텍스트 편집기에 대 한 특정 지원 되지 않습니다. 여러 번 실행 취소 또는 다시 실행을 지원 하려는 경우에 이렇게 하려면이 개체를 사용할 수 있습니다.  
  
## <a name="see-also"></a>참고 항목  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLifetimeControlledObject>   
 [방법: 실행 취소 스택 지우기](../extensibility/how-to-clear-the-undo-stack.md)
