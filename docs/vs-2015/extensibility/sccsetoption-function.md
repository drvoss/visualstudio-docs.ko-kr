---
title: SccSetOption 함수 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- SccSetOption
helpviewer_keywords:
- SccSetOption function
ms.assetid: 4b5e6666-c24c-438a-a9df-9c52f58f8175
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7f2660ca99d8704f5dd8e7b9aa66c9c8fc5bdbb6
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68143743"
---
# <a name="sccsetoption-function"></a>SccSetOption 함수
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

이 함수는 소스 제어 플러그 인의 동작을 제어 하는 옵션을 설정 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
SCCRTN SccSetOption(  
   LPVOID pvContext,  
   LONG   nOption,  
   LONG   dwVal  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 pvContext  
 [in] 원본 제어 플러그 인 상황에 맞는 구조입니다.  
  
 nOption  
 [in] 설정 되는 옵션입니다.  
  
 dwVal  
 [in] 옵션에 대 한 설정입니다.  
  
## <a name="return-value"></a>반환 값  
 원본 제어 플러그 인이 함수의 구현은 다음 값 중 하나를 반환 하:  
  
|값|설명|  
|-----------|-----------------|  
|SCC_OK|옵션을 설정 했습니다.|  
|SCC_I_SHARESUBPROJOK|경우 반환 되는 `nOption` 된 `SCC_OPT_SHARESUBPROJ` 하 고 소스 제어 플러그 인 대상 폴더를 설정 하기 위해 IDE를 허용 합니다.|  
|SCC_E_OPNOTSUPPORTED|옵션이 설정 되지 않은 및 시 해서는 안 됩니다.|  
  
## <a name="remarks"></a>설명  
 IDE는 플러그 인 소스 제어의 동작을 제어 하려면이 함수를 호출 합니다. 첫 번째 매개 변수를 `nOption`, 두 번째 하는 동안 설정 되는 값을 나타내는 `dwVal`, 해당 값을 사용 하 여 수행할 작업을 나타냅니다. 플러그 인 연결 된이 정보를 저장을 `pvContext``,` IDE 호출한 후이 함수를 호출 해야 하므로 합니다 [SccInitialize](../extensibility/sccinitialize-function.md) (각 호출 후 반드시 합니다 [SccOpenProject](../extensibility/sccopenproject-function.md)).  
  
 옵션 및 해당 값의 요약:  
  
|`nOption`|`dwValue`|Description|  
|---------------|---------------|-----------------|  
|`SCC_OPT_EVENTQUEUE`|`SCC_OPT_EQ_DISABLE`<br /><br /> `SCC_OPT_EQ_ENABLE`|이벤트 큐 백그라운드 하는 설정 하거나 해제 합니다.|  
|`SCC_OPT_USERDATA`|임의 값|에 전달할 사용자 값을 지정 합니다 [OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md) 콜백 함수입니다.|  
|`SCC_OPT_HASCANCELMODE`|`SCC_OPT_HCM_NO`<br /><br /> `SCC_OPT_HCM_YES`|지원 하는지 여부를 IDE 현재 작업 취소를 나타냅니다.|  
|`SCC_OPT_NAMECHANGEPFN`|에 대 한 포인터를 [OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md) 콜백 함수|이름 변경 콜백 함수에 대 한 포인터를 설정합니다.|  
|`SCC_OPT_SCCCHECKOUTONLY`|`SCC_OPT_SCO_NO`<br /><br /> `SCC_OPT_SCO_YES`|IDE 허용 여부는 체크 아웃 해야만 소스 제어 플러그 인을 통해 또는 수동으로 (소스 제어 사용자 인터페이스를 통해) 해당 파일을 검사 하는지 여부를 나타냅니다.|  
|`SCC_OPT_SHARESUBPROJ`|N/A|소스 제어 플러그 인 로컬 프로젝트 폴더를 지정 하기 위해 IDE를 허용 하는 경우 플러그 인 반환 `SCC_I_SHARESUBPROJOK`합니다.|  
  
## <a name="sccopteventqueue"></a>SCC_OPT_EVENTQUEUE  
 하는 경우 `nOption` 는 `SCC_OPT_EVENTQUEUE`, IDE 사용 하지 않도록 설정 (또는 다시 사용 하도록 설정) 백그라운드 작업을 처리 합니다. 예를 들어를 컴파일하는 동안 IDE는 소스 제어 플러그 인 모든 종류의 유휴에서 처리를 중지를 지시할 수 있습니다. 컴파일 후 이벤트 큐에 대 한 플러그 인을 최신 상태로 유지 하는 백그라운드 처리를 다시 활성화는 것입니다. 에 해당 하는 `SCC_OPT_EVENTQUEUE` 의 값 `nOption`, 두 개의 가능한 값에 대 한 `dwVal`, 즉 `SCC_OPT_EQ_ENABLE` 및 `SCC_OPT_EQ_DISABLE`합니다.  
  
## <a name="sccopthascancelmode"></a>SCC_OPT_HASCANCELMODE  
 경우에 대 한 값 `nOption` 는 `SCC_OPT_HASCANCELMODE`, IDE 장기 작업을 취소할 수 있습니다. 설정 `dwVal` 에 `SCC_OPT_HCM_NO` (기본값) IDE 취소 모드 없음 있음을 나타냅니다. 소스 제어 플러그 인을 취소 하려면 사용자가 자체 취소 단추를 제공 해야 합니다. `SCC_OPT_HCM_YES` IDE 플러그 인 SCC 자체 취소 단추를 표시 하지 않아도 되므로 작업을 취소 하는 기능을 제공 함을 나타냅니다. IDE 설정 하는 경우 `dwVal` 하 `SCC_OPT_HCM_YES`, 응답할 준비 되 면 `SCC_MSG_STATUS` 및 `DOCANCEL` 로 전송 된 메시지를 `lpTextOutProc` 콜백 함수 (참조 [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)). IDE는이 변수를 설정 하지 않으면, 플러그 인 보내지 않아야 이러한 두 메시지입니다.  
  
## <a name="sccoptnamechangepfn"></a>SCC_OPT_NAMECHANGEPFN  
 NOption로 설정 된 경우 `SCC_OPT_NAMECHANGEPFN`, 및 두 원본 제어 플러그 인 및 IDE 있도록, 플러그 인 수 실제로 이름 바꾸기 또는 소스 제어 작업을 하는 동안 파일을 이동 합니다. 합니다 `dwVal` 함수 포인터 형식으로 설정 됩니다 [OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md)합니다. 소스 제어 작업을 하는 동안 플러그 인이 함수를 호출, 세 개의 매개 변수를 전달 합니다. 이 해당 파일 및 IDE와 관련 된 정보에 대 한 포인터의 새 이름 (정규화 된 경로 포함) 파일의 이전 이름 (정규화 된 경로 포함)입니다. 호출 하 여이 마지막 포인터에서 IDE를 보냅니다 `SccSetOption` 사용 하 여 `nOption` 로 설정 `SCC_OPT_USERDATA`를 사용 하 여 `dwVal` 데이터를 가리키는 합니다. 이 함수에 대 한 지원을 선택 사항입니다. VSSCI 플러그-를 사용 하 여가이 기능 초기화 해야 해당 함수 포인터와 사용자 데이터 변수를 `NULL`, 권한이 부여 된 한 경우가 아니면 rename 함수를 호출 하지 해야 합니다. 또한 준비 해야 하는 새 호출에 대 한 응답의 설정을 변경 하려면 또는 지정 된 값을 보유할 `SccSetOption`합니다. 소스 제어 명령 작업 도중 발생 하지 않을 수 있지만 명령 간에 발생할 수 있습니다.  
  
## <a name="sccoptscccheckoutonly"></a>SCC_OPT_SCCCHECKOUTONLY  
 NOption로 설정 된 경우 `SCC_OPT_SCCCHECKOUTONLY`, IDE이는 현재 열려 있는 프로젝트의 파일 되지 체크 아웃 해야 수동으로 소스 제어 시스템의 사용자 인터페이스를 통해 표시 됩니다. 대신 파일은 체크 아웃할 수 IDE 제어 플러그 인 소스 제어를 사용할 때만 합니다. 하는 경우 `dwValue` 로 설정 된 `SCC_OPT_SCO_NO`, 즉, 파일 플러그 인에서 정상적으로 처리 되어야 하 고 원본 제어 UI 통해 체크 아웃할 수 있습니다. 하는 경우 `dwValue` 로 설정 된 `SCC_OPT_SCO_YES`, 다음만 플러그 인은 수 파일을 체크 아웃 및 소스 제어 시스템의 UI를 호출 해야 합니다. IDE는 IDE를 사용할 때만 확인 하는 것이 "의사 (pseudo) 파일" 있을 수 있는 상황입니다.  
  
## <a name="sccoptsharesubproj"></a>SCC_OPT_SHARESUBPROJ  
 하는 경우`nOption` 로 설정 된 `SCC_OPT_SHARESUBPROJ`, IDE는 소스 제어 플러그 인 소스 제어에서 파일을 추가할 때 지정된 된 로컬 폴더를 사용할 수 있는지 여부를 테스트 합니다. 값을 `dwVal` 매개 변수는이 경우 중요 하지 않습니다. 플러그 인 파일 원본에서 추가 될 위치는 로컬 대상 폴더를 지정 하는 IDE를 허용 하는 경우 제어는 [SccAddFromScc](../extensibility/sccaddfromscc-function.md) 플러그 인을 반환 해야 합니다 라고 `SCC_I_SHARESUBPROJOK` 때는 `SccSetOption` 함수는 호출 됩니다. IDE를 사용 하 여는 `lplpFileNames` 의 매개 변수는 `SccAddFromScc` 대상 폴더에 전달 하는 함수입니다. 플러그 인 소스 제어에서 추가 된 파일을 배치할 대상 폴더를 사용 합니다. 플러그 인을 반환 하지 않는 경우 `SCC_I_SHARESUBPROJOK` 경우는 `SCC_OPT_SHARESUBPROJ` 옵션이 설정 되어, IDE는 플러그 인은 현재 로컬 폴더에만 파일을 추가할 수 있다고 가정 합니다.  
  
## <a name="see-also"></a>참고 항목  
 [원본 제어 플러그 인 API 함수](../extensibility/source-control-plug-in-api-functions.md)   
 [SccInitialize](../extensibility/sccinitialize-function.md)   
 [SccOpenProject](../extensibility/sccopenproject-function.md)   
 [SccAddFromScc](../extensibility/sccaddfromscc-function.md)   
 [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)   
 [OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md)
