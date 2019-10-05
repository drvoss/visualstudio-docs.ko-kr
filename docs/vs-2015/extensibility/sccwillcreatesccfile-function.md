---
title: SccWillCreateSccFile 함수 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- SccWillCreateSccFile
helpviewer_keywords:
- SccWillCreateSccFile function
ms.assetid: 0d7542f0-4351-41b3-b24c-960ab99c05a1
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: cb0df475098a0fb0675327cece6dd9c643a0c4d7
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68147954"
---
# <a name="sccwillcreatesccfile-function"></a>SccWillCreateSccFile 함수
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

이 함수는 소스 제어 플러그 인을 MSSCCPRJ 만들기를 지원 하는지 여부를 결정 합니다. SCC 파일의 각 지정 된 파일입니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
SCCRTN SccWillCreateSccFile(  
   LPVOID  pContext,  
   LONG    nFiles,  
   LPCSTR* lpFileNames,  
   LPBOOL  pbSccFiles  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 pContext  
 [in] 원본 제어 플러그 인 컨텍스트 포인터입니다.  
  
 nFiles  
 [in] 에 포함 된 파일 이름의 개수는 `lpFileNames` 의 길이와 배열는 `pbSccFiles` 배열입니다.  
  
 lpFileNames  
 [in] 확인 하려면 정규화 된 파일 이름의 배열입니다 (배열 호출자가 할당 해야 합니다).  
  
 pbSccFiles  
 [out에서] 결과 저장할 배열입니다.  
  
## <a name="return-value"></a>반환 값  
 원본 제어 플러그 인이 함수의 구현은 다음 값 중 하나를 반환 하:  
  
|값|설명|  
|-----------|-----------------|  
|SCC_OK|명령 실행 성공|  
|SCC_E_INVALIDFILEPATH|배열에서 경로 중 하나가 올바르지 않습니다.|  
|SCC_E_NONSPECIFICERROR|알 수 없는 오류가 발생 했습니다.|  
  
## <a name="remarks"></a>설명  
 이 함수는 소스 제어 플러그 인을 MSSCCPRJ 지원을 제공 하는 경우를 결정 하는 파일의 목록을 사용 하 여 호출 됩니다. 각 (대 한 자세한 내용은 MSSCCPRJ 지정 된 파일에 대 한 SCC 파일. SCC 파일 참조 [MSSCCPRJ 합니다. SCC 파일](../extensibility/mssccprj-scc-file.md)). 원본 제어 플러그 인 MSSCCPRJ 만드는 기능이 있는지 선언할 수 있습니다. SCC 파일 선언 하 여 `SCC_CAP_SCCFILE` 초기화 중입니다. 플러그 인 반환 `TRUE` 또는 `FALSE` 파일당는 `pbSccFiles` 를 나타내는 지정 된 파일의 MSSCCPRJ 있는 배열입니다. 소스 코드 제어를 지원 합니다. 플러그 인 경우 함수에서 성공 코드를 반환, 반환 배열에 값이 적용 됩니다. 오류가 발생 하면 배열 무시 됩니다.  
  
## <a name="see-also"></a>관련 항목  
 [원본 제어 플러그 인 API 함수](../extensibility/source-control-plug-in-api-functions.md)   
 [MSSCCPRJ.SCC 파일](../extensibility/mssccprj-scc-file.md)
