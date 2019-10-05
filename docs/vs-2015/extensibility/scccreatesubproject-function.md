---
title: SccCreateSubProject 함수 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- SccCreateSubProject
helpviewer_keywords:
- SccCreateSubProject function
ms.assetid: 08154aed-ae5c-463c-8694-745d0e332965
caps.latest.revision: 20
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c2f28d8bb9ebc440db69085324becb6a96c19afe
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68200198"
---
# <a name="scccreatesubproject-function"></a>SccCreateSubProject 함수
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

이 함수는 지정 된 기존 부모 프로젝트에서 지정 된 이름의 하위 프로젝트를 만듭니다는 `lpParentProjPath` 인수입니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
SCCRTN SccCreateSubProject(  
   LPVOID pContext,  
   HWND   hWnd,  
   LPSTR  lpUser,  
   LPCSTR lpParentProjPath,  
   LPCSTR lpSubProjName,  
   LPSTR  lpAuxProjPath,  
   LPSTR  lpSubProjPath  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 pContext  
 [in] 원본 제어 플러그 인 컨텍스트 포인터입니다.  
  
 hWnd  
 [in] 소스 제어 플러그 인을 제공 하는 모든 대화 상자에 대 한 부모로 사용할 수 있는 IDE 창 핸들입니다.  
  
 lpUser  
 [out에서] (최대 SCC_USER_SIZE NULL 종결자를 포함 하 여) 사용자 이름입니다.  
  
 lpParentProjPath  
 [in] 부모 프로젝트 (최대 SCC_PRJPATH_SIZE NULL 종결자 포함)의 경로 식별 하는 문자열입니다.  
  
 lpSubProjName  
 [in] SCC_PRJPATH_SIZE NULL 종결자 포함) (최대 제안 된 하위 프로젝트 이름입니다.  
  
 lpAuxProjPath  
 [out에서] (최대 SCC_PRJPATH_SIZE NULL 종결자 포함) 프로젝트를 식별 하는 보조 문자열입니다.  
  
 lpSubProjPath  
 [out에서] \(최대 SCC_PRJPATH_SIZE NULL 종결자 포함)의 하위 경로 식별 하는 출력 문자열입니다.  
  
## <a name="return-value"></a>반환 값  
 원본 제어 플러그 인이 함수의 구현은 다음 값 중 하나를 반환 하:  
  
|값|Description|  
|-----------|-----------------|  
|SCC_OK|하위 프로젝트를 만들었습니다.|  
|SCC_E_INITIALIZEFAILED|부모 프로젝트를 초기화할 수 없습니다.|  
|SCC_E_INVALIDUSER|사용자 소스 제어 시스템에 로그인 하지 못했습니다.|  
|SCC_E_COULDNOTCREATEPROJECT|하위 프로젝트를 만들 수 없습니다.|  
|SCC_E_PROJSYNTAXERR|잘못 된 프로젝트 구문입니다.|  
|SCC_E_UNKNOWNPROJECT|부모 프로젝트 소스 제어 플러그 인에 인식 되지 않습니다.|  
|SCC_E_INVALIDFILEPATH|잘못 되었거나 사용할 수 없는 파일 경로입니다.|  
|SCC_E_NOTAUTHORIZED|사용자는이 작업을 수행할 수 없습니다.|  
|SCC_E_ACCESSFAILURE|소스 제어 시스템에 경합 또는 네트워크 문제로 인해 액세스 문제가 있습니다. 재시도 사용 하는 것이 좋습니다.|  
|SCC_E_CONNECTIONFAILURE|원본 제어 플러그 인 연결에 문제가 있었습니다.|  
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|알 수 없는 오류가 발생 했습니다.|  
  
## <a name="remarks"></a>설명  
 함수를 추가 하 여 고유한 대시보드를 만든 기본 이름을 변경할 수 이름의 하위 프로젝트가 이미 있는 경우 "_\<번호 >"를 합니다. 호출자에 변경 사항을 적용 하도록 준비 해야 `lpUser`, `lpSubProjPath`, 및 `lpAuxProjPath`합니다. `lpSubProjPath` 하 고`lpAuxProjPath` 인수에 대 한 호출에 사용 됩니다 합니다 [SccOpenProject](../extensibility/sccopenproject-function.md)합니다. 반환 시 호출자가 되지 수정 해야 합니다. 이러한 문자열 소스 제어 플러그 인을 프로젝트와 연결 하는 데 필요한 정보를 추적 하는 방법을 제공 합니다. 호출자에 게 IDE 플러그 인 보기에 적합 하지 않을 수 있는 서식이 지정 된 문자열을 사용할 수 있으므로 반환 될 때이 두 매개 변수를 표시 하지 않습니다. 함수 성공 또는 실패 코드를 반환 하 고, 성공 하면 변수를 채웁니다 `lpSubProjPath` 새 프로젝트에 전체 프로젝트 경로 사용 하 여 합니다.  
  
 이 함수는 비슷합니다는 [SccGetProjPath](../extensibility/sccgetprojpath-function.md)하나를 선택 하 라는 메시지 하는 것이 아니라 프로젝트를 자동으로 생성 한다는 점을 제외 하면, 합니다. 경우는 `SccCreateSubProject` 함수를 호출 `lpParentProjName` 및 `lpAuxProjPath` 빈 되지 않으며 유효한 프로젝트에 해당 됩니다. 이러한 문자열은 일반적으로 IDE에 대 한 이전 호출에서 받은 합니다 `SccGetProjPath` 함수 또는 [SccGetParentProjectPath](../extensibility/sccgetparentprojectpath-function.md)합니다.  
  
 `lpUser` 인수는 사용자 이름입니다. IDE에서 이전에 수신한 동일한 사용자 이름을 전달 `SccGetProjPath`, 소스 제어 플러그 인 기본 이름을 사용 해야 합니다. 사용자에 게 이미 플러그 인을 사용 하 여 연결 된 경우 다음 플러그 인 하려고 해야 함수를 자동으로 작동 하는지 확인 하 라는 메시지가 표시를 제거 합니다. 그러나 로그인이 실패 하는 경우 플러그 인에서 메시지를 표시 사용자가 로그인 하 고, 올바른 로그인 이름을 다시 전달 받으면 `lpUser`합니다. IDE는 버퍼를 할당 항상 바뀌므로 플러그 인이 문자열을 크기 조정 (SCC_USER_LEN + 1 또는 null 종결자를 위한 공간이 포함 된 SCC_USER_SIZE). 문자열 변경 되 면 새 문자열 (적어도 이전 문자열 유효) 유효한 로그인 이름 이어야 합니다.  
  
## <a name="technical-notes-for-scccreatesubproject-and-sccgetparentprojectpath"></a>SccCreateSubProject 및 SccGetParentProjectPath 기술 참고 사항  
 소스 제어에 솔루션 및 프로젝트를 추가할 수 있는 사용자는 소스 제어 시스템에서 위치를 선택 하 라는 메시지가 표시 되는 횟수를 최소화 하기 위해 Visual Studio에서 간소화 되었습니다. 소스 제어 플러그 인을 지 원하는 새 기능을 모두 경우 이러한 변경 내용은 Visual Studio로 활성화 되 `SccCreateSubProject` 고 `SccGetParentProjectPath`입니다. 그러나 이러한 변경 내용을 사용 하지 않도록 설정 하 여 이전 Visual Studio (소스 제어 플러그 인 API 버전 1.1) 동작으로 되돌리려면 다음 레지스트리 항목을 사용할 수 있습니다.  
  
 [HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl] "DoNotCreateSolutionRootFolderInSourceControl"=dword:00000001  
  
 이 레지스트리 항목이 존재 하지 않거나 dword:00000000은로 설정 되어, 새 함수를 사용 하 여 Visual Studio 시도 `SccCreateSubProject` 고 `SccGetParentProjectPath`입니다.  
  
 레지스트리 항목 dword:00000001으로 설정 된 경우 Visual Studio는 이러한 새 함수를 사용 하지 및 이전 버전의 Visual Studio에서와 마찬가지로 소스 제어에 추가 하는 작업에서 작동 합니다.  
  
## <a name="see-also"></a>참고 항목  
 [원본 제어 플러그 인 API 함수](../extensibility/source-control-plug-in-api-functions.md)   
 [SccGetParentProjectPath](../extensibility/sccgetparentprojectpath-function.md)   
 [SccGetProjPath](../extensibility/sccgetprojpath-function.md)
