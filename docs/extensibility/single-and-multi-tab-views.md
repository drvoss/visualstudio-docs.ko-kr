---
title: 단일 및 다중 탭 보기 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - single and multi-tab views
ms.assetid: e3611704-349f-4323-b03c-f2b0a445d781
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: def68627223ba082f5ec6a3ef571e314feae33f3
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66332050"
---
# <a name="single-and-multi-tab-views"></a>단일 및 다중 탭 보기
편집기 다양 한 뷰를 만들 수 있습니다. 한 가지 예는 코드 편집기 창은 다른 폼 디자이너가 있습니다.

 다중 탭 보기 여러 탭이 있는 뷰입니다. 예를 들어, HTML 편집기에 맨 아래에 두 개의 탭이 있습니다. **디자인** 하 고 **소스**각 논리적 보기. 디자인 뷰를 다른 웹 페이지를 구성 하는 HTML을 표시 하는 동안 렌더링된 된 웹 페이지를 표시 합니다.

## <a name="accessing-physical-views"></a>실제 보기에 액세스
 실제 뷰 문서 뷰 개체를 각각 나타내는 코드 또는 양식과 같은 버퍼에 데이터의 뷰를 호스트 합니다. 따라서 각 문서 뷰 개체에 물리적 뷰 (실제 뷰 문자열로 알려진 것으로 식별 됨) 및 일반적으로 단일 논리적 보기

 그러나 경우에 따라 실제 뷰 논리 뷰를 두 개 이상 있을 수 있습니다. 몇 가지 예는 side-by-side-보기를 사용 하 여 분할 창에 있는 편집기 또는 GUI/디자인 보기 및 코드 숨김-the-형식 뷰를 포함 하는 폼 디자이너입니다.

 모든 사용 가능한 실제 보기에 액세스 하려면 편집기를 사용 하려면 편집기 팩터리를 만들 수 있는 문서 뷰 개체의 각 형식에 대 한 고유한 물리적 보기 문자열을 만들어야 합니다. 예를 들어를 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 편집기 팩터리 문서 뷰 개체는 코드 창 및 forms 디자이너 창을 만들 수 있습니다.

## <a name="creating-multi-tabbed-views"></a>다중 탭 보기 만들기
 문서 뷰 개체는 고유한 물리적 보기 문자열을 통해 실제 보기를 사용 하 여 연결 되어야 합니다, 하지만 다른 방법으로 데이터를 볼 수 있도록 실제 뷰 내에 있는 여러 탭을 배치할 수 있습니다. 이 탭이 여러 개 구성에서 모든 탭은 동일한 실제 보기 문자열을와 연결 되지만 다른 논리 보기 GUID를 지정 하는 각 탭 합니다.

 편집기에 대 한 다중 탭 보기를 만들려면 다음을 구현 합니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsMultiViewDocumentView> 인터페이스를 다양 한 논리적 보기 GUID에 연결 하 여 (<xref:Microsoft.VisualStudio.Shell.Interop.LogicalViewID>) 만든 각 탭을 사용 하 여 합니다.

 Visual Studio HTML 편집기는 다중 탭 보기를 사용 하 여 편집기의 예시입니다. 있기 **디자인** 하 고 **원본** 탭 합니다. 이 작업이 가능 하도록 다양 한 논리 뷰는 각 탭에 연결 `LOGICALVIEWID_TextView` 에 대 한 합니다 **디자인** 탭 및 `LOGICALVIEWID_Code` 에 대 한 합니다 **원본** 탭 합니다.

 VSPackage는 적절 한 논리 뷰를 지정 하 여 폼을 디자인, 코드 편집, 코드 디버깅 등 특정 목적에 해당 하는 뷰에 액세스할 수 있습니다. 그러나 창 중 하나는 NULL 문자열에 의해 식별 되어야 합니다 및 기본 논리 보기에 해당 해야 합니다 (`LOGVIEWID_Primary`).

 다음 표에서 사용 가능한 논리 보기 값 및 용도 나열합니다.

|LOGVIEWID GUID|권장된 사용|
|--------------------|---------------------|
|`LOGVIEWID_Primary`|편집기 팩터리의 기본/기본 보기입니다.<br /><br /> 모든 편집기 팩터리는이 값을 지원 해야 합니다. 이 보기는 해당 물리적 보기 문자열로 NULL 문자열을 사용 해야 합니다. 하나 이상의 논리 보기는이 값으로 설정 되어야 합니다.|
|`LOGVIEWID_Debugging`|뷰를 디버깅 합니다. 일반적으로 `LOGVIEWID_Debugging` 동일한 뷰로 매핑됩니다 `LOGVIEWID_Code`합니다.|
|`LOGVIEWID_Code`|보기에서 시작 합니다 **코드 보기** 명령입니다.|
|`LOGVIEWID_Designer`|보기에서 시작 합니다 **양식 보기** 명령입니다.|
|`LOGVIEWID_TextView`|텍스트 편집기 보기입니다. 반환 하는 뷰입니다 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>에서 액세스할 수 있습니다 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>합니다.|
|`LOGVIEWID_UserChooseView`|뷰를 사용 하 여 선택 하 라는 메시지입니다.|
|`LOGVIEWID_ProjectSpecificEditor`|로 전달 된 **연결 프로그램** 대화 상자<br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.OpenItem%2A><br /><br /> 때 사용자는 "(프로젝트 기본 편집기)" 항목을 선택 합니다.|

 논리 뷰 Guid는 확장 가능한, VSPackage에 정의 된 논리적 보기 Guid만 사용할 수 있습니다.

 Visual Studio 종료 편집기 팩터리 및 솔루션을 다시 열 때 문서 창을 다시 열려면 사용할 수 있도록 문서 창과 사용 하 여 연결 된 실제 뷰 문자열의 GUID를 유지 합니다. 솔루션을 닫으면 열려 있는 창은 솔루션 (.suo) 파일에 유지 됩니다. 이러한 값에 해당는 `VSFPROPID_guidEditorType` 및 `VSFPROPID_pszPhysicalView` 전달 된 값을 `propid` 에서 매개 변수는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> 메서드.

## <a name="example"></a>예제
 이 코드 조각을 보여 줍니다 하는 방법을 <xref:Microsoft.VisualStudio.Shell.Interop.LogicalViewID.TextView> 개체를 구현 하는 뷰에 액세스할 수는 `IVsCodeWindow`합니다. 이 경우에 <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShellOpenDocument> 서비스를 사용 하 여를 호출 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenDocumentViaProject%2A> 및 요청 `LOGVIEWID_TextView`는 창 프레임에 대 한 포인터를 가져옵니다. 문서 뷰 개체에 대 한 포인터를 호출 하 여 가져온 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> 의 값을 지정 하 고 `VSFPROPID_DocView`입니다. 문서 보기 개체에서 `QueryInterface` 에 대 한 라고 `IVsCodeWindow`합니다. 예상은 텍스트 편집기가 반환 되 고 문서 보기 개체에서 반환 되는 있으므로 예제의 경우는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> 메서드 코드 창입니다.

```cpp
HRESULT CFindTool::GotoFileLocation(const WCHAR * szFile, long iLine, long iStart, long iLen)
{
  HRESULT hr;
  if (NULL == szFile || !*szFile)
    return E_INVALIDARG;

  if (iLine == -1L)
    return S_FALSE;

  VSITEMID                  itemid;
  VARIANT                   var;
  RECT                      rc;
  IVsUIShellOpenDocument *  pOpenDoc    = NULL;
  IVsCodeWindow *           pCodeWin    = NULL;
  IVsTextView *             pTextView   = NULL;
  IVsUIHierarchy *          pHierarchy  = NULL;
  IVsWindowFrame *          pFrame      = NULL;
  IUnknown *                pUnk        = NULL;
  IVsHighlight *            pHighlight  = NULL;

  IfFailGo(CGlobalServiceProvider::HrQueryService(SID_SVsUIShellOpenDocument, IID_IVsUIShellOpenDocument, (void **)&pOpenDoc));
  IfFailGo(pOpenDoc->OpenDocumentViaProject(szFile, LOGVIEWID_TextView, NULL, &pHierarchy, &itemid, &pFrame));
  pFrame->Show();
  VariantInit(&var);
  IfFailGo(pFrame->GetProperty(VSFPROPID_DocView, &var));
  if (VT_UNKNOWN != var.vt) { hr = E_FAIL; goto Error; }
  pUnk = V_UNKNOWN(&var);
  if (NULL != pUnk)
  {
    IfFailGo(pUnk->QueryInterface(IID_IVsCodeWindow, (void **)&pCodeWin));
    if (SUCCEEDED(hr = pCodeWin->GetLastActiveView(&pTextView)) ||
        SUCCEEDED(hr = pCodeWin->GetPrimaryView(&pTextView)) )
    {
      pTextView->SetSelection(iLine, iStart, iLine, iStart + iLen);
      // uncover selection
      IfFailGo(pTextView->QueryInterface(IID_IVsHighlight, (void**)&pHighlight));
      IfFailGo(SUCCEEDED(pHighlight->GetHighlightRect(&rc)));
      UncoverSelectionRect(&rc);
    }
  }

Error:
  CLEARINTERFACE(pHighlight);
  CLEARINTERFACE(pTextView);
  CLEARINTERFACE(pCodeWin);
  CLEARINTERFACE(pUnk);
  CLEARINTERFACE(pFrame);
  CLEARINTERFACE(pOpenDoc);
  CLEARINTERFACE(pHierarchy);
  RedrawWindow(m_hwndResults, NULL, NULL, RDW_ERASE|RDW_FRAME|RDW_INVALIDATE|RDW_ALLCHILDREN);
  return hr;
}
```

## <a name="see-also"></a>참고 항목
- [여러 문서 보기 지원](../extensibility/supporting-multiple-document-views.md)
- [방법: 문서 데이터에 보기 연결](../extensibility/how-to-attach-views-to-document-data.md)
- [사용자 지정 편집기 및 디자이너 만들기](../extensibility/creating-custom-editors-and-designers.md)