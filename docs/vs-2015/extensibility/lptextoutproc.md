---
title: LPTEXTOUTPROC | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- LPTEXTOUTPROC
helpviewer_keywords:
- SccMsgDataOnMessage structure
- SccMsgDataOnBeforeGetFile structure
- SccMsgDataIsCancelled structure
- LPTEXTOUTPROC callback function
- SccMsgDataOnAfterGetFile structure
ms.assetid: 2025c969-e3c7-4cf4-a5c5-099d342895ea
caps.latest.revision: 22
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f14942ffd59ce2c6eacf7da2d0d1ab252d58e2cb
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68194455"
---
# <a name="lptextoutproc"></a>LPTEXTOUTPROC
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

사용자 통합된 개발 환경 (IDE) 내에서 소스 제어 작업을 실행 하는 경우 소스 제어 플러그 인 작업에 관련 된 오류 또는 상태 메시지를 전달 하려고 합니다. 플러그 인이 목적을 위해 자체 메시지 상자를 표시할 수 있습니다. 그러나 더 원활한 통합을 위한 플러그 인에 전달할 수 문자열 상태 정보를 표시 하는 기본으로 표시 하는 IDE. 이 메커니즘은는 `LPTEXTOUTPROC` 함수 포인터입니다. IDE 오류 및 상태를 표시 하기 위한 (아래에서 자세히 설명)이이 함수를 구현 합니다.  
  
 IDE 소스 제어 플러그 인이 함수에 대 한 함수 포인터 값으로 전달 합니다 `lpTextOutProc` 매개 변수를 호출 하는 경우는 [SccOpenProject](../extensibility/sccopenproject-function.md)합니다. 예를 들어에 대 한 호출 중에 SCC 작업 중를 [SccGet](../extensibility/sccget-function.md) 많은 파일을 포함 하는, 플러그 인 호출할 수는 `LPTEXTOUTPROC` 함수를 주기적으로 표시할 문자열을 전달 합니다. IDE 상태 표시줄, 출력 창에서 또는 적절 하 게 별도 메시지 상자에서에 이러한 문자열을 표시할 수 있습니다. 필요에 따라 IDE를 사용 하 여 특정 메시지를 표시할 수 수를 **취소** 단추입니다. 이렇게 하면 사용자가 작업을 취소 하 고 IDE 다시 플러그 인에이 정보를 전달 하는 기능.  
  
## <a name="signature"></a>서명  
 IDE의 함수 시그니처가 다음 출력:  
  
```cpp#  
typedef LONG (*LPTEXTOUTPROC) (  
   LPSTR display_string,  
   LONG mesg_type  
);  
```  
  
## <a name="parameters"></a>매개 변수  
 display_string  
 표시할 텍스트 문자열입니다. 이 문자열은 캐리지 반환 또는 줄 바꿈 종료할 수 없습니다.  
  
 mesg_type  
 메시지의 형식입니다. 다음 표에서이 매개 변수에 대해 지원 되는 값을 나열합니다.  
  
|값|Description|  
|-----------|-----------------|  
|`SCC_MSG_INFO, SCC_MSG_WARNING, SCC_MSG_ERROR`|메시지는 정보, 경고 또는 오류 것으로 간주 됩니다.|  
|`SCC_MSG_STATUS`|메시지 상태를 표시 하 고 상태 표시줄에 표시할 수 있습니다.|  
|`SCC_MSG_DOCANCEL`|없는 메시지 문자열을 사용 하 여 전송 합니다.|  
|`SCC_MSG_STARTCANCEL`|시작 표시를 **취소** 단추입니다.|  
|`SCC_MSG_STOPCANCEL`|표시를 중지 한 **취소** 단추입니다.|  
|`SCC_MSG_BACKGROUND_IS_CANCELLED`|백그라운드 작업이 취소 될 경우 IDE를 요청 합니다. IDE 반환 `SCC_MSG_RTN_CANCEL` 작업이 취소 되었습니다; 그렇지 않으면 반환 `SCC_MSG_RTN_OK`합니다. `display_string` 로 캐스팅 매개 변수를 [SccMsgDataIsCancelled](#LinkSccMsgDataIsCancelled) 소스 제어 플러그 인에서 제공 하는 구조를 합니다.|  
|`SCC_MSG_BACKGROUND_ON_BEFORE_GET_FILE`|Ide가 파일에 대 한 버전 제어에서 검색 하기 전에 합니다. `display_string` 로 캐스팅 매개 변수를 [SccMsgDataOnBeforeGetFile](#LinkSccMsgDataOnBeforeGetFile) 소스 제어 플러그 인에서 제공 하는 구조를 합니다.|  
|`SCC_MSG_BACKGROUND_ON_AFTER_GET_FILE`|버전 제어에서 검색 한 후에 파일에 대 한 IDE를 지시 합니다. `display_string` 로 캐스팅 매개 변수를 [SccMsgDataOnAfterGetFile](#LinkSccMsgDataOnAfterGetFile) 소스 제어 플러그 인에서 제공 하는 구조를 합니다.|  
|`SCC_MSG_BACKGROUND_ON_MESSAGE`|Ide가 백그라운드 작업의 현재 상태입니다. `display_string` 로 캐스팅 매개 변수를 [SccMsgDataOnMessage](#LinkSccMsgDataOnMessage) 소스 제어 플러그 인에서 제공 하는 구조를 합니다.|  
  
## <a name="return-value"></a>반환 값  
  
|값|Description|  
|-----------|-----------------|  
|SCC_MSG_RTN_OK|표시 된 문자열 또는 작업이 성공적으로 완료 되었습니다.|  
|SCC_MSG_RTN_CANCEL|사용자 작업을 취소 하려고 합니다.|  
  
## <a name="example"></a>예제  
 IDE 호출 한다고 가정 합니다 [SccGet](../extensibility/sccget-function.md) 20 파일 이름의 합니다. 소스 제어 플러그 인 파일 get 중간 작업을 취소 하지 못하게 하려고 했습니다. 호출한 후 각 파일을 가져올 `lpTextOutProc`, 각 파일에 상태 정보를 전달 하 고 보내는 `SCC_MSG_DOCANCEL` 상태가 보고서에 있으면 메시지입니다. 하는 경우 언제 든 지 플러그 인 값을 받은 반환 `SCC_MSG_RTN_CANCEL` IDE에서 취소는 get 작업이 즉시 파일이 더 이상 없습니다 검색 않도록 합니다.  
  
## <a name="structures"></a>구조체  
  
### <a name="LinkSccMsgDataIsCancelled"></a> SccMsgDataIsCancelled  
  
```cpp#  
typedef struct {  
   DWORD dwBackgroundOperationID;  
} SccMsgDataIsCancelled;  
```  
  
 이 구조와 함께 전송 되는 `SCC_MSG_BACKGROUND_IS_CANCELLED` 메시지입니다. 취소 된 백그라운드 작업의 ID를 전달 하는 것이 됩니다.  
  
### <a name="LinkSccMsgDataOnBeforeGetFile"></a> SccMsgDataOnBeforeGetFile  
  
```cpp#  
typedef struct {  
   DWORD dwBackgroundOperationID;  
   PCSTR szFile;  
} SccMsgDataOnBeforeGetFile;  
```  
  
 이 구조와 함께 전송 되는 `SCC_MSG_BACKGROUND_ON_BEFORE_GET_FILE` 메시지입니다. 검색할 파일의 이름 및 검색을 수행 하는 백그라운드 작업의 ID를 전달 하기 위해 사용 됩니다.  
  
### <a name="LinkSccMsgDataOnAfterGetFile"></a> SccMsgDataOnAfterGetFile  
  
```cpp#  
typedef struct {  
   DWORD dwBackgroundOperationID;  
   PCSTR szFile;  
   SCCRTN sResult;  
} SccMsgDataOnAfterGetFile;  
```  
  
 이 구조와 함께 전송 되는 `SCC_MSG_BACKGROUND_ON_AFTER_GET_FILE` 메시지입니다. 검색을 수행 하는 백그라운드 작업의 ID 뿐만 아니라 지정된 된 파일을 검색 한 결과 통신 하는 것이 됩니다. 반환 값을 확인 합니다 [SccGet](../extensibility/sccget-function.md) 결과적으로 지정할 수 있으며 무엇에 대 한 합니다.  
  
### <a name="LinkSccMsgDataOnMessage"></a> SccMsgDataOnMessage  
 [C++]  
  
```  
typedef struct {  
   DWORD dwBackgroundOperationID;  
   PCSTR szMessage;  
   BOOL bIsError;  
} SccMsgDataOnMessage;  
```  
  
 이 구조와 함께 전송 되는 `SCC_MSG_BACKGROUND_ON_MESSAGE` 메시지입니다. 백그라운드 작업의 현재 상태를 통신 하는 것이 됩니다. 상태는 IDE에 의해 표시 되는 문자열로 표현 됩니다 하 고 `bIsError` 메시지의 심각도 나타냅니다 (`TRUE` 에서 오류 메시지입니다. `FALSE` 경고 또는 정보 메시지에 대 한). 전송 상태를 백그라운드 작업의 ID 지정 됩니다.  
  
## <a name="code-example"></a>코드 예  
 호출 하는 간단한 예는 다음과 같습니다 `LPTEXTOUTPROC` 보낼는 `SCC_MSG_BACKGROUND_ON_MESSAGE` 호출 구조를 캐스팅 하는 방법을 보여 주는 메시지입니다.  
  
```cpp#  
LONG SendStatusMessage(  
    LPTEXTOUTPROC pTextOutProc,  
    DWORD         dwBackgroundID,  
    LPCTSTR       pStatusMsg,  
    BOOL          bIsError)  
{  
    SccMsgDataOnMessage msgData = { 0 };  
    LONG                result  = 0;  
  
    msgData.dwBackgroundOperationID = dwBackgroundID;  
    msgData.szMessage               = pStatusMsg;  
    msgData.bIsError                = bIsError;  
  
    result = pTextOutProc(reinterpret_cast<LPCTSTR>(&msgData), SCC_MSG_BACKGROUND_ON_MESSAGE);  
    return result;  
}  
```  
  
## <a name="see-also"></a>참고 항목  
 [IDE에 의해 구현 된 콜백 함수](../extensibility/callback-functions-implemented-by-the-ide.md)   
 [소스 제어 플러그 인](../extensibility/source-control-plug-ins.md)
