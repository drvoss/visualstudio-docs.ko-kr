---
title: IActiveScriptError | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptError interface
ms.assetid: c8e0288d-38ff-4145-a7e3-f8cdfb72eefe
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ca4d3fe5ff90fc0d116814771308fa599052dba9
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576896"
---
# <a name="iactivescripterror"></a>IActiveScriptError
이 인터페이스를 구현 하는 개체는 스크립팅 엔진에서 처리 되지 않은 오류가 발생할 때마다 [IActiveScriptSite:: OnScriptError](../../winscript/reference/iactivescriptsite-onscripterror.md) 메서드에 전달 됩니다. 그런 다음 호스트는이 개체의 메서드를 호출 하 여 발생 한 오류에 대 한 정보를 가져옵니다.  
  
## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드  
  
|메서드|설명|  
|------------|-----------------|  
|[IActiveScriptError::GetExceptionInfo](../../winscript/reference/iactivescripterror-getexceptioninfo.md)|오류에 대 한 정보를 검색 합니다.|  
|[IActiveScriptError::GetSourcePosition](../../winscript/reference/iactivescripterror-getsourceposition.md)|소스 코드에서 오류가 발생 한 위치를 검색 합니다.|  
|[IActiveScriptError::GetSourceLineText](../../winscript/reference/iactivescripterror-getsourcelinetext.md)|오류가 발생 한 소스 파일의 줄을 검색 합니다.|  
  
## <a name="see-also"></a>참조  
 [액티브 스크립트 인터페이스](../../winscript/reference/active-script-interfaces.md)