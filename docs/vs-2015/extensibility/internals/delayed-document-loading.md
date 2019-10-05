---
title: 지연 된 문서 로드 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: fb07b8e2-a4e3-4cb0-b04f-8eb11c491f35
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5565749a21614bb0b882beab8c83ed63bc839229
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68196866"
---
# <a name="delayed-document-loading"></a>지연된 문서 로드
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

사용자는 Visual Studio 솔루션 다시 열릴 때 대부분의 관련된 문서를 즉시 로드 되지 않습니다. 문서 창 프레임의 초기화 보류 중 상태에 만들어지고 (스텁 프레임) 자리 표시자 문서 실행 문서 테이블 (RDT)에 배치 됩니다.  
  
 확장은 프로젝트 문서를 로드 하기 전에 문서에 요소를 쿼리하여 불필요 하 게 로드 될 수 있습니다. Visual Studio에 대 한 전체 메모리 사용 공간이 늘어날 수 있습니다.  
  
## <a name="document-loading"></a>문서 로드  
 스텁 프레임 및 문서 액세스 하면 문서의 예를 들어 창 프레임의 탭을 선택 하면 초기화 완벽 하 게 됩니다. 문서를 직접 문서 데이터를 가져오려고 RDT에 액세스 하거나 데이터에 다음 호출 중 하나를 만들어는 RDT를 직접 액세스를 요청 하는 확장에서 문서를 초기화할 수도 있습니다.  
  
- 창 프레임에는 메서드 표시: <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A>합니다.  
  
- 창 프레임의 GetProperty 메서드 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> 다음 속성 중 하나:  
  
  - <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
  - <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
  - <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
  - <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
  - <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
  - <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
  확장 관리 코드를 사용 하는 경우를 호출 하지 않아야 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.GetDocumentInfo%2A> 것이 확실 하지 않으면 문서 초기화 보류 중 상태가 아니거나 완전히 초기화 될 문서... 이 메서드는 항상 문서 반환 하기 때문에 이것이 필요한 경우 새로 만드는 데이터 개체입니다. 대신 IVsRunningDocumentTable4 인터페이스에서 메서드 중 하나를 호출 해야 있습니다.  
  
  확장을 사용 하는 경우 C++를 전달할 수 있습니다 `null` 않으려는 매개 변수에 대 한 합니다.  
  
  관련 속성에 대 한 요청 하기 전에 다음 방법 중 하나를 호출 하 여 불필요 한 문서 로드를 방지할 수 있습니다: 다른 속성에 대 한 요청 전에 합니다.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> 사용 하 여 <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID6>입니다.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentFlags%2A>. 이 메서드가 반환 된 <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4> 개체에 대 한 값을 포함 하는 <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4> 문서 아직 초기화 되지 않은 경우.  
  
  문서를 완전히 초기화 될 때 발생 하는 RDT 이벤트를 구독 하 여 문서 로드 되었을 때 찾을 수 있습니다. 두 가지 방법이 있습니다.  
  
- 이벤트 싱크를 구현 하는 경우 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents2>을 구독할 수 있습니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents2.OnAfterAttributeChangeEx%2A>,  
  
- 그렇지 않은 경우에 가입할 수 있습니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents.OnAfterAttributeChange%2A>합니다.  
  
  다음은 가상 문서 액세스 시나리오입니다. Visual Studio 확장에서 열린 문서에 대 한 일부 정보를 표시 하려면 예를 들어 편집 잠금 수 및 문서 데이터에 대 한 것입니다. 사용 하 여 RDT 문서 열거 <xref:Microsoft.VisualStudio.Shell.Interop.IEnumRunningDocuments>, 다음 호출 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.GetDocumentInfo%2A> 편집 잠금 수 및 문서 데이터를 검색 하기 위해 각 문서에 대 한 합니다. 문서 초기화 보류 중 상태에서 이면 문서 데이터를 요청 하면 불필요 하 게 초기화 됩니다.  
  
  이렇게 더 효율적으로 사용 하는 것 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentEditLockCount%2A> 편집 잠금 수를 사용 하 여 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentFlags%2A> 문서 초기화 되었는지 여부를 확인 하려면. 플래그는 포함 되지 않은 경우 <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4>, 문서가 이미 초기화 된 문서 데이터를 요청 하 고 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentData%2A> 모든 불필요 한 초기화가 발생 하지 않습니다. 플래그를 포함 하는 경우 <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4>, 확장 문서 초기화 될 때까지 문서 데이터를 요청 하지 않아야 합니다. OnAfterAttributeChange(Ex) 이벤트 처리기에서 검색할 수 있습니다.  
  
## <a name="testing-extensions-to-see-if-they-force-initialization"></a>초기화를 수행 하는 경우 이러한 참조에 대 한 확장을 테스트  
 확장 강제로 초기화 되어 경우 찾기가 어려울 수 있으므로 문서 초기화 되었는지 여부를 나타내는 표시 큐 없는 경우 텍스트가 완전히 초기화 되지 않은 모든 문서의 제목을 하면 되므로 더 쉽게 확인 하는 레지스트리 키를 설정할 수 있습니다 `[Stub]` 제목에서입니다.  
  
 **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\14.0\BackgroundSolutionLoad]** 설정 **StubTabTitleFormatString** 하  **{0} [스텁]** 합니다.
