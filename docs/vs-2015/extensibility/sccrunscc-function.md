---
title: SccRunScc 함수 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- SccRunScc
helpviewer_keywords:
- SccRunScc function
ms.assetid: bbe7c931-b17a-4779-9cf6-59e5f9f0c172
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d2b36bd226d4eb19a694347edcba51812ee6f771
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68190878"
---
# <a name="sccrunscc-function"></a>SccRunScc 함수
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

이 함수는 원본 제어 관리 도구를 호출합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
SCCRTN SccRunScc(  
   LPVOID  pvContext,  
   HWND    hWnd,  
   LONG    nFiles,  
   LPCSTR* lpFileNames  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 pvContext  
 [in] 원본 제어 플러그 인 상황에 맞는 구조입니다.  
  
 hWnd  
 [in] 소스 제어 플러그 인을 제공 하는 모든 대화 상자에 대 한 부모로 사용할 수 있는 IDE 창 핸들입니다.  
  
 nFiles  
 [in] 에 지정 된 파일 수는 `lpFileNames` 배열입니다.  
  
 lpFileNames  
 [in] 선택한 파일 이름의 배열입니다.  
  
## <a name="return-value"></a>반환 값  
 원본 제어 플러그 인이 함수의 구현은 다음 값 중 하나를 반환 하:  
  
|값|Description|  
|-----------|-----------------|  
|SCC_OK|소스 제어 관리 도구를 호출 했습니다.|  
|SCC_I_OPERATIONCANCELED|작업이 취소 되었습니다.|  
|SCC_E_INITIALIZEFAILED|소스 제어 시스템을 초기화 하지 못했습니다.|  
|SCC_E_ACCESSFAILURE|소스 제어 시스템에 경합 또는 네트워크 문제로 인해 액세스 문제가 있습니다.|  
|SCC_E_CONNECTIONFAILURE|소스 제어 시스템에 연결 하지 못했습니다.|  
|SCC_E_FILENOTCONTROLLED|선택한 파일이 소스 제어 없습니다.|  
|SCC_E_NONSPECIFICERROR|알 수 없는 오류가 발생 했습니다.|  
  
## <a name="remarks"></a>설명  
 이 함수는 호출자가 외부 관리 도구를 통해 광범위 한 소스 제어 시스템의 기능에 액세스할 수 있도록 합니다. 소스 제어 시스템에 사용자 인터페이스가 없는 경우 소스 제어 플러그 인 필요한 관리 기능을 수행 하는 인터페이스를 구현할 수 있습니다.  
  
 이 함수는 수 및 현재 선택한 파일의 파일 이름 배열을 사용 하 여 호출 됩니다. 관리 도구에서 지 원하는 경우 파일의 목록을 데 사용할 수 있습니다 관리 인터페이스에서 파일을 미리 선택 그렇지 않으면 목록 무시할 수 있습니다.  
  
 사용자가 선택 하는 경우에 일반적으로이 함수가 호출 되는 **시작 \<소스 제어 서버 >** 에서 합니다 **파일** -> **소스 제어** 메뉴입니다. 이렇게 **시작** 메뉴 옵션 항상 사용 하지 않도록 설정 하거나도 레지스트리 항목을 설정 하 여 숨길 수 있습니다. [방법: 원본 제어 플러그 인 설치](../extensibility/internals/how-to-install-a-source-control-plug-in.md) 세부 정보에 대 한 합니다. 경우에이 함수를 호출 [SccInitialize](../extensibility/sccinitialize-function.md) 를 반환 합니다 `SCC_CAP_RUNSCC` 기능 비트 (참조 [기능 플래그](../extensibility/capability-flags.md) 이 및 다른 기능 비트에 대 한 자세한 내용은).  
  
## <a name="see-also"></a>참고 항목  
 [원본 제어 플러그 인 API 함수](../extensibility/source-control-plug-in-api-functions.md)   
 [방법: 소스 제어 플러그 인 설치](../extensibility/internals/how-to-install-a-source-control-plug-in.md)   
 [기능 플래그](../extensibility/capability-flags.md)   
 [SccInitialize](../extensibility/sccinitialize-function.md)
