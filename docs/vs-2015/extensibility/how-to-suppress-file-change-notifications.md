---
title: '방법: 파일 변경 알림 표시 안 함 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - suppress file change notification
ms.assetid: 891c1eb4-f6d0-4073-8df0-2859dbd417ca
caps.latest.revision: 19
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 3f045175eae165b75a887ada2716b19f34fc228b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68204073"
---
# <a name="how-to-suppress-file-change-notifications"></a>방법: 파일 변경 알림 표시 안 함
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

메시지와 함께 대화 상자가 표시 텍스트 버퍼를 나타내는 물리적 파일이 변경 된 경우 **다음 항목의 변경 내용을 저장 하 시겠습니까?** 이 파일 변경 알림 이라고 합니다. 하지만 많은 변경 하는 경우 파일을이 대화 상자를 반복적으로 표시 될 수 있습니다 신속 하 게 성가신.  
  
 다음 절차를 사용 하 여이 대화 상자를 프로그래밍 방식으로 억제할 수 있습니다. 이 작업을 수행 하 여 다시 로드할 수 있습니다 파일 즉시 될 때마다 변경 내용을 저장 하 라는 메시지를 표시 하지 않고 있습니다.  
  
### <a name="to-suppress-file-change-notification"></a>파일 변경 알림을 표시 하지 않으려면  
  
1. 호출 된 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.FindAndLockDocument%2A> 텍스트 버퍼 개체가 열려 있는 파일에 연관 된 확인 방법입니다.  
  
2. 직접를 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> 무시 하기 위해 메모리에 모니터링 하는 파일 변경 내용을 가져와서 개체를 <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl> 에서 인터페이스를 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> (문서 데이터) 개체를 반복한 다음 구현 합니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl.IgnoreFileChanges%2A> 메서드를 `fIgnore` 매개 변수 로 `true`합니다.  
  
3. 메서드를 호출 합니다 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> 및 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> 인터페이스 메모리 내 업데이트를 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> 파일 변경 (예: 구성 요소에 필드를 추가 되 면)를 사용 하 여 개체입니다.  
  
4. 보류 중인 편집 내용이, 사용자가 진행 중 하나를 고려 하지 않고 변경 내용으로 디스크에 있는 파일을 업데이트 합니다.  
  
     이렇게 하면는 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> 파일에 대 한 모니터링을 다시 시작 하는 개체 변경 알림, 텍스트 버퍼 메모리의 다른 모든 보류 중인 편집 뿐만 아니라 생성 된 변경 내용을 반영 합니다. 디스크의 파일을 반영 하 여 생성 되는 최신 코드 및 모든 이전에 사용자가 변경 내용을 사용자가 편집한 코드에 저장 합니다.  
  
5. 호출을 <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl.IgnoreFileChanges%2A> 에 알리기 위해 메서드를 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> 설정 하 여 파일 변경 알림에 대 한 모니터링을 다시 시작 하는 개체를 `fIgnore` 매개 변수를 `false`합니다.  
  
6. 소스 코드 제어 (SCC)의 경우와 같이 파일에 대 한 몇 가지 변경 하려는 경우 파일 변경 알림 일시 중단 하도록 전역 파일 변경 서비스에 알려 줘야 합니다.  
  
     예를 들어 파일을 다시 작성 하 고 다음 타임 스탬프를 변경 하는 경우 재작성 및 timestample 작업은 각 계산 별도 파일로 이벤트를 변경 하는 대로 파일 변경 알림의 일시 중단 해야 합니다. 대신 호출 해야 하는 전역 파일 변경 알림을 사용 하도록 설정 된 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFileChangeEx.IgnoreFile%2A> 메서드.  
  
## <a name="example"></a>예제  
 다음 파일 변경 알림 표시 안 함 하는 방법에 설명 합니다.  
  
```cpp#  
//Misc. helper classes  
  
CSuspendFileChanges::CSuspendFileChanges(  
    /* [in] */ const CString& strMkDocument,   
    /* [in] */ BOOL fSuspendNow /* = TRUE */)   
:  
    m_strMkDocument(strMkDocument),  
    m_fFileChangeSuspended(FALSE)  
{  
    if(fSuspendNow)  
        Suspend();  
}  
CSuspendFileChanges::~CSuspendFileChanges()  
{  
    Resume();  
}  
void CSuspendFileChanges::Suspend()  
{  
    USES_CONVERSION;  
  
    // Prevent suspend from suspending more than once.  
    if(m_fFileChangeSuspended)  
        return;  
  
    IVsRunningDocumentTable* pRDT =   
      _VxModule.GetIVsRunningDocumentTable();  
    ASSERT(pRDT);  
    if (!pRDT)  
        return;  
  
    CComPtr<IUnknown> srpDocData;  
    VSCOOKIE vscookie = VSCOOKIE_NIL;  
    pRDT->FindAndLockDocument(RDT_NoLock, T2COLE(m_strMkDocument),    
      NULL, NULL, &srpDocData, &vscookie);  
    if ( (vscookie == VSCOOKIE_NIL) || !srpDocData)  
        return;  
    CComPtr<IVsFileChangeEx> srpIVsFileChangeEx;  
    HRESULT hr = _VxModule.QueryService(SID_SVsFileChangeEx,   
      IID_IVsFileChangeEx, (void **)&srpIVsFileChangeEx);  
    if (SUCCEEDED(hr) && srpIVsFileChangeEx)  
    {  
        m_fFileChangeSuspended = TRUE;  
        srpIVsFileChangeEx->IgnoreFile(NULL, m_strMkDocument, TRUE);   
        srpDocData->QueryInterface(IID_IVsDocDataFileChangeControl,   
          (void**)&m_srpIVsDocDataFileChangeControl);  
        if(m_srpIVsDocDataFileChangeControl)  
            m_srpIVsDocDataFileChangeControl->IgnoreFileChanges(TRUE);  
    }  
}  
void CSuspendFileChanges::Resume()  
{  
    if(!m_fFileChangeSuspended)  
        return;  
  
    CComPtr<IVsFileChangeEx> srpIVsFileChangeEx;  
    HRESULT hr = _VxModule.QueryService(SID_SVsFileChangeEx,   
      IID_IVsFileChangeEx, (void **)&srpIVsFileChangeEx);  
    if (SUCCEEDED(hr) && srpIVsFileChangeEx)  
  
    srpIVsFileChangeEx->IgnoreFile(NULL, m_strMkDocument, FALSE);   
    if(m_srpIVsDocDataFileChangeControl)  
        m_srpIVsDocDataFileChangeControl->IgnoreFileChanges(FALSE);  
    m_fFileChangeSuspended = FALSE;  
    m_srpIVsDocDataFileChangeControl.Release();  
}  
// Misc. helper classes  
```  
  
## <a name="robust-programming"></a>강력한 프로그래밍  
 사용자의 경우 소스 코드 제어, 대/소문자와 같이 파일에 여러 변경 내용을 포함 하는 경우 다음 반드시 전역 파일 변경 알림 경고 문서 데이터 파일 변경 내용에 대 한 모니터링을 재개 하기 전에 다시 시작 합니다.
