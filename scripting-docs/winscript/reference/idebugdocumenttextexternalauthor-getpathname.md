---
title: 'IDebugDocumentTextExternalAuthor:: GetPathName | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentTextExternalAuthor.GetPathName
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentTextExternalAuthor::GetPathName
ms.assetid: 445152a1-9cf8-402e-93d6-3d4bf2b81d17
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e876b41ce1bde4defffd11267c6665f9d57da077
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575964"
---
# <a name="idebugdocumenttextexternalauthorgetpathname"></a>IDebugDocumentTextExternalAuthor::GetPathName
문서의 전체 경로와 파일 이름을 반환 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT GetPathName(  
   BSTR*  pbstrLongName,  
   BOOL*  pfIsOriginalFile  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `pbstrLongName`  
 제한이 전체 경로 및 파일 이름을 포함 하는 문자열입니다.  
  
 `pfIsOriginalFile`  
 제한이 경로 및 파일 이름이 원본 문서를 참조 하는지 여부를 나타내는 부울입니다.  
  
## <a name="return-value"></a>반환 값  
 메서드는 `HRESULT`를 반환 합니다. 가능한 값에는 다음 표에 있는 값이 포함되지만, 이에 국한되는 것은 아닙니다.  
  
|값|설명|  
|-----------|-----------------|  
|`S_OK`|메서드가 성공했으며|  
|`E_FAIL`|원본 파일을 만들거나 확인할 수 없습니다.|  
  
## <a name="remarks"></a>주의  
 이 메서드는 문서의 전체 경로와 파일 이름을 반환 합니다.  
  
 @No__t_0 FALSE 이면 `pbstrLongName`의 경로 및 파일 이름이 새로 만든 임시 파일을 참조 합니다.  
  
## <a name="see-also"></a>참조  
 [IDebugDocumentTextExternalAuthor 인터페이스](../../winscript/reference/idebugdocumenttextexternalauthor-interface.md)