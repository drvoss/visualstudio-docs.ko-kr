---
title: IDebugCustomViewer | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugCustomViewer
helpviewer_keywords:
- IDebugCustomViewer interface
ms.assetid: 7aca27d3-c7b8-470f-b42c-d1e9d9115edd
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5f94fe0301777a615fa6dc567311c493ff55a90a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68196292"
---
# <a name="idebugcustomviewer"></a>IDebugCustomViewer
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

이 인터페이스는 식 계산기를 (EE) 형식에 관계 없이가 필요한 속성의 값을 표시할 수 있습니다.  
  
## <a name="syntax"></a>구문  
  
```  
IDebugCustomViewer : IUknown  
```  
  
## <a name="notes-for-implementers"></a>구현자 참고 사항  
 EE 속성의 값을 사용자 지정 형식으로 표시 하려면이 인터페이스를 구현 합니다.  
  
## <a name="notes-for-callers"></a>호출자에 대 한 정보  
 COM의 호출이 `CoCreateInstance` 함수는이 인터페이스를 인스턴스화합니다. 합니다 `CLSID` 전달할 `CoCreateInstance` 레지스트리에서 가져옵니다. 에 대 한 호출 [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) 레지스트리의 위치를 가져옵니다. 예제 뿐만 아니라 세부 정보에 대 한 설명을 참조 하세요.  
  
## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드  
 이 인터페이스는 다음 메서드를 구현합니다.  
  
|메서드|Description|  
|------------|-----------------|  
|[DisplayValue](../../../extensibility/debugger/reference/idebugcustomviewer-displayvalue.md)|지정된 된 값을 표시 하는 데 필요한 무엇이 수행 합니다.|  
  
## <a name="remarks"></a>설명  
 정상적인 방법으로 속성의 값을 표시할 수 없는 경우이 인터페이스는 사용-예를 들어 데이터 테이블 또는 다른 복합 속성 형식입니다. 표시 되는 사용자 지정 뷰어를는 `IDebugCustomViewer` 인터페이스, EE에 관계 없이 특정 형식의 데이터를 표시 하는 것에 대 한 외부 프로그램은 형식 시각화 도우미와에서 다릅니다. EE는 EE 관련 된 사용자 지정 뷰어를 구현 합니다. 사용자는 어떤 유형의 시각화 도우미를 사용할 형식 시각화 도우미 또는 사용자 지정 뷰어를 선택 합니다. 참조 [시각화 및 데이터 보기](../../../extensibility/debugger/visualizing-and-viewing-data.md) 이 프로세스에 대 한 자세한 내용은 합니다.  
  
 사용자 지정 뷰어는 EE와 마찬가지로에 등록 되 고 따라서 언어 GUID와 공급 업체 GUID 필요 합니다. 정확한 메트릭 (또는 레지스트리 항목 이름)는 EE에만 알려집니다. 이 메트릭은 반환 됩니다 합니다 [DEBUG_CUSTOM_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md) 를 호출 하 여 반환 되는 구조 [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)합니다. 메트릭 저장 된 값은는 `CLSID` COM의 전달 되는 `CoCreateInstance` 함수 (예제 참조).  
  
 합니다 [디버깅을 위한 SDK 도우미](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) 함수를 `SetEEMetric`, 사용자 지정 뷰어를 등록할 수 있습니다. "식 계산기" 레지스트리 섹션을 참조 `Debugging SDK Helpers` 특정 레지스트리 키에 대 한 사용자 지정 해야 합니다. 식 계산기를 몇 가지 미리 정의 된 메트릭이 필요 하지만 사용자 지정 뷰어 (EE의 구현자에 의해 정의 됩니다)는 하나의 메트릭 해야 함을 note 합니다.  
  
 일반적으로 사용자 지정 보기가 읽기 전용 데이터를 이후 합니다 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) 인터페이스를 제공 [DisplayValue](../../../extensibility/debugger/reference/idebugcustomviewer-displayvalue.md) 문자열로 제외 하 고 속성의 값을 변경 하는 것에 대 한 메서드가 없습니다. 사용자 지정 인터페이스를 구현 하는 동일한 개체에서 EE 변경 데이터의 임의 요소를 지원 하기 위해 구현 된 `IDebugProperty3` 인터페이스입니다. 이 사용자 지정 인터페이스는 데이터의 임의 블록을 변경 하는 데 필요한 메서드를 제공 합니다.  
  
## <a name="requirements"></a>요구 사항  
 헤더: msdbg.h  
  
 네임스페이스: Microsoft.VisualStudio.Debugger.Interop  
  
 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="example"></a>예제  
 이 예제에 해당 속성이 모든 사용자 지정 뷰어가 경우 속성에서 첫 번째 사용자 지정 뷰어를 가져오는 방법을 보여 줍니다.  
  
```cpp#  
IDebugCustomViewer *GetFirstCustomViewer(IDebugProperty2 *pProperty)  
{  
    // This string is typically defined globally.  For this example, it  
    // is defined here.  
    static const WCHAR strRegistrationRoot[] = L"Software\\Microsoft\\VisualStudio\\8.0Exp";  
    IDebugCustomViewer *pViewer = NULL;  
    if (pProperty != NULL) {  
        CComQIPtr<IDebugProperty3> pProperty3(pProperty);  
        if (pProperty3 != NULL) {  
            HRESULT hr;  
            ULONG viewerCount = 0;  
            hr = pProperty3->GetCustomViewerCount(&viewerCount);  
            if (viewerCount > 0) {  
                ULONG viewersFetched = 0;  
                DEBUG_CUSTOM_VIEWER viewerInfo = { 0 };  
                hr = pProperty3->GetCustomViewerList(0,  
                                                     1,  
                                                     &viewerInfo,  
                                                     &viewersFetched);  
                if (viewersFetched == 1) {  
                    CLSID clsidViewer = { 0 };  
                    CComPtr<IDebugCustomViewer> spCustomViewer;  
                    // Get the viewer's CLSID from the registry.  
                    ::GetEEMetric(viewerInfo.guidLang,  
                                  viewerInfo.guidVendor,  
                                  viewerInfo.bstrMetric,  
                                  &clsidViewer,  
                                  strRegistrationRoot);  
                    if (!IsEqualGUID(clsidViewer,GUID_NULL)) {  
                        // Instantiate the custom viewer.  
                        spCustomViewer.CoCreateInstance(clsidViewer);  
                        if (spCustomViewer != NULL) {  
                            pViewer = spCustomViewer.Detach();  
                        }  
                    }  
                }  
            }  
        }  
    }  
    return(pViewer);  
}  
```  
  
## <a name="see-also"></a>관련 항목  
 [Core 인터페이스](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)   
 [디버깅을 위한 SDK 도우미](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)   
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)
