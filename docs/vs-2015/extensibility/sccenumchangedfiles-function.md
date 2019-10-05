---
title: SccEnumChangedFiles 함수 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- SccEnumChangedFiles
helpviewer_keywords:
- SccEnumChangedFiles function
ms.assetid: 76cac510-107b-4c1a-ba60-9c39b6db2e71
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 00ef98c93f02aa8e8a1b4ea53f1998d0ab6713a9
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68200122"
---
# <a name="sccenumchangedfiles-function"></a>SccEnumChangedFiles 함수
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

로컬 파일의 목록을 지정 되 면이 함수는 파일은 소스 코드 제어 데이터베이스에서 해당 버전의 다른 결정 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
SCCRTN SccEnumChangedFiles(  
   LPVOID  pContext,  
   HWND    hWnd,  
   LONG    cFiles,  
   LPCSTR* lpFileNames,  
   LONG*   plIsFileDifferent  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 pContext  
 [in] 원본 제어 플러그 인 컨텍스트 포인터입니다.  
  
 hWnd  
 [in] 소스 제어 플러그 인을 제공 하는 모든 대화 상자에 대 한 부모로 사용할 수 있는 IDE 창 핸들입니다.  
  
 cFiles  
 [in] 파일 이름에 지정 된 수의 `lpFileNames` 배열입니다. 또한의 크기를 지정 `plIsFileDifferent` 배열입니다.  
  
 lpFileNames  
 [in] 확인 하려면 로컬 파일 이름의 배열입니다.  
  
 plIsFileDifferent  
 [out에서] 각 파일의 차이 상태를 나타내는 값의 배열 (배열의 이상 이어야 `cFiles` 항목). Nonzero 파일 다른 임을 의미 합니다.  
  
## <a name="return-value"></a>반환 값  
 원본 제어 플러그 인이 함수의 구현은 다음 값 중 하나를 반환 하:  
  
|값|Description|  
|-----------|-----------------|  
|SCC_OK|작업이 완료되었습니다.|  
|SCC_UNSPECIFIEDERROR|일반 오류입니다.|  
  
## <a name="see-also"></a>참고 항목  
 [소스 제어 플러그 인 API 함수](../extensibility/source-control-plug-in-api-functions.md)
