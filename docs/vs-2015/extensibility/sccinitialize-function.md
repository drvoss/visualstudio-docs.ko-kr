---
title: SccInitialize 함수 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- SccInitialize
helpviewer_keywords:
- SccInitialize function
ms.assetid: 5bc0d28b-2c68-4d43-9e51-541506a8f76e
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ce52b65d028f82d75d4890b0b1298b4d13b7eafa
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68200040"
---
# <a name="sccinitialize-function"></a>SccInitialize 함수
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

이 함수는 소스 제어 플러그 인을 초기화 하 고 기능 및 제한 사항이 통합된 개발 환경 (IDE)를 제공 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
SCCRTN SccInitialize (  
   LPVOID* ppvContext,  
   HWND    hWnd,  
   LPCSTR  lpCallerName,  
   LPSTR   lpSccName,  
   LPLONG  lpSccCaps,  
   LPSTR   lpAuxPathLabel,  
   LPLONG  pnCheckoutCommentLen,  
   LPLONG  pnCommentLen  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `ppvContext`  
 [in] 소스 제어 플러그 인 여기 해당 상황에 맞는 구조에 대 한 포인터를 배치할 수 있습니다.  
  
 `hWnd`  
 [in] 소스 제어 플러그 인을 제공 하는 모든 대화 상자에 대 한 부모로 사용할 수 있는 IDE 창 핸들입니다.  
  
 `lpCallerName`  
 [in] 소스 제어 플러그 인을 호출 하는 프로그램의 이름입니다.  
  
 `lpSccName`  
 [out에서] 소스 제어 플러그 인 이름 자체를 배치 하는 위치 버퍼 (넘지 `SCC_NAME_LEN`).  
  
 `lpSccCaps`  
 [out] 소스 제어 플러그 인의 기능 플래그를 반환합니다.  
  
 `lpAuxPathLabel`  
 [out에서] 소스 제어 플러그 인에 대해 설명 하는 문자열을 배치 하는 위치는 버퍼를 `lpAuxProjPath` 반환한 매개 변수를 [SccOpenProject](../extensibility/sccopenproject-function.md) 및 [SccGetProjPath](../extensibility/sccgetprojpath-function.md) (넘지 `SCC_AUXLABEL_LEN`).  
  
 `pnCheckoutCommentLen`  
 [out] 체크 아웃 주석에 대 한 최대 허용 길이 반환합니다.  
  
 `pnCommentLen`  
 [out] 다른 의견에 대 한 최대 허용 길이 반환합니다.  
  
## <a name="return-value"></a>반환 값  
 원본 제어 플러그 인이 함수의 구현은 다음 값 중 하나를 반환 하:  
  
|값|Description|  
|-----------|-----------------|  
|SCC_OK|원본 제어 초기화에 성공 했습니다.|  
|SCC_E_INITIALIZEFAILED|시스템을 초기화할 수 없습니다.|  
|SCC_E_NOTAUTHORIZED|사용자 지정된 작업을 수행할 수 없습니다.|  
|SCC_E_NONSPECFICERROR|일반 오류입니다. 소스 제어 시스템을 초기화 되지 않았습니다.|  
  
## <a name="remarks"></a>설명  
 먼저 소스 제어 플러그 인을 로드할 때 IDE에서이 함수를 호출 합니다. IDE를 플러그 인에 호출자에 게 이름과 같은 특정 정보를 전달할 수 있습니다. IDE도 다시 가져옵니다 주석 및 기능의 기능에 대 한 최대 허용 길이 같은 특정 정보를.  
  
 합니다 `ppvContext` 가리키는 `NULL` 포인터입니다. 소스 제어 플러그 인 자체 용도에 구조체를 할당 하에서 해당 구조에 대 한 포인터를 저장 `ppvContext`합니다. IDE는 플러그 인 전역 저장소에 문의 하지 않고 컨텍스트 정보를 알고 있어야 하 고 플러그 인의 여러 인스턴스를 지원 하도록 허용이 포인터 마다 다른 VSSCI API 함수에 전달 됩니다. 이 구조는 취소할 때 합니다 [SccUninitialize](../extensibility/sccuninitialize-function.md) 라고 합니다.  
  
 합니다 `lpCallerName` 고 `lpSccName` 이름을 교환 하는 IDE 및 소스 제어 플러그 인 매개 변수를 사용 합니다. 메뉴 또는 대화 상자에서 실제로 표시 될 수 또는 여러 인스턴스 간에 구분 하기 위해 단순히 이러한 이름은 사용할 수 있습니다.  
  
 합니다 `lpAuxPathLabel` 매개 변수는 솔루션 파일에 저장 되 고 소스 제어 플러그 인에 대 한 호출에 전달 하는 보조 프로젝트 경로 확인 하는 주석으로 사용 하는 문자열을 [SccOpenProject](../extensibility/sccopenproject-function.md)합니다. [!INCLUDE[vsvss](../includes/vsvss-md.md)] 문자열을 사용 하 여 "SourceSafe 프로젝트:"; 다른 원본 제어 플러그 인이 특정 문자열을 사용 하 여 하지 않도록 해야 합니다.  
  
 `lpSccCaps` 매개 변수는 소스 제어를 제공 플러그 인-기능을 나타내는 비트를 저장 합니다. (기능 비트의 전체 목록을 참조 하세요 [기능 플래그](../extensibility/capability-flags.md)). 예를 들어, 플러그 인 계획 기능을 설정 플러그 인 호출자가 제공한 콜백 함수에 결과 쓸 SCC_CAP_TEXTOUT 비트 경우. 버전 제어 결과 창을 만들려면 IDE 신호는이 합니다.  
  
## <a name="see-also"></a>관련 항목  
 [원본 제어 플러그 인 API 함수](../extensibility/source-control-plug-in-api-functions.md)   
 [SccUninitialize](../extensibility/sccuninitialize-function.md)   
 [SccOpenProject](../extensibility/sccopenproject-function.md)   
 [기능 플래그](../extensibility/capability-flags.md)
