---
title: SccAddFilesFromSCC 함수 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- SccAddFilesFromSCC
helpviewer_keywords:
- SccAddFilesFromSCC function
ms.assetid: f21a3500-ade8-4dd8-8647-10e2179be9c1
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d5af748c9180644cae928d1b6db3a3f880b6b286
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68200913"
---
# <a name="sccaddfilesfromscc-function"></a>SccAddFilesFromSCC 함수
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

이 함수는 현재 열려 있는 프로젝트를 소스 제어에서 파일 목록을 추가 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
SCCRTN SccAddFilesFromSCC(  
   LPVOID  pContext,  
   HWND    hWnd,  
   LPSTR   lpUser,  
   LPSTR   lpAuxProjPath,  
   LONG    cFiles,  
   LPCSTR* lpFilePaths,  
   LPCSTR  lpDestination,  
   LPCSTR  lpComment,  
   LPBOOL  pbResults  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 pContext  
 [in] 원본 제어 플러그 인 컨텍스트 포인터입니다.  
  
 hWnd  
 [in] 소스 제어 플러그 인을 제공 하는 모든 대화 상자에 대 한 부모로 사용할 수 있는 IDE 창 핸들입니다.  
  
 lpUser  
 [out에서] 사용자 이름 (최대 SCC_USER_SIZE null 종결자 포함).  
  
 lpAuxProjPath  
 [out에서] 프로젝트를 식별 하는 보조 문자열 (최대 `SCC_PRJPATH_`null 종결자를 비롯 하 여 크기).  
  
 cFiles  
 [in] 제공한 파일 수가 `lpFilePaths`합니다.  
  
 lpFilePaths  
 [out에서] 현재 프로젝트에 추가할 파일 이름 배열입니다.  
  
 lpDestination  
 [in] 쓸 파일이 있는 대상 경로입니다.  
  
 lpComment  
 [in] 각 추가 되는 파일에 적용할 주석입니다.  
  
 pbResults  
 [out에서]\ (0이 아닌 또는 TRUE) 성공을 나타내기 위해 집합 또는 실패 하는 플래그의 배열 (0 또는 FALSE) 각 파일에 대 한 (배열 크기 이상 이어야 합니다 `cFiles` long)입니다.  
  
## <a name="return-value"></a>반환 값  
 원본 제어 플러그 인이 함수의 구현은 다음 값 중 하나를 반환 하:  
  
|값|Description|  
|-----------|-----------------|  
|SCC_E_PROJNOTOPEN|프로젝트 열려 있지 않습니다.|  
|SCC_E_OPNOTPERFORMED|연결에 지정 된 대로 동일한 프로젝트에 아닙니다. `lpAuxProjPath.`|  
|SCC_E_NOTAUTHORIZED|사용자는 데이터베이스를 업데이트할 권한이 없습니다.|  
|SCC_E_NONSPECIFICERROR|알 수 없는 오류입니다.|  
|SCC_I_RELOADFILE|파일 또는 프로젝트 다시 로드 해야 합니다.|  
  
## <a name="see-also"></a>관련 항목  
 [소스 제어 플러그 인 API 함수](../extensibility/source-control-plug-in-api-functions.md)
