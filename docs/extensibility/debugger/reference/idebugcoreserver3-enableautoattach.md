---
title: IDebugCoreServer3::EnableAutoAttach | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugCoreServer3::EnableAutoAttach
helpviewer_keywords:
- IDebugCoreServer3::EnableAutoAttach
ms.assetid: 06aa633b-263b-4e08-8844-9a52d5120b94
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e5fc3ab0767a7077860c82acefc9554ba1228cee
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49831122"
---
# <a name="idebugcoreserver3enableautoattach"></a>IDebugCoreServer3::EnableAutoAttach
지정 된 디버그 엔진에 대 한 자동 연결을 사용 하도록 설정 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
HRESULT EnableAutoAttach(  
   GUID*     rgguidSpecificEngines,  
   DWORD     celtSpecificEngines,  
   LPCOLESTR pszStartPageUrl,  
   BSTR*     pbstrSessionId  
);  
```  
  
```csharp  
int EnableAutoAttach(  
   Guid[]     rgguidSpecificEngines,  
   uint       celtSpecificEngines,  
   string     pszStartPageUrl,  
   out string pbstrSessionId  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `rgguidSpecificEngines`  
 [in] 자동 연결로 표시할 각 디버그 엔진에 대 한 Guid의 배열입니다.  
  
 `celtSpecificEngines`  
 [in] 에 지정 된 엔진 수가 `rgguidSpecificEngines`합니다.  
  
 `pszStartPageUrl`  
 [in] 자동 연결 하는 경우 사용할 시작 URL입니다.  
  
 `pbstrSessionID`  
 [out] 자동 연결 된 세션 ID입니다.  
  
## <a name="return-value"></a>반환 값  
 성공 하면 반환 `S_OK`; 그렇지 않으면 오류 코드를 반환 합니다. 하나의 오류 코드는 `E_AUTO_ATTACH_NOT_REGISTERED`, auto-attach 클래스 팩터리를 등록 되지 않은 나타냅니다.  
  
## <a name="remarks"></a>설명  
 지정 된 URL에 연결 된 프로그램이 시작 되 면 지정 된 디버그 엔진을 자동으로 시작 및 연결 합니다.  
  
## <a name="see-also"></a>참고 항목  
 [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)