---
title: SccCloseProject 함수 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- SccCloseProject
helpviewer_keywords:
- SccCloseProject function
ms.assetid: 259c2069-d349-4814-810f-1c3151b7fb84
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7d2364215f528f16d05ecf0c53b152f7334f4b4a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68156141"
---
# <a name="scccloseproject-function"></a>SccCloseProject 함수
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

이 함수는 특정 세션의 끝을 표시 하는 프로젝트를 닫습니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
SCCRTN SccCloseProject (  
   LPVOID pvContext  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 pvContext  
 원본 제어 플러그 인 상황에 맞는 구조입니다.  
  
## <a name="return-value"></a>반환 값  
 원본 제어 플러그 인이 함수의 구현은 다음 값 중 하나를 반환 하:  
  
|값|Description|  
|-----------|-----------------|  
|SCC_OK|프로젝트를 닫았습니다.|  
|SCC_E_PROJNOTOPEN|프로젝트가 현재 열려 있습니다.|  
|SCC_E_NOTAUTHORIZED|사용자는이 작업을 수행할 수 없습니다.|  
|SCC_E_NONSPECIFICERROR|알 수 없는 오류가 발생 했습니다.|  
  
## <a name="remarks"></a>설명  
 합니다 [SccOpenProject](../extensibility/sccopenproject-function.md) 는 항상이 함수 앞에 호출 됩니다. 이 함수에 대 한 호출을 호출 하 여 이어서 합니다 `SccOpenProject` 함수 또는 [SccUninitialize](../extensibility/sccuninitialize-function.md), 완전히 소스 제어 시스템에 대 한 연결을 종료 합니다.  
  
## <a name="see-also"></a>관련 항목  
 [원본 제어 플러그 인 API 함수](../extensibility/source-control-plug-in-api-functions.md)   
 [SccOpenProject](../extensibility/sccopenproject-function.md)   
 [SccInitialize](../extensibility/sccinitialize-function.md)
