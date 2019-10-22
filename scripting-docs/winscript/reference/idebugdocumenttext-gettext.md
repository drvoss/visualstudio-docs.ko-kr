---
title: 'IDebugDocumentText:: GetText | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentText.GetText
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentText::GetText
ms.assetid: 3c940a30-6c0f-4deb-aa4d-21a0bdef8461
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e6472c40802fff4dad6e5ecc8f2729c95459e09f
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572077"
---
# <a name="idebugdocumenttextgettext"></a>IDebugDocumentText::GetText
문자 위치 범위와 연결 된 문자 및/또는 문자 특성을 검색 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT GetText(  
   ULONG              cCharacterPosition,  
   WCHAR*             pcharText,  
   SOURCE_TEXT_ATTR*  pstaTextAttr,  
   ULONG*             pcNumChars,  
   ULONG              cMaxChars  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `cCharacterPosition`  
 진행 문자 위치 범위의 시작 위치입니다.  
  
 `pcharText`  
 [in, out] 문자 텍스트 버퍼입니다. 버퍼는 `cMaxChars` 문자를 저장할 수 있을 만큼 커야 합니다. 이 매개 변수가 NULL 이면 메서드는 문자를 반환 하지 않습니다.  
  
 `pstaTextAttr`  
 [in, out] 문자 특성 버퍼입니다. 버퍼는 `cMaxChars` 문자를 저장할 수 있을 만큼 커야 합니다. 이 매개 변수가 NULL 이면 메서드는 특성을 반환 하지 않습니다.  
  
 `pcNumChars`  
 [in, out] 반환 된 문자/특성의 수입니다. 이 메서드를 호출 하기 전에이 매개 변수를 0으로 설정 해야 합니다.  
  
 `cMaxChars`  
 진행 문자 위치 범위의 문자 수입니다. 또한 반환할 최대 문자 수를 지정 합니다.  
  
## <a name="return-value"></a>반환 값  
 메서드는 `HRESULT`를 반환 합니다. 가능한 값에는 다음 표에 있는 값이 포함되지만, 이에 국한되는 것은 아닙니다.  
  
|값|설명|  
|-----------|-----------------|  
|`S_OK`|메서드가 성공했으며|  
  
## <a name="remarks"></a>주의  
 이 메서드는 문자 위치 범위와 연결 된 문자 및/또는 문자 특성을 검색 합니다. 문자 위치 범위는 문자 위치 및 문자 수로 지정 됩니다.  
  
## <a name="see-also"></a>참조  
 [Idebugdocumenttext 인터페이스](../../winscript/reference/idebugdocumenttext-interface.md)    
 [SOURCE_TEXT_ATTR 열거형](../../winscript/reference/source-text-attr-enumeration.md)