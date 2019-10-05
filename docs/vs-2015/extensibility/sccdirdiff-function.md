---
title: SccDirDiff 함수 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- SccDirDiff
helpviewer_keywords:
- SccDirDiff function
ms.assetid: 26c9ba92-e3b9-4dd2-bd5e-76b17745e308
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 81279e0fdb0df6600686adc57bb1c5489e8e7aab
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63432452"
---
# <a name="sccdirdiff-function"></a>SccDirDiff 함수
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

이 함수는 클라이언트 디스크에서 현재 로컬 디렉터리와 해당 소스 제어 프로젝트 간의 차이점을 표시합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
SCCRTN SccDirDiff(  
   LPVOID    pContext,  
   HWND      hWnd,  
   LPCSTR    lpDirName,  
   LONG      dwFlags,  
   LPCMDOPTS pvOptions  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 pContext  
 [in] 원본 제어 플러그 인 상황에 맞는 구조입니다.  
  
 hWnd  
 [in] 소스 제어 플러그 인을 제공 하는 모든 대화 상자에 대 한 부모로 사용할 수 있는 IDE 창 핸들입니다.  
  
 lpDirName  
 [in] Visual 차이 표시 하는 로컬 디렉터리에 정규화 된 경로입니다.  
  
 dwFlags  
 [in] 명령 플래그 (주의 참조 섹션).  
  
 pvOptions  
 [in] 원본 제어 플러그 인에 대 한 옵션입니다.  
  
## <a name="return-value"></a>반환 값  
 원본 제어 플러그 인이 함수의 구현은 다음 값 중 하나를 반환 하:  
  
|값|설명|  
|-----------|-----------------|  
|SCC_OK|디스크에 있는 디렉터리에서 소스 코드 제어 프로젝트와 같습니다.|  
|SCC_I_FILESDIFFER|디스크에 있는 디렉터리에서 소스 코드 제어 프로젝트와 다릅니다.|  
|SCC_I_RELOADFILE|파일 또는 프로젝트 다시 로드 해야 합니다.|  
|SCC_E_FILENOTCONTROLLED|디렉터리를 소스 코드 제어 아닙니다.|  
|SCC_E_NOTAUTHORIZED|사용자는이 작업을 수행할 수 없습니다.|  
|SCC_E_ACCESSFAILURE|소스 제어 시스템에 경합 또는 네트워크 문제로 인해 액세스 문제가 있습니다. 재시도 사용 하는 것이 좋습니다.|  
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|알 수 없는 오류가 발생 했습니다.|  
|SCC_E_FILENOTEXIST|로컬 디렉터리를 찾을 수 없습니다.|  
  
## <a name="remarks"></a>설명  
 이 함수는 소스 제어 플러그 인 지정된 된 디렉터리 변경 내용 목록을 사용자에 게 표시 하도록 지시 하려면 사용 됩니다. 플러그 인 자체 창에서 디스크에 대 한 사용자의 디렉터리와 해당 프로젝트를 버전 제어의 차이점을 표시 하려면 선택한 형식으로 열립니다.  
  
 경우에 모든 디렉터리의 플러그 인에서 지 원하는 반면 "빠른 diff" 옵션을 지원 하지 않는 경우에 디렉터리의 비교 파일 이름으로 지원 해야 합니다.  
  
|`dwFlags`|해석|  
|---------------|--------------------|  
|SCC_DIFF_IGNORECASE|대/소문자 비교 (빠른 diff 또는 시각적 개체에 대해 사용할 수 있음).|  
|SCC_DIFF_IGNORESPACE|공백 (빠른 diff 또는 시각적 개체에 대해 사용할 수 있음)를 무시 합니다.|  
|SCC_DIFF_QD_CONTENTS|소스 제어 플러그 인에서 지 원하는, 자동으로 디렉터리를 바이트 단위로 비교 합니다.|  
|SCC_DIFF_QD_CHECKSUM|플러그 인에서 지 원하는, 자동으로 체크섬을 통해 디렉터리를 비교 하거나, 지원 되지 않는 경우 SCC_DIFF_QD_CONTENTS로 대체 합니다.|  
|SCC_DIFF_QD_TIME|플러그 인에서 지 원하는, 자동으로 해당 타임 스탬프를 통해 디렉터리를 비교 하거나, 지원 되지 않는 경우 SCC_DIFF_QD_CHECKSUM 또는 SCC_DIFF_QD_CONTENTS 대체 합니다.|  
  
> [!NOTE]
> 이 함수는 동일한 명령 플래그를 사용 합니다 [SccDiff](../extensibility/sccdiff-function.md)합니다. 그러나 원본 제어 플러그 인을 디렉터리에 대 한 "빠른 diff" 작업을 지원 하지 않도록 수도 있습니다.  
  
## <a name="see-also"></a>참고 항목  
 [소스 제어 플러그 인 API 함수](../extensibility/source-control-plug-in-api-functions.md)
