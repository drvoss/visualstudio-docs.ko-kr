---
title: IActiveScriptSiteWindow::GetWindow | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptSiteWindow.GetWindow
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSiteWindow_GetWindow
ms.assetid: 6284e38c-9dfb-4d69-903d-f243f78c0331
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7b6efa066765339375a8315695aa9c1de2f9c46b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62992051"
---
# <a name="iactivescriptsitewindowgetwindow"></a>IActiveScriptSiteWindow::GetWindow
스크립팅 엔진을 표시 해야 하는 팝업 창의 소유자 역할을 수행할 수 있는 창에 핸들을 검색 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT GetWindow(  
    HWND *phwnd  // address of variable for window handle  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `phwnd`  
 [out] 창 핸들을 받는 변수의 주소입니다.  
  
## <a name="return-value"></a>반환 값  
 반환 `S_OK` 성공 하면 또는 `E_FAIL` 오류가 발생 합니다.  
  
## <a name="remarks"></a>설명  
 이 메서드는 비슷합니다는 `IOleWindow::GetWindow` 메서드.  
  
## <a name="see-also"></a>참고 항목  
 [IActiveScriptSiteWindow](../../winscript/reference/iactivescriptsitewindow.md)