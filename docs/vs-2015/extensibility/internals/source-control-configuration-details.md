---
title: 원본 제어 구성 세부 정보 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], configuration details
ms.assetid: adbee9fc-7a2e-4abe-a3b8-e6615bcd797f
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5faa0ce575647038ac5ac7839b6dc066b7b51ce6
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63432063"
---
# <a name="source-control-configuration-details"></a>소스 제어 구성 세부 정보
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

소스 제어를 구현 하려면 다음을 수행 하 여 편집기나 프로젝트 시스템을 올바르게 구성 해야 합니다.  
  
- 변경 된 상태로 전환 하는 권한을 요청합니다  
  
- 파일을 저장할 수 있는 권한을 요청  
  
- 추가, 제거 또는 프로젝트의 파일 이름을 바꿀 수 있는 권한을 요청합니다  
  
## <a name="request-permission-to-transition-to-changed-state"></a>변경 된 상태로 전환 하는 권한을 요청합니다  
 프로젝트 또는 편집기를 호출 하 여 변경 된 (더티) 상태로 전환 하는 권한을 요청 해야 합니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>합니다. 구현 하는 각 편집기 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData.IsDocDataDirty%2A> 를 호출 해야 합니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> 환경에서 문서를 반환 하기 전에 변경에 대 한 승인 받고 `True` 에 대 한 `M:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData.IsDocDataDirty(System.Int32@)`합니다. 프로젝트를 기본적으로 프로젝트 파일에 대 한 편집기 있고 결과적으로, 해당 파일에 대 한 텍스트 편집기와 마찬가지로 프로젝트 파일에 대 한 상태 변경 추적을 구현에 대 한 동일한 책임이 있습니다. 환경 솔루션의 변경 된 상태를 처리 하지만 솔루션 참조 하지만 프로젝트 파일 또는 해당 항목 처럼 저장 하지 않습니다 모든 개체의 변경된 된 상태를 처리 해야 합니다. 일반적으로 프로젝트 또는 편집기를 지 속성 항목에 대 한 관리를 담당 하는 경우 다음 것 상태 변경 추적을 구현 하는 일을 담당 합니다.  
  
 에 대 한 응답을 `IVsQueryEditQuerySave2::QueryEditFiles` 호출 환경에는 다음을 수행할 수:  
  
- 있는 경우 편집기 또는 프로젝트에에서 있어야 합니다 (클린) 상태로 변경 호출을 거부 합니다.  
  
- 문서 데이터를 다시 로드할지를 나타냅니다. 프로젝트의 경우 환경을 프로젝트에 대 한 데이터를 다시 로드 됩니다. 편집기를 통해 디스크에서 데이터를 다시 로드 해야 해당 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.ReloadDocData%2A> 구현 합니다. 두 경우 모두에서 프로젝트 또는 편집기의 컨텍스트에서 데이터 다시 로드 되 면 변경할 수 있습니다.  
  
  적절 한 개/보수를 복잡 하 고 어려운 작업은 `IVsQueryEditQuerySave2::QueryEditFiles` 기존 코드 베이스를 호출 합니다. 결과적으로, 프로젝트 또는 편집기를 만드는 동안 이러한 호출을 통합 해야 합니다.  
  
## <a name="request-permission-to-save-a-file"></a>파일을 저장할 수 있는 권한을 요청  
 프로젝트 또는 편집기 파일을 저장 하기 전에 호출 해야 합니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFile%2A> 또는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A>합니다. 프로젝트 파일에 대 한 프로젝트 파일을 저장 하는 시기는 솔루션에서 이러한 호출은 자동으로 완료할 수 있습니다. 편집기는 하지 않는 한 이러한 호출에 대 한 편집기 구현의 `IVsPersistDocData2` 도우미 함수를 사용 하 여 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SaveDocDataToFile%2A>입니다. 편집기를 구현 하는 경우 `IVsPersistDocData2` 이 이렇게 하면 다음에 대 한 호출에서 `IVsQueryEditQuerySave2::QuerySaveFile` 또는 `IVsQueryEditQuerySave2::QuerySaveFiles` 수행 됩니다.  
  
> [!NOTE]
> 항상 먼저이 호출 하 게-즉, 편집기는 취소를 수신 하는 일을 할 때 한 번에 있습니다.  
  
## <a name="request-permission-to-add-remove-or-rename-files-in-the-project"></a>추가, 제거 또는 프로젝트의 파일 이름을 바꿀 수 있는 권한을 요청합니다  
 프로젝트 수 추가, 이름 바꾸기 또는 파일이 나 디렉터리를 제거 하기 전에 적절 한 호출 해야 `IVsTrackProjectDocuments2::OnQuery*` 환경에서 권한을 요청 메서드. 권한이 부여 되 면 프로젝트 작업을 완료 하 고 적절 한을 호출 해야 `IVsTrackProjectDocuments2::OnAfter*` 작업이 완료 되는 환경에 알리기 위해 메서드. 프로젝트의 메서드를 호출 해야 합니다는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> 모든 파일 (예를 들어, 특수 한 파일) 및 부모 파일 뿐만 아니라 인터페이스입니다. 파일 호출은 필수 있지만 디렉터리 호출 선택적입니다. 프로젝트 디렉터리 정보가 있으면 적절 한 호출 해야 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> 메서드 하지만이 정보가 없는 경우 환경 디렉터리 정보를 유추 합니다.  
  
 프로젝트의 메서드를 호출 하지 해야 `IVsTrackProjectDocuments2` 프로젝트 열기 또는 닫기입니다. 시작 시이 정보를 수신기에 대 한 대기 수를 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenSolution%2A> 이벤트 필요한 정보를 찾으려면 솔루션 전체를 반복 합니다. 이 정보는 종료 필요 하지 않습니다. `IVsTrackProjectDocuments2` 제공 되는 <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>합니다.  
  
 각 추가, 이름 바꾸기 및 제거 작업에 대 한 방법이 `OnQuery*` 메서드 및 `OnAfter*` 메서드. 호출 된 `OnQuery*` 메서드를 추가 하려면 권한이 있는지 확인 하기를 바꾸거나 파일 또는 디렉터리를 제거 합니다. 호출 된 `OnAfter*` 메서드 후, 파일 또는 디렉터리가 추가 또는 이름이 바뀌었거나, 제거 된 새 상태를 반영 하는 프로젝트 상태입니다.  
  
## <a name="see-also"></a>참고 항목  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFile%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SaveDocDataToFile%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>   
 [소스 제어 지원](../../extensibility/internals/supporting-source-control.md)
