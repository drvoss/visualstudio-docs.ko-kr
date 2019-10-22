---
title: 'IActiveScriptError:: GetSourceLineText | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptError.GetSourceLineText
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptError_GetSourceLineText
ms.assetid: 64f7f37f-7288-4dbe-b626-a35d90897f36
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ded57f97ec40167bac34bf0f288c2e3d15a5c4b7
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576910"
---
# <a name="iactivescripterrorgetsourcelinetext"></a>IActiveScriptError::GetSourceLineText
스크립팅 엔진에서 스크립트를 실행 하는 동안 오류가 발생 한 소스 파일의 줄을 검색 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT GetSourceLineText(  
    BSTR *pbstrSourceLine  // address of buffer for source line  
);  
```  
  
## <a name="parameter"></a>매개 변수  
 `pbstrSourceLine`  
 제한이 오류가 발생 한 소스 코드 줄을 수신 하는 버퍼의 주소입니다.  
  
## <a name="return-value"></a>반환 값  
 성공 하면 `S_OK`을 반환 하 고, 소스 파일의 줄을 검색 하지 않은 경우 `E_FAIL`을 반환 합니다.  
  
## <a name="see-also"></a>참조  
 [IActiveScriptError](../../winscript/reference/iactivescripterror.md)