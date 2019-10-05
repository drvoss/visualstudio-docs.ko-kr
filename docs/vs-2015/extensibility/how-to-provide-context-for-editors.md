---
title: '방법: 편집기에 대 한 컨텍스트를 제공 합니다. | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - provide context
ms.assetid: 12df4d06-df6b-4eaf-a7bf-c83655a0c683
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 11a98599a9812cd00650d113170ff55c01ac44db
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63435906"
---
# <a name="how-to-provide-context-for-editors"></a>방법: 편집기에 대 한 컨텍스트를 제공 합니다.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

편집기에 대 한는 컨텍스트는 편집기에 포커스가 또는 도구 창에 포커스를 이동 된 직전 포커스가 있던 경우에 활성화 됩니다. 다음을 수행 하 여 편집기에 대 한 컨텍스트를 제공할 수 있습니다.  
  
1. 컨텍스트 모음을 만듭니다.  
  
2. 컨텍스트 모음 선택 요소 식별자 (SEID)에 게시 합니다.  
  
3. 모음에 컨텍스트를 유지 합니다.  
  
   이러한 작업은 다음 절차에 포함 됩니다. 컨텍스트를 제공 하는 방법에 대 한 자세한 내용은 참조 하세요. **강력한 프로그래밍** 이 항목의에서 뒷부분에 있습니다.  
  
### <a name="to-create-a-context-bag-for-an-editor-or-a-designer"></a>편집기 또는 디자이너에 대 한 상황에 맞는 모음을 만들려면  
  
1. 호출 `QueryService` 에 사용자 <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> 에 대 한 인터페이스를 <xref:Microsoft.VisualStudio.Shell.Interop.SVsMonitorUserContext> 서비스입니다.  
  
     에 대 한 포인터를 <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorUserContext> 인터페이스가 반환 됩니다.  
  
2. 호출 된 <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorUserContext.CreateEmptyContext%2A> 새 컨텍스트 또는 하위 컨텍스트의 모음을 만드는 방법.  
  
     에 대 한 포인터를 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext> 인터페이스가 반환 됩니다.  
  
3. 호출 된 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AddAttribute%2A> 컨텍스트 또는 하위 컨텍스트의 모음에 특성, 조회 키워드 또는 F1 키워드를 추가 하는 방법입니다.  
  
4. 하위 컨텍스트의 모음을 만드는 경우 호출 된 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AddSubcontext%2A> 하위 컨텍스트의 모음 부모 컨텍스트 모음에 연결 하는 방법입니다.  
  
5. 호출 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AdviseUpdate%2A> 알림을 받을 때 합니다 **동적 도움말** 기간은 업데이트 하려고 합니다.  
  
     필요 합니다 **동적 도움말** 창을 호출 하는 편집기를 업데이트할 준비가 되었을 때 기회가 지연 업데이트가 발생할 때까지 컨텍스트가 변경. 이렇게 시스템 유휴 시간까지 시간이 오래 걸리는 알고리즘 실행을 지연 시킬 수 있으므로 성능을 향상 시킬 수 있습니다.  
  
### <a name="to-publish-the-context-bag-to-the-seid"></a>컨텍스트 모음을 SEID를 게시 하려면  
  
1. 호출 `QueryService` 에 <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackSelectionEx> 에 대 한 포인터를 반환 하도록 서비스에는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx> 인터페이스입니다.  
  
2. 호출 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx.OnElementValueChange%2A>, 요소 식별자를 지정 합니다. (`elementid` 매개 변수) SEID_UserContext 전역 수준 컨텍스트를 전달 하는 있는지를 나타내는 값입니다.  
  
3. 편집기 또는 디자이너를 활성화 하면,의 값을 해당 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx> 개체 전역 선택에 전파 됩니다. 세션당 한 번이 프로세스를 완료 하 여 다음을 호출할 때 만든 전역 컨텍스트에 대 한 포인터를 저장 하기만 하면 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx.OnElementValueChange%2A>합니다.  
  
### <a name="to-maintain-the-context-bag"></a>컨텍스트 모음을 유지 하기 위해  
  
1. 구현 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext> 되도록 합니다 **동적 도움말** 를 업데이트 하기 전에 창 편집기 또는 디자이너를 호출 합니다.  
  
     가 호출 하는 각 상황에 맞는 모음에 대 한 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AdviseUpdate%2A> 컨텍스트 모음을 만들고 구현한 후 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate>, IDE 호출 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate.UpdateUserContext%2A> 컨텍스트 모음을 업데이트할 컨텍스트 공급자를 알립니다. 전에 특성과 키워드 컨텍스트 모음 및 모든 하위 컨텍스트의 백을 변경 하려면이 호출을 사용할 수는 **동적 도움말** 창 업데이트가 발생 합니다.  
  
2. 호출 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.SetDirty%2A> 편집기 또는 디자이너에 새 컨텍스트 있음을 나타내기 위해 컨텍스트 모음에 있습니다.  
  
     경우는 **동적 도움말** 창 호출 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate.UpdateUserContext%2A> 업데이트 하는, 편집기 또는 디자이너를 해당 시점에 부모 컨텍스트 모음 및 모든 하위 컨텍스트의 모음이 모두에 대해 적절 하 게 컨텍스트를 업데이트할 수 있습니다 하 합니다.  
  
    > [!NOTE]
    > 합니다 `SetDirty` 플래그 자동으로 설정 됩니다 `true` 컨텍스트에서 추가 되거나 컨텍스트 모음에서 제거 될 때마다 합니다. **동적 도움말** 창을 호출 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate.UpdateUserContext%2A> 컨텍스트 모음에서 경우 합니다 `SetDirty` 플래그가로 설정 되어 `true`합니다. 다시 설정 `false` 업데이트 후 합니다.  
  
3. 호출 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AddAttribute%2A> 상황에 맞는 active 컨텍스트 컬렉션에 추가할 또는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.RemoveAttribute%2A> 컨텍스트를 제거 합니다.  
  
## <a name="robust-programming"></a>강력한 프로그래밍  
 사용자 고유의 편집기를 작성 하는 경우 세 가지 모두를 편집기에 대 한 컨텍스트를 제공 하려면이 항목의 절차를 완료 해야 합니다.  
  
> [!NOTE]
> 호출 해야 제대로 프로그램 편집기 또는 디자이너 창을 활성화 하 고 명령 라우팅가 제대로 업데이트 되도록 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A> 에서 구성 요소를 포커스 창으로 만듭니다.  
  
 SEID는 선택에 따라 변경 하는 속성의 컬렉션입니다. SEID 정보는 전역 선택을 통해 제공 됩니다. 전역 선택에 의해 트리거되는 이벤트에 연결 하는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx> 인터페이스에 있는 모든 항목의 목록을 선택 (현재 편집기, 현재 도구 창, 현재 계층 및 등).  
  
 편집기와 디자이너는 컨텍스트 때마다 변경 될 수 커서 이동가 단어 안에서 것은 비효율적 컨텍스트 모음을 지속적으로 업데이트 합니다. 편집기 또는 디자이너 창 내에서 이동 하는 커서를 발견 하면 언제 든 지 더 효율적으로 업데이트 하도록 호출할 수 있습니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.SetDirty%2A>합니다. 유휴 시간이 IDE의 상황에 맞는 서비스에 알림을 보냅니다 편집기 또는 디자이너는 때까지 컨텍스트 변경 내용을 저장할 수 있습니다이 작업을 수행 합니다 **동적 도움말** 창이 업데이트 됩니다. 이 방법은이 항목의 "컨텍스트 모음 유지 하려면" 절차에서 사용 됩니다.  
  
 편집기 또는 디자이너 내에서 활동에 대 한 컨텍스트를 입력 한 후 사용자가 편집기 또는 디자이너 자체에 대 한 도움말을 가져올 수 있도록 특정 F1 키워드를 제공 해야 합니다.  
  
## <a name="see-also"></a>참고 항목  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx.OnElementValueChange%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AddAttribute%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AdviseUpdate%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.RemoveAttribute%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.SetDirty%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate.UpdateUserContext%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackSelectionEx>
