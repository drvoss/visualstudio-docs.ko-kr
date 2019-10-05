---
title: SccUninitialize 함수 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- SccUninitialize
helpviewer_keywords:
- SccUninitialize function
ms.assetid: 17cf5337-d251-4422-bc96-93fe7d48f2ae
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: bcb0b3a6718cc90db6f7176c823ccccbbfc05f9a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68190844"
---
# <a name="sccuninitialize-function"></a>SccUninitialize 함수
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

이 함수에 대 한 이전 호출에서 만든 연결 나 할당 정리 합니다 [SccInitialize](../extensibility/sccinitialize-function.md) 소스 제어 플러그 인 종료에 대 한 준비 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
SCCRTN SccUninitialize (  
   LPVOID pvContext  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 pvContext  
 [in] 원본 제어 플러그 인 상황에 맞는 구조에 대 한 포인터에서 생성 된 [SccInitialize](../extensibility/sccinitialize-function.md)합니다.  
  
## <a name="return-value"></a>반환 값  
 원본 제어 플러그 인이 함수의 구현은 다음 값 중 하나를 반환 하:  
  
|값|설명|  
|-----------|-----------------|  
|SCC_OK|정리 완료 되었습니다.|  
  
## <a name="remarks"></a>설명  
 소스 제어 플러그 인는 종료 하기 위해 준비 하 고 상황에 맞는 구조에 대 한 플러그 인에서 할당 메모리를 해제 합니다. 함수는 플러그 인 지정 된 각 인스턴스에 대해 한 번씩 호출 됩니다. 에 대 한 호출을 [SccInitialize](../extensibility/sccinitialize-function.md) 이 호출 앞에 옵니다. 프로젝트가 없으므로 계속 열 수에 대 한 호출 시 `SccUninitialize`합니다.  
  
## <a name="see-also"></a>참고 항목  
 [원본 제어 플러그 인 API 함수](../extensibility/source-control-plug-in-api-functions.md)   
 [SccInitialize](../extensibility/sccinitialize-function.md)
