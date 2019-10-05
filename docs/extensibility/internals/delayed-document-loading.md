---
title: 지연 된 문서 로드 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: fb07b8e2-a4e3-4cb0-b04f-8eb11c491f35
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 30a3b1ce88a3e6a8069053c6d9daa14230034b28
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67821817"
---
# <a name="delayed-document-loading"></a>지연 된 문서 로드

사용자는 Visual Studio 솔루션 다시 열릴 때 대부분의 관련된 문서를 즉시 로드 되지 않습니다. 문서 창 프레임의 초기화 보류 중 상태에 만들어지고 (스텁 프레임) 자리 표시자 문서 실행 Document 테이블 (RDT)에 배치 됩니다.

확장 프로그램에 Visual Studio에 대 한 전체 메모리 사용 공간을 늘릴 수 있는 로드 된 전에 문서에 요소를 쿼리하여 불필요 하 게 로드할 프로젝트 문서 발생할 수 있습니다.

## <a name="document-loading"></a>문서 로드

스텁 프레임 및 문서 액세스 하면 문서의 예를 들어 창 프레임의 탭을 선택 하면 초기화 완벽 하 게 됩니다. 문서를 직접 문서 데이터를 가져오려고 RDT에 액세스 하거나 데이터에 다음 호출 중 하나를 만들어는 RDT를 직접 액세스를 요청 하는 확장에서 문서를 초기화할 수도 있습니다.

- 창 프레임 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A> 메서드.

- 창 프레임 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> 메서드를 다음과 같은 속성:

  - [__VSFPROPID.VSFPROPID_DocView](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID.VSFPROPID_DocView>)

  - [__VSFPROPID.VSFPROPID_ViewHelper](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID.VSFPROPID_ViewHelper>)

  - [__VSFPROPID.VSFPROPID_DocData](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID.VSFPROPID_DocData>)

  - [__VSFPROPID.VSFPROPID_AltDocData](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID.VSFPROPID_AltDocData>)

  - [__VSFPROPID.VSFPROPID_RDTDocData](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID.VSFPROPID_RDTDocData>)

  - [__VSFPROPID.VSFPROPID_SPProjContext](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID.VSFPROPID_SPProjContext>)

- 확장 관리 코드를 사용 하는 경우를 호출 하지 않아야 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.GetDocumentInfo%2A> 것이 확실 하지 않으면 문서 초기화 보류 중 상태가 아니거나 완전히 초기화 될 문서. 메서드는 항상 문서 반환 때문에 필요한 경우 새로 만드는 데이터 개체입니다. 메서드 중 하나를 호출 해야는 아니라는 `IVsRunningDocumentTable4` 인터페이스입니다.

- 확장을 사용 하는 경우 C++를 전달할 수 있습니다 `null` 않으려는 매개 변수에 대 한 합니다.

- 다른 속성에 대 한 요청 전에 관련 속성에 대 한 요청 하기 전에 다음 방법 중 하나를 호출 하 여 로드 하는 불필요 한 문서를 방지할 수 있습니다.

  - <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> 사용 하 여 [__VSFPROPID6 합니다. VSFPROPID_PendingInitialization](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID6.VSFPROPID_PendingInitialization>)합니다.

  - <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentFlags%2A>. 이 메서드는 반환 된 <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4> 에 대 한 값을 포함 하는 개체 [_VSRDTFLAGS4 합니다. RDT_PendingInitialization](<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4.RDT_PendingInitialization>) 문서 아직 초기화 되지 않은 경우.

문서를 완전히 초기화 될 때 발생 하는 RDT 이벤트를 구독 하 여 문서 로드 되었을 때 찾을 수 있습니다. 두 가지 방법이 있습니다.

- 이벤트 싱크를 구현 하는 경우 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents2>을 구독할 수 있습니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents2.OnAfterAttributeChangeEx%2A>,

- 그렇지 않은 경우에 가입할 수 있습니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents.OnAfterAttributeChange%2A>합니다.

다음 예제에서는 가상의 문서 액세스 경우 같습니다. Visual Studio 확장에서 열린 문서에 대 한 일부 정보를 표시 하려는 예를 들어 편집 잠금 수 및 문서 데이터에 대 한 것입니다. 사용 하 여 RDT 문서 열거 <xref:Microsoft.VisualStudio.Shell.Interop.IEnumRunningDocuments>, 다음 호출 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.GetDocumentInfo%2A> 편집 잠금 수 및 문서 데이터를 검색 하기 위해 각 문서에 대 한 합니다. 문서 초기화 보류 중 상태에서 이면 문서 데이터를 요청 하면 불필요 하 게 초기화 됩니다.

문서에 액세스 하는 더 효율적으로 사용 하는 것 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentEditLockCount%2A> 편집 잠금 수를 사용 하 여 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentFlags%2A> 문서 초기화 되었는지 여부를 확인 하려면. 플래그는 포함 되지 않은 경우 [_VSRDTFLAGS4 합니다. RDT_PendingInitialization](<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4.RDT_PendingInitialization>), 문서가 이미 초기화 된 문서 데이터를 요청 하 고 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentData%2A> 모든 불필요 한 초기화가 발생 하지 않습니다. 플래그를 포함 하는 경우 [_VSRDTFLAGS4 합니다. RDT_PendingInitialization](<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4.RDT_PendingInitialization>), 확장 문서 초기화 될 때까지 문서 데이터를 요청 하지 않아야 합니다. 검색 가능한이 초기화는 `OnAfterAttributeChange(Ex)` 이벤트 처리기입니다.

## <a name="test-extensions-to-see-if-they-force-initialization"></a>초기화를 수행 하는 경우 이러한 참조에 대 한 확장을 테스트 합니다.

확장 강제로 초기화 되어 경우 찾기가 어려울 수 있으므로 문서 초기화 되었는지 여부를 나타내는 표시 큐 없는 경우 텍스트가 완전히 초기화 되지 않은 모든 문서의 제목을 하면 되므로 더 쉽게 확인 하는 레지스트리 키를 설정할 수 있습니다 *[스텁]* 제목에 있습니다.

**HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\14.0\BackgroundSolutionLoad**설정 **StubTabTitleFormatString** 하  *{0} [스텁]* 합니다.
