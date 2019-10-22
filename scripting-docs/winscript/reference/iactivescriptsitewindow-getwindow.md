---
title: 'IActiveScriptSiteWindow:: GetWindow | Microsoft Docs'
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
ms.openlocfilehash: d8263db447c7692ec7b0982127d63b4bea588a4b
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574350"
---
# <a name="iactivescriptsitewindowgetwindow"></a>IActiveScriptSiteWindow::GetWindow
스크립팅 엔진에서 표시 해야 하는 팝업 창의 소유자 역할을 할 수 있는 창에 대 한 핸들을 검색 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT GetWindow(  
    HWND *phwnd  // address of variable for window handle  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `phwnd`  
 제한이 창 핸들을 받는 변수의 주소입니다.  
  
## <a name="return-value"></a>반환 값  
 성공 하면 `S_OK`을 반환 하 고, 오류가 발생 한 경우 `E_FAIL` 합니다.  
  
## <a name="remarks"></a>주의  
 이 메서드는 `IOleWindow::GetWindow` 메서드와 비슷합니다.  
  
## <a name="see-also"></a>참조  
 [IActiveScriptSiteWindow](../../winscript/reference/iactivescriptsitewindow.md)