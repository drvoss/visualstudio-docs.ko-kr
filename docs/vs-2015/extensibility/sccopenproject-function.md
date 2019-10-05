---
title: SccOpenProject 함수 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- SccOpenProject
helpviewer_keywords:
- SccOpenProject function
ms.assetid: d609510b-660a-46d7-b93d-2406df20434d
caps.latest.revision: 17
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: af2b33d31d813533d833e4a5c15a3b562bc2e94e
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63446795"
---
# <a name="sccopenproject-function"></a>SccOpenProject 함수
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

이 함수 기존 소스 제어 프로젝트를 열거나 새로 만듭니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
SCCRTN SccOpenProject (  
   LPVOID        pvContext,  
   HWND          hWnd,  
   LPSTR         lpUser,  
   LPCSTR        lpProjName,  
   LPCSTR        lpLocalProjPath,  
   LPSTR         lpAuxProjPath,  
   LPCSTR        lpComment,  
   LPTEXTOUTPROC lpTextOutProc,  
   LONG          dwFlags  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 pvContext  
 [in] 원본 제어 플러그 인 상황에 맞는 구조입니다.  
  
 hWnd  
 [in] 소스 제어 플러그 인을 제공 하는 모든 대화 상자에 대 한 부모로 사용할 수 있는 IDE 창 핸들입니다.  
  
 lpUser  
 [out에서] \(NULL 종결자를 포함 하 여 SCC_USER_SIZE 초과 하지 않음) 하는 사용자의 이름입니다.  
  
 lpProjName  
 [in] 프로젝트의 이름을 나타내는 문자열입니다.  
  
 lpLocalProjPath  
 [in] 프로젝트에 대 한 작업 폴더 경로입니다.  
  
 lpAuxProjPath  
 [out에서] 프로젝트 (NULL 종결자를 포함 하 여 SCC_AUXPATH_SIZE, 초과 하지 않음)를 식별 하는 선택적 보조 문자열입니다.  
  
 lpComment  
 [in] 생성 되는 새 프로젝트에 주석을 추가 합니다.  
  
 lpTextOutProc  
 [in] 소스 제어 플러그 인에서 출력 텍스트를 표시 하는 선택적 콜백 함수입니다.  
  
 dwFlags  
 [in] 신호 새 프로젝트를 프로젝트에 소스를 알 수 없는 경우 생성 해야 하는지 여부를 제어 플러그 인입니다. 값의 조합일 수 있습니다 `SCC_OP_CREATEIFNEW` 및 `SCC_OP_SILENTOPEN.`  
  
## <a name="return-value"></a>반환 값  
 원본 제어 플러그 인이 함수의 구현은 다음 값 중 하나를 반환 하:  
  
|값|설명|  
|-----------|-----------------|  
|SCC_OK|프로젝트를 열고에 성공 했습니다.|  
|SCC_E_INITIALIZEFAILED|프로젝트를 초기화할 수 없습니다.|  
|SCC_E_INVALIDUSER|사용자 소스 제어 시스템에 로그인 하지 못했습니다.|  
|SCC_E_COULDNOTCREATEPROJECT|프로젝트를 호출 하기 전에 없었습니다.  `SCC_OPT_CREATEIFNEW` 플래그가 설정 되었지만 프로젝트를 만들 수 없습니다.|  
|SCC_E_PROJSYNTAXERR|잘못 된 프로젝트 구문입니다.|  
|SCC_E_UNKNOWNPROJECT|프로젝트 소스 제어 플러그 인을 알 수 없는 및 `SCC_OPT_CREATEIFNEW` 플래그가 설정 되지 않았습니다.|  
|SCC_E_INVALIDFILEPATH|잘못 되었거나 사용할 수 없는 파일 경로입니다.|  
|SCC_E_NOTAUTHORIZED|사용자는이 작업을 수행할 수 없습니다.|  
|SCC_E_ACCESSFAILURE|소스 제어 시스템에 경합 또는 네트워크 문제로 인해 액세스 문제가 있습니다. 재시도 사용 하는 것이 좋습니다.|  
|SCC_E_NONSPECFICERROR|일반 오류입니다. 소스 제어 시스템을 초기화 되지 않았습니다.|  
  
## <a name="remarks"></a>설명  
 IDE 사용자 이름에 전달할 수 있습니다 (`lpUser`)에 있고 단순히 빈 문자열에 대 한 포인터에서 전달할 수 있습니다. 없는 경우 사용자 이름, 소스 제어 플러그 인을 기본값으로 사용 해야 합니다. 그러나 이름이 전달 되지 않은, 또는 지정 된 이름의 로그인에 실패 하는 경우 플러그 인 사용자가 로그인 메시지를 표시 및에서 유효한 이름을 반환 하는 `lpUser` 유효한 로그인을 받을 때`.` 플러그 인는 사용자 이름 문자열을 변경 될 수 있으므로 에서 IDE를 항상 크기의 버퍼를 할당 (`SCC_USER_LEN`+ 1 또는 null 종결자를 위한 공간이 포함 된 SCC_USER_SIZE).  
  
> [!NOTE]
> IDE는 수행 해야 할 수 있습니다 첫 번째 작업에 대 한 호출 수를 `SccOpenProject` 함수 또는 [SccGetProjPath](../extensibility/sccgetprojpath-function.md)합니다. 이러한 이유로 둘 다가 동일한 `lpUser` 매개 변수입니다.  
  
 `lpAuxProjPath` 및`lpProjName` 솔루션 파일에서 읽는 호출에서 반환 되는 또는 `SccGetProjPath` 함수입니다. 이러한 매개 변수는 소스 제어 플러그 인을 프로젝트와 연결 하는 문자열을 포함 및 플러그 인에 의미 합니다. 해당 문자열이 없거나 솔루션 파일에 있고 사용자가 이동할 묻지 (통해 문자열을 반환 하는 것은 `SccGetProjPath` 함수)를 둘 다에 대해 빈 문자열을 전달 하는 IDE `lpAuxProjPath` 및 `lpProjName`, 하며 이러한 값을 업데이트할 수 이 함수에서 플러그 인 경우 다음을 반환합니다.  
  
 `lpTextOutProc` 명령 결과 출력을 표시 하기 위해 플러그 인 소스 제어에는 IDE에서 제공 하는 콜백 함수에 포인터가입니다. 이 콜백 함수에서 자세히 설명 되어 [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)합니다.  
  
> [!NOTE]
> 소스 제어 플러그 인이 활용 하는, 하는 경우 설정 있어야 합니다는 `SCC_CAP_TEXTOUT` 플래그를 [SccInitialize](../extensibility/sccinitialize-function.md)합니다. IDE는이 기능을 지원 하지 않는 경우 또는 해당 플래그가 설정 되지 않은 경우 `lpTextOutProc` 됩니다 `NULL`합니다.  
  
 `dwFlags` 매개 변수는 열려 있는 프로젝트가 현재 없습니다 결과 제어 합니다. 두 비트 이루어져 `SCC_OP_CREATEIFNEW` 고 `SCC_OP_SILENTOPEN`입니다. 이미 열려 있는 프로젝트가 있는 경우 간단히 프로젝트가 열립니다 함수와 반환 `SCC_OK`합니다. 프로젝트가 존재 하지 않는 경우는 `SCC_OP_CREATEIFNEW` 플래그에는, 소스 제어 플러그 인 수 소스 제어 시스템에서 프로젝트 만들기, 열 및 반환 `SCC_OK`합니다. 프로젝트가 없는 경우는 `SCC_OP_CREATEIFNEW` 플래그를 해제 하면 플러그 인은 확인 한 후의 `SCC_OP_SILENTOPEN` 플래그입니다. 플래그를 없는 경우에 플러그 인 넣으라는 메시지를 프로젝트 이름에 대 한 사용자. 해당 플래그가 켜져 있는지, 플러그 인을 반환 하면 `SCC_E_UNKNOWNPROJECT`합니다.  
  
## <a name="calling-order"></a>호출 순서  
 이벤트의 정상적인 합니다 [SccInitialize](../extensibility/sccinitialize-function.md) 원본 제어 세션을 열려면 먼저 호출 됩니다. 세션 구성에 대 한 호출 될 수 있습니다 `SccOpenProject`뒤에 다른 원본 제어 플러그 인 API 함수 호출이 고 호출 하 여 종료 됩니다 합니다 [SccCloseProject](../extensibility/scccloseproject-function.md)합니다. 이러한 세션을 여러 번 반복 될 수 있습니다 합니다 [SccUninitialize](../extensibility/sccuninitialize-function.md) 라고 합니다.  
  
 원본 제어 플러그 인 설정 하는 경우는 `SCC_CAP_REENTRANT` 비트 `SccInitialize`, 다음 위의 세션 순서 동시에 여러 번 반복 될 수 있습니다. 다른 `pvContext` 구조에 다른 세션에서 각 추적 `pvContext` 은 한 번에 하나의 프로젝트 열기를 사용 하 여 연결 합니다. 에 따라는`pvContext` 매개 변수를 플러그 인 확인할 수는 프로젝트는 특정 호출에서 참조 됩니다. 기능 비트 경우 `SCC_CAP_REENTRANT` 을 설정 하지 않으면 nonreentrant 원본 제어 플러그 인 프로젝트를 사용 하는 기능이 제한 됩니다.  
  
> [!NOTE]
> `SCC_CAP_REENTRANT` 비트 원본 제어 플러그 인 API의 버전 1.1에서에서 도입 되었습니다. 이 설정 되어 있지 않거나 버전 1.0에서는 무시 됩니다 및 모든 버전 1.0 원본 제어 플러그 인 nonreentrant 것으로 간주 됩니다.  
  
## <a name="see-also"></a>참고 항목  
 [원본 제어 플러그 인 API 함수](../extensibility/source-control-plug-in-api-functions.md)   
 [SccCloseProject](../extensibility/scccloseproject-function.md)   
 [SccGetProjPath](../extensibility/sccgetprojpath-function.md)   
 [SccInitialize](../extensibility/sccinitialize-function.md)   
 [SccUninitialize](../extensibility/sccuninitialize-function.md)   
 [문자열 길이 제한](../extensibility/restrictions-on-string-lengths.md)   
 [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)
