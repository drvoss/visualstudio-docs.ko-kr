---
title: SccAdd 함수 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- SccAdd
helpviewer_keywords:
- SccAdd function
ms.assetid: 545268f3-8e83-446a-a398-1a9db9e866e8
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: daac15bbb7829d510db17ba02057a2dc86c55990
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63432503"
---
# <a name="sccadd-function"></a>SccAdd 함수
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

이 함수는 소스 제어 시스템에 새 파일을 추가합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
SCCRTN SccAdd(  
   LPVOID    pvContext,  
   HWND      hWnd,  
   LONG      nFiles,  
   LPCSTR*   lpFileNames,  
   LPCSTR    lpComment,  
   LONG*     pfOptions,  
   LPCMDOPTS pvOptions  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 pvContext  
 [in] 원본 제어 플러그 인 상황에 맞는 구조입니다.  
  
 hWnd  
 [in] 소스 제어 플러그 인을 제공 하는 모든 대화 상자에 대 한 부모로 사용할 수 있는 IDE 창 핸들입니다.  
  
 nFiles  
 [in] 에 지정 된 대로 현재 프로젝트에 추가 하도록 선택한 파일의 수는 `lpFileNames` 배열입니다.  
  
 lpFileNames  
 [in] 추가할 파일의 정규화 된 로컬 이름 배열입니다.  
  
 lpComment  
 [in] 모든 추가 파일에 적용할 주석입니다.  
  
 pfOptions  
 [in] 파일 단위 별로 제공 되는 명령 플래그의 배열입니다.  
  
 pvOptions  
 [in] 원본 제어 플러그 인에 대 한 옵션입니다.  
  
## <a name="return-value"></a>반환 값  
 원본 제어 플러그 인이 함수의 구현은 다음 값 중 하나를 반환 하:  
  
|값|설명|  
|-----------|-----------------|  
|SCC_OK|추가 작업이 완료 되었습니다.|  
|SCC_E_FILEALREADYEXISTS|선택한 파일이 소스 제어에서 이미 있습니다.|  
|SCC_E_TYPENOTSUPPORTED|형식 (예: 이진) 파일의 소스 제어 시스템에서 지원 되지 않습니다.|  
|SCC_E_OPNOTSUPPORTED|소스 제어 시스템에서이 작업을 지원 하지 않습니다.|  
|SCC_E_ACCESSFAILURE|소스 제어 시스템에 경합 또는 네트워크 문제로 인해 액세스 문제가 있습니다. 재시도 사용 하는 것이 좋습니다.|  
|SCC_E_NOTAUTHORIZED|사용자는이 작업을 수행할 수 없습니다.|  
|SCC_E_NONSPECIFICERROR|일반 오류입니다. 추가 수행 되지 않습니다.|  
|SCC_I_OPERATIONCANCELED|작업이 완료 되기 전에 취소 되었습니다.|  
|SCC_I_RELOADFILE|파일 또는 프로젝트 다시 로드 해야 합니다.|  
|SCC_E_FILENOTEXIST|로컬 파일을 찾을 수 없습니다.|  
  
## <a name="remarks"></a>설명  
 일반적인 `fOptions` 바뀝니다 여기 배열이 `pfOptions`에 하나를 사용 하 여 `LONG` 파일당 사양 옵션입니다. 즉, 파일 형식 파일에서 다를 수 있습니다.  
  
> [!NOTE]
> 둘 다 지정 올바르지 `SCC_FILETYPE_TEXT` 및 `SCC_FILETYPE_BINARY` 하지만 동일한 파일에 대 한 옵션은 둘 다 지정할 수 있습니다. 모두 설정은 설정과 동일 `SCC_FILETYPE_AUTO`,이 경우 소스 제어 플러그 인이 파일 형식입니다.  
  
 다음에 사용 된 플래그의 목록은 합니다 `pfOptions` 배열:  
  
|옵션|값|의미|  
|------------|-----------|-------------|  
|SCC_FILETYPE_AUTO|0x00|소스 제어 플러그 인 파일 유형을 검색 해야 합니다.|  
|SCC_FILETYPE_TEXT|0x01|ASCII 텍스트 파일을 나타냅니다.|  
|SCC_FILETYPE_BINARY|0x02|ASCII 텍스트 이외에 다른 파일 형식을 나타냅니다.|  
|SCC_ADD_STORELATEST|0x04|만 없습니다 델타 파일의 최신 복사본을 저장합니다.|  
|SCC_FILETYPE_TEXT_ANSI|0x08|ANSI 텍스트 파일을 처리합니다.|  
|SCC_FILETYPE_UTF8|0x10|UTF8 형식으로 유니코드 텍스트로 파일을 처리합니다.|  
|SCC_FILETYPE_UTF16LE|0x20|Little Endian 형식 UTF16에 유니코드 텍스트로 파일을 처리합니다.|  
|SCC_FILETYPE_UTF16BE|0x40|처리에서 UTF16 Big Endian 유니코드 텍스트로 서식을 지정 합니다.|  
  
## <a name="see-also"></a>참고 항목  
 [소스 제어 플러그 인 API 함수](../extensibility/source-control-plug-in-api-functions.md)
