---
title: SccDiff 함수 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- SccDiff
helpviewer_keywords:
- SccDiff function
ms.assetid: d49bc8c5-f631-4153-9d3c-feb3564da305
caps.latest.revision: 17
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: aa5ea0a269cdbfe678328dc652b4177bdc667b99
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63432473"
---
# <a name="sccdiff-function"></a>SccDiff 함수
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

이 함수 표시 (또는 확인만 필요한 경우)에서 차이점 (로컬 디스크)의 현재 파일 및 해당 마지막 체크 인 버전 원본 제어 시스템입니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
SCCRTN SccDiff(  
   LPVOID    pvContext,  
   HWND      hWnd,  
   LPCSTR    lpFileName,  
   LONG      fOptions,  
   LPCMDOPTS pvOptions  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 pvContext  
 [in] 원본 제어 플러그 인 상황에 맞는 구조입니다.  
  
 hWnd  
 [in] 소스 제어 플러그 인을 제공 하는 모든 대화 상자에 대 한 부모로 사용할 수 있는 IDE 창 핸들입니다.  
  
 lpFileName  
 [in] 차이 요청한 대상 파일 이름입니다.  
  
 fOptions  
 [in] 명령 플래그입니다. 세부 정보에 대 한 설명을 참조 하세요.  
  
 pvOptions  
 [in] 원본 제어 플러그 인에 대 한 옵션입니다.  
  
## <a name="return-value"></a>반환 값  
 원본 제어 플러그 인이 함수의 구현은 다음 값 중 하나를 반환 하:  
  
|값|설명|  
|-----------|-----------------|  
|SCC_OK|작업 복사 및 서버 버전은 동일 합니다.|  
|SCC_I_FILESDIFFERS|작업 복사본을 소스 제어에서 사용 중인 버전에서 서로 다릅니다.|  
|SCC_I_RELOADFILE|파일 또는 프로젝트 다시 로드 해야 합니다.|  
|SCC_E_FILENOTCONTROLLED|소스 제어를 파일이 없습니다.|  
|SCC_E_NOTAUTHORIZED|사용자는이 작업을 수행할 수 없습니다.|  
|SCC_E_ACCESSFAILURE|소스 제어 시스템에 경합 또는 네트워크 문제로 인해 액세스 문제가 있습니다. 재시도 사용 하는 것이 좋습니다.|  
|SCC_E_NONSPECIFICERROR|일반 오류입니다. 파일 차이 가져오지 못했습니다.|  
|SCC_E_FILENOTEXIST|로컬 파일을 찾을 수 없습니다.|  
  
## <a name="remarks"></a>설명  
 이 함수는 두 개의 다른 용도로 사용 됩니다. 기본적으로 파일에 변경 내용 목록을 표시 합니다. 소스 제어 플러그 인 형식에 관계 없이 디스크에 대 한 사용자의 파일 및 소스 제어에서 파일의 최신 버전의 차이점을 표시 하려면 선택에서 자체 창에서 열립니다.  
  
 또는 IDE 단순히 파일 변경 되었는지 여부를 확인 해야 합니다. 예를 들어, IDE는 파일을 체크 아웃 한 사용자에 게 알리지 않고 안전 인지 확인 해야 합니다. IDE에서 전달 하는 경우는 `SCC_DIFF_CONTENTS` 플래그입니다. 소스 제어 플러그 인 소스 제어 파일에 대해 바이트 단위로 디스크에 파일을 확인 하 고 두 개의 파일을 사용자에 게 아무 것도 표시 하지 않고 다른 지 여부를 나타내는 값을 반환 해야 합니다.  
  
 성능 최적화, 소스 제어 플러그 인 체크섬 또는 호출한 바이트 단위로 비교 하는 대신 타임 스탬프를 기반으로 하는 대신 사용할 수 있습니다 `SCC_DIFF_CONTENTS`: 물론 빨라지지만 덜 안정적인 이러한 형태의 비교 됩니다. 모든 소스 제어 시스템에는 이러한 대체 비교 메서드를 지원할 수 있습니다 및 플러그 인 할 내용 비교 하도록 대체 합니다. 모든 원본 제어 플러그 인, 최소한 지원 해야 내용을 비교 합니다.  
  
> [!NOTE]
> 빠른 차이 플래그는 함께 사용할 수 없습니다. 없음 플래그를 전달 하는 것이 유효 하지만 동시에 둘 이상의 전달 올바르지 않습니다. `SCC_DIFF_QUICK_DIFF`을 테스트 하려면 사용할 수는 모든 플래그를 결합 하는 마스크 있지만 매개 변수로 전달 되지 해야 합니다.  
  
|`fOption`|의미|  
|---------------|-------------|  
|SCC_DIFF_IGNORECASE|대/소문자 비교 (빠른 또는 시각적 개체 차이점에 대해 사용할 수 있음).|  
|SCC_DIFF_IGNORESPACE|공백 (빠른 또는 시각적 개체 차이점에 대해 사용할 수 있음)를 무시 합니다.|  
|SCC_DIFF_QD_CONTENTS|자동으로 파일을 바이트 단위로 비교합니다.|  
|SCC_DIFF_QD_CHECKSUM|지원 되는 경우 checksum 통해 파일을 자동으로 비교 합니다. 지원 되지 않는 경우 비교 내용 대체 합니다.|  
|SCC_DIFF_QD_TIME|지원 되는 경우 해당 타임 스탬프를 통해 파일을 자동으로 비교 합니다. 지원 되지 않는 경우 비교 내용 대체 합니다.|  
  
## <a name="see-also"></a>참고 항목  
 [소스 제어 플러그 인 API 함수](../extensibility/source-control-plug-in-api-functions.md)
