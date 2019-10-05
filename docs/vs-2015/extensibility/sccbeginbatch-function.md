---
title: SccBeginBatch 함수 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- SccBeginBatch
helpviewer_keywords:
- SccBeginBatch function
ms.assetid: 33968183-2e15-4e0d-955b-ca12212d1c25
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 264d9057bf4f17281d6d8a16ed3a6794004e0e21
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68189552"
---
# <a name="sccbeginbatch-function"></a>SccBeginBatch 함수
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

이 함수는 소스 제어 작업의 일괄 처리 시퀀스를 시작합니다. 합니다 [SccEndBatch](../extensibility/sccendbatch-function.md) 일괄 처리를 종료 하도록 호출 됩니다. 이러한 일괄 처리를 중첩할 수 있습니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
SCCRTN SccBeginBatch(void);  
```  
  
#### <a name="parameters"></a>매개 변수  
 없음  
  
## <a name="return-value"></a>반환 값  
 원본 제어 플러그 인이 함수의 구현은 다음 값 중 하나를 반환 하:  
  
|값|Description|  
|-----------|-----------------|  
|SCC_OK|일괄 처리 작업을 성공적으로 시작 합니다.|  
|SCC_E_UNKNOWNERROR|알 수 없는 오류가 발생 했습니다.|  
  
## <a name="remarks"></a>설명  
 원본 제어 일괄 처리는 여러 프로젝트 또는 여러 컨텍스트 간에 동일한 작업을 실행 하는 데 사용 됩니다. 일괄 처리 작업 중 사용자 환경에서 중복 프로젝트 대화 상자를 제거 하기 위해 일괄 처리를 사용할 수 있습니다. 합니다 `SccBeginBatch` 함수 및 [SccEndBatch](../extensibility/sccendbatch-function.md) 함수 쌍으로 작업의 시작과 끝을 표시 하는 데 사용 됩니다. 이러한 중첩 될 수 없습니다. `SccBeginBatch` 일괄 처리 작업이 진행에서 중임을 나타내는 플래그를 설정 합니다.  
  
 일괄 처리 작업을 적용 하는 동안 소스 제어 플러그 인 사용자에 게 최대 모든 질문에 대 한 하나의 대화 상자를 표시 하 고 모든 후속 작업에서 해당 대화 상자에서 응답을 적용 해야 합니다.  
  
## <a name="see-also"></a>관련 항목  
 [원본 제어 플러그 인 API 함수](../extensibility/source-control-plug-in-api-functions.md)   
 [SccEndBatch](../extensibility/sccendbatch-function.md)
