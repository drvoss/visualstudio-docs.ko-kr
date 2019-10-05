---
title: SccGet 함수 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- SccGet
helpviewer_keywords:
- SccGet function
ms.assetid: 09a18bd2-b788-411a-9da6-067d806e46f6
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2a5d5065ca427f0319174aa59e6b87d356816d4c
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63432426"
---
# <a name="sccget-function"></a>SccGet 함수
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

이 함수는 하나 이상의 파일 보기 및 컴파일하기 위한 아니라 편집의 복사본을 검색 합니다. 대부분의 시스템에서 파일 읽기 전용으로 태그가 지정 됩니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
SCCRTN SccGet(  
   LPVOID    pvContext,  
   HWND      hWnd,  
   LONG      nFiles,  
   LPCSTR*   lpFileNames,  
   LONG      fOptions,  
   LPCMDOPTS pvOptions  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 pvContext  
 [in] 상황에 맞는 구조는 소스 제어 플러그 인입니다.  
  
 hWnd  
 [in] 소스 제어 플러그 인을 제공 하는 모든 대화 상자에 대 한 부모로 사용할 수 있는 IDE 창 핸들입니다.  
  
 nFiles  
 [in] 에 지정 된 파일 수는 `lpFileNames` 배열입니다.  
  
 lpFileNames  
 [in] 검색할 파일의 정규화 된 이름의 배열입니다.  
  
 fOptions  
 [in] 명령 플래그 (`SCC_GET_ALL`, `SCC_GET_RECURSIVE`).  
  
 pvOptions  
 [in] 원본 제어 플러그 인에 대 한 옵션입니다.  
  
## <a name="return-value"></a>반환 값  
 원본 제어 플러그 인이 함수의 구현은 다음 값 중 하나를 반환 하:  
  
|값|설명|  
|-----------|-----------------|  
|SCC_OK|가져오기 작업의 성공 했습니다.|  
|SCC_E_FILENOTCONTROLLED|소스 제어를 파일이 없습니다.|  
|SCC_E_OPNOTSUPPORTED|소스 제어 시스템에서이 작업을 지원 하지 않습니다.|  
|SCC_E_FILEISCHECKEDOUT|사용자 현재 체크 아웃 된 파일을 가져올 수 없습니다.|  
|SCC_E_ACCESSFAILURE|소스 제어 시스템에 경합 또는 네트워크 문제로 인해 액세스 문제가 있습니다. 재시도 사용 하는 것이 좋습니다.|  
|SCC_E_NOSPECIFIEDVERSION|에 잘못 된 버전 또는 날짜/시간을 지정 합니다.|  
|SCC_E_NONSPECIFICERROR|일반 오류입니다. 파일 동기화 되지 않았습니다.|  
|SCC_I_OPERATIONCANCELED|작업이 완료 되기 전에 취소 되었습니다.|  
|SCC_E_NOTAUTHORIZED|사용자는이 작업을 수행할 수 있는 권한이 없습니다.|  
  
## <a name="remarks"></a>설명  
 이 함수는 수 고를 검색할 파일의 이름 배열을 사용 하 여 호출 됩니다. IDE 플래그를 전달 하는 경우 `SCC_GET_ALL`, 즉, 항목 `lpFileNames` 파일이 아니라 디렉터리 및 지정 된 디렉터리에서 소스 제어 아래 모든 파일이 검색 됩니다.  
  
 `SCC_GET_ALL` 플래그를 사용 하 여 결합할 수는 `SCC_GET_RECURSIVE` 플래그를 지정 된 디렉터리의 모든 파일 및 모든 하위 디렉터리도 검색 합니다.  
  
> [!NOTE]
> `SCC_GET_RECURSIVE` 없이 전달 되지 해야 `SCC_GET_ALL`합니다. 또한는 C:\A\B 및 C:\A 디렉터리 재귀 전달 모두 가져올 경우 C:\A\B 및 모든 하위 디렉터리는 실제로 검색할 두 번 note 합니다. IDE의 책임-인 원본이 아닌 제어 및-같이 중복 하는 배열에서 유지 되도록 합니다.  
  
 소스 제어 플러그 인 경우에 지정 하는 마지막으로 `SCC_CAP_GET_NOUI` 초기화 없기 Get 명령에 대 한 사용자 인터페이스에이 함수는 파일을 검색 하려면 IDE에서 여전히 호출할 수 있습니다를 나타내는 플래그입니다. 플래그는 단순히 IDE 가져오기 메뉴 항목을 표시 하지 않습니다 하 고 UI를 제공 해야 플러그 인 아님을 의미 합니다.  
  
## <a name="renaming-and-sccget"></a>이름 바꾸기 및 SccGet  
 상황: 사용자, 예를 들어 a.txt 파일을 체크 아웃 및 수정 합니다. A.txt 확인할 수 있습니다, 전에 두 번째 사용자 a.txt 소스 제어 데이터베이스에서 b.txt로 바꿉니다, 그리고 b.txt 확인, 일부 파일을 수정 하면 및 파일을 검사 합니다. 첫 번째 사용자가 첫 번째 사용자 b.txt a.txt 파일의 로컬 버전에 해당 이름을 바꾼 파일에 get 않습니다 있도록 두 번째 사용자가 수행한 변경 합니다. 그러나 버전 번호를 추적 하는 로컬 캐시 것으로 생각 a.txt의 첫 번째 버전 로컬로 저장 되 고 소스 제어 차이 확인할 수 없습니다.  
  
 두 가지 방법으로 원본 제어 버전의 로컬 캐시는 원본 제어 데이터베이스와 동기화 되는이 상황을 해결 하기.  
  
1. 현재 체크 아웃 원본 제어 데이터베이스에서 파일 이름을 바꿀 수 없습니다.  
  
2. "이전"삭제 "새로 추가" 뒤에 해당 하는를 수행 합니다. 다음 알고리즘은이 작업을 수행 하는 하나의 방법입니다.  
  
    1. 호출 된 [SccQueryChanges](../extensibility/sccquerychanges-function.md) a.txt 소스 제어 데이터베이스에서 b.txt로 이름 바꾸기에 대 한 자세한 함수입니다.  
  
    2. 로컬 a.txt를 이름을 b.txt로 바꿉니다.  
  
    3. 호출 된 `SccGet` a.txt와 b.txt 함수입니다.  
  
    4. 소스 제어 데이터베이스에 있는 a.txt 없으므로 로컬 버전 캐시 누락 된 a.txt 버전 정보의 제거 됩니다.  
  
    5. B.txt 파일을 체크 아웃 되는 로컬 b.txt 파일의 내용으로 병합 됩니다.  
  
    6. 이제 업데이트 된 b.txt 파일을 확인할 수 있습니다.  
  
## <a name="see-also"></a>참고 항목  
 [원본 제어 플러그 인 API 함수](../extensibility/source-control-plug-in-api-functions.md)   
 [특정 명령에 사용되는 Bitflag](../extensibility/bitflags-used-by-specific-commands.md)
