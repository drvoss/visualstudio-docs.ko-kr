---
title: SccGetProjPath 함수 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- SccGetProjPath
helpviewer_keywords:
- SccGetProjPath function
ms.assetid: 1079847e-d45f-4cb8-9d92-1e01ce5d08f6
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 585402efbda165844f449e2477d5ca69722613a8
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63446869"
---
# <a name="sccgetprojpath-function"></a>SccGetProjPath 함수
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

이 함수는 프로젝트 경로 소스 제어 플러그 인에 의미 있는 문자열에 대 한 라는 메시지입니다. 사용자가 있는 경우 라고 합니다.  
  
- 새 프로젝트 만들기  
  
- 버전 제어에 기존 프로젝트 추가  
  
- 기존 버전 제어 프로젝트를 찾으려고 시도  
  
## <a name="syntax"></a>구문  
  
```cpp#  
SCCRTN SccGetProjPath (  
   LPVOID pvContext,  
   HWND   hWnd,  
   LPSTR  lpUser,  
   LPSTR  lpProjName,  
   LPSTR  lpLocalPath,  
   LPSTR  lpAuxProjPath,  
   BOOL   bAllowChangePath,  
   LPBOOL pbNew  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 pvContext  
 [in] 원본 제어 플러그 인 상황에 맞는 구조입니다.  
  
 hWnd  
 [in] 소스 제어 플러그 인을 제공 하는 모든 대화 상자에 대 한 부모로 사용할 수 있는 IDE 창 핸들입니다.  
  
 lpUser  
 [out에서] 사용자 이름 (NULL 종결자를 포함 하 여 SCC_USER_SIZE, 초과 하지 않음)  
  
 lpProjName  
 [out에서] IDE 프로젝트, 프로젝트 작업 영역 또는 메이크파일 (NULL 종결자를 포함 하 여 SCC_PRJPATH_SIZE, 초과 하지 않음)의 이름입니다.  
  
 lpLocalPath  
 [out에서] 프로젝트의 작업 경로입니다. 하는 경우 `bAllowChangePath` 는 `TRUE`, 소스 제어 플러그 인 (_max_path(256, null 종결자를 포함 하 여 초과 하지 않음)이이 문자열을 수정할 수 있습니다.  
  
 lpAuxProjPath  
 [out에서] 반환 된 프로젝트 경로 (NULL 종결자를 포함 하 여 SCC_PRJPATH_SIZE, 초과 하지 않음)에 대 한 버퍼입니다.  
  
 bAllowChangePath  
 [in] 이것이 `TRUE`, 소스 제어 플러그 인에 대 한 메시지를 표시 하 고 수정할 수는 `lpLocalPath` 문자열입니다.  
  
 pbNew  
 [out에서] 들어오는 값 새 프로젝트를 만들지 여부를 나타냅니다. 반환 된 값에는 프로젝트를 만들기의 성공을 나타냅니다.  
  
|들어오는|해석|  
|--------------|--------------------|  
|TRUE|사용자는 새 프로젝트를 만들 수 있습니다.|  
|FALSE|사용자는 새 프로젝트를 만들 수 없습니다.|  
  
|나가는 포트|해석|  
|--------------|--------------------|  
|TRUE|새 프로젝트를 만들었습니다.|  
|FALSE|기존 프로젝트를 선택 했습니다.|  
  
## <a name="return-value"></a>반환 값  
 원본 제어 플러그 인이 함수의 구현은 다음 값 중 하나를 반환 하:  
  
|값|설명|  
|-----------|-----------------|  
|SCC_OK|성공적으로 프로젝트를 만들거나 검색 됩니다.|  
|SCC_I_OPERATIONCANCELED|작업이 취소 되었습니다.|  
|SCC_E_ACCESSFAILURE|소스 제어 시스템에 경합 또는 네트워크 문제로 인해 액세스 문제가 있습니다.|  
|SCC_E_CONNECTIONFAILURE|소스 제어 시스템에 연결 하려는 중 오류가 발생 했습니다.|  
|SCC_E_NONSPECIFICERROR|지정되지 않은 오류가 발생했습니다.|  
  
## <a name="remarks"></a>설명  
 매개 변수를 획득 하기 위해 IDE에 대 한이 함수의 목적은 `lpProjName` 고 `lpAuxProjPath`입니다. 이 정보에 대 한 라는 메시지를 표시 하는 소스 제어 플러그 인, 후 두 문자열이 IDE에 다시 전달 합니다. IDE의 솔루션 파일에 이러한 문자열을 지속 하 고 전달 하도록 합니다 [SccOpenProject](../extensibility/sccopenproject-function.md) 사용자가이 프로젝트를 열 때마다 합니다. 이러한 문자열을 프로젝트와 관련 된 정보를 추적 플러그 인을 사용 합니다.  
  
 함수가 먼저 호출 되 면 `lpAuxProjPath` 빈 문자열로 설정 됩니다. `lProjName` 비어 있을 수도 소스 제어 플러그 인 사용 하거나 무시할 수 있는 IDE 프로젝트 이름을 포함할 수 있습니다. 함수는 성공적으로 반환 될 때 해당 문자열을 두 개의 플러그 인 반환 합니다. IDE 이러한 문자열에 대 한 가정 하지 않고,을 사용 하지 않으며 사용자가 수정할 수 없습니다. 사용자가 설정을 변경 하려는 경우 IDE는 호출 `SccGetProjPath` 마찬가지로 동일한 값에서 전달 받은 이전 시간입니다. 이 두 문자열이 완전히 플러그 인 제어를 제공합니다.  
  
 에 대 한 `lpUser`, IDE 사용자 이름에 전달할 수 있습니다 또는 빈 문자열에 대 한 포인터에서 단순히 통과할 수 있습니다. 없는 경우 사용자 이름, 소스 제어 플러그 인을 기본값으로 사용 해야 합니다. 그러나 이름이 전달 되지 않은 경우, 지정 된 이름의 로그인에 실패 하는 경우 플러그 인 메시지를 표시할 로그인 하 고 이름을 다시 전달 `lpUser` 유효한 로그인을 받을 때입니다. IDE는 크기의 버퍼를 할당 항상 플러그 인이 문자열 변경 될 수, 있으므로 (`SCC_USER_LEN`+ 1).  
  
> [!NOTE]
> IDE에서 수행 하는 첫 번째 작업 중 하나에 대 한 호출 수를 `SccOpenProject` 함수 또는 `SccGetProjPath` 함수입니다. 따라서 둘 다가 동일한 `lpUser` 소스 제어 플러그 인을 두 번에 사용자를 로그인을 사용 하도록 설정 하는 매개 변수입니다. 함수에서 반환 된 값을 실패를 나타내는 경우에 플러그 인 채워야 유효한 로그인 이름의이 문자열입니다.  
  
 `lpLocalPath` 여기서 사용자가 프로젝트 디렉터리가입니다. 빈 문자열일 수 있습니다. 디렉터리가 없습니다 (의 경우와 같이 소스 제어 시스템에서 프로젝트를 다운로드 하는 동안 사용자) 현재 정의 된 경우 `bAllowChangePath` 는 `TRUE`, 소스 제어 플러그 인 입력에 대 한 사용자 수 또는 일부 다른 메서드를 사용 하 여 배치 해당 문자열을 소유 `lpLocalPath`합니다. 하는 경우 `bAllowChangePath` 는 `FALSE`, 플러그 인은 문자열 때문에 변경할 사용자가 이미 지정된 된 디렉터리에서 작업 합니다.  
  
 사용자 소스 제어에서 삽입할 새 프로젝트를 만드는 경우 원본 제어 플러그 인 만들지 못할 수도 있습니다 실제로 해당 소스 제어 시스템에 시 `SccGetProjPath` 라고 합니다. 대신, 전달 다시 0이 아닌 값을 사용 하 여 함께 문자열 `pbNew`, 소스 제어 시스템에서 프로젝트를 만들 수를 나타내는입니다.  
  
 예를 들어, 사용자는 **새 프로젝트** Visual Studio에서 마법사가 자신의 프로젝트를 소스 제어에 추가 하 고이 함수를 호출 하는 Visual Studio 플러그 인에 소스 제어 시스템에서 새 프로젝트를 만들 수 있는지 결정 Visual Studio 프로젝트를 포함 합니다. 클릭 하면 **취소** 마법사를 완료 하기 전에 프로젝트 만들어지지 않습니다. 클릭 하면 **확인**를 호출 하는 Visual Studio `SccOpenProject`전달 `SCC_OPT_CREATEIFNEW`, 소스 제어 프로젝트는 해당 시점에 생성 됩니다.  
  
## <a name="see-also"></a>참고 항목  
 [원본 제어 플러그 인 API 함수](../extensibility/source-control-plug-in-api-functions.md)   
 [SccOpenProject](../extensibility/sccopenproject-function.md)
