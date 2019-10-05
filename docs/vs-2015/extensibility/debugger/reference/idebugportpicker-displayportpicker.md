---
title: IDebugPortPicker::DisplayPortPicker | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- DisplayPortPicker
- IDebugPortPicker::DisplayPortPicker
ms.assetid: 08511ef5-be64-4069-b169-a569cc94bc64
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 3dd9317a73800a3886a5a807e9e28b0c24b2301c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68188371"
---
# <a name="idebugportpickerdisplayportpicker"></a>IDebugPortPicker::DisplayPortPicker
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

사용자가 포트를 선택할 수 있도록 지정 된 대화 상자가 표시 됩니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
HRESULT DisplayPortPicker(  
   HWND hwndParentDialog,  
   BSTR* pbstrPortId  
);  
```  
  
```csharp  
public int DisplayPortPicker(  
   int hwndParentDialog,  
   out string pbstrPortId  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `hwndParentDialog`  
 [in] 부모 대화 상자에 대 한 핸들입니다.  
  
 `pbstrPortId`  
 [out] 포트 식별자 문자열입니다.  
  
## <a name="return-value"></a>반환 값  
 성공 하면 반환 `S_OK`고, 그렇지 않으면 오류 코드를 반환 합니다. 반환 값 `S_FALSE` (또는 반환 값이 `S_OK` 사용 하 여는 `BSTR` 로 설정 `NULL`) 사용자 클릭 했음을 나타냅니다 **취소**합니다.  
  
## <a name="see-also"></a>참고 항목  
 [IDebugPortPicker](../../../extensibility/debugger/reference/idebugportpicker.md)
