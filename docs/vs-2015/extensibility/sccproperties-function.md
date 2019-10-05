---
title: SccProperties 함수 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- SccProperties
helpviewer_keywords:
- SccProperties function
ms.assetid: 1bed38c9-73d2-4474-9717-f9dc26a89cbe
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f4e8452465873cb66883abd347406d17b469e90a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68199994"
---
# <a name="sccproperties-function"></a>SccProperties 함수
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

이 함수는 파일 또는 프로젝트에 대 한 소스 제어 속성을 표시합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
SCCRTN SccProperties (  
   LPVOID pvContext,  
   HWND   hWnd,  
   LPCSTR lpFileName  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 pvContext  
 [in] 원본 제어 플러그 인 상황에 맞는 구조입니다.  
  
 hWnd  
 [in] 소스 제어 플러그 인을 제공 하는 모든 대화 상자에 대 한 부모로 사용할 수 있는 IDE 창 핸들입니다.  
  
 lpFileName  
 [in] 프로젝트 파일의 정규화 된 경로 이름입니다.  
  
## <a name="return-value"></a>반환 값  
 원본 제어 플러그 인이 함수의 구현은 다음 값 중 하나를 반환 하:  
  
|값|Description|  
|-----------|-----------------|  
|SCC_OK|속성은 성공적으로 표시 되었습니다.|  
|SCC_I_RELOADFILE|버전 제어 시스템은 IDE이이 파일을 다시 로드 해야 하므로 파일 속성을 수정입니다.|  
|SCC_E_PROJNOTOPEN|지정된 된 프로젝트에 소스 제어에서 열리지 않았습니다.|  
|SCC_E_NOTAUTHORIZED|사용자는이 파일 또는 프로젝트의 속성을 볼 수 있는 권한이 없습니다.|  
|SCC_E_FILENOTCONTROLLED|지정 된 파일 또는 프로젝트 아니며 소스 제어|  
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|알 수 없거나 일반 오류가 발생 했습니다.|  
  
## <a name="remarks"></a>설명  
 소스 제어 플러그 인 자체 대화 상자에서 속성을 표시합니다.  
  
 속성을 원본 제어 플러그 인 정의 되 고 플러그 인에서 플러그 인에 다를 수 있습니다. 반환 해야 하는 경우 플러그 인을 사용 하면 파일의 소스 제어 속성을 변경 하려면, `SCC_I_RELOAD` 이 파일 또는 프로젝트 다시 로드 해야 하는 IDE를 알립니다.  
  
## <a name="see-also"></a>참고 항목  
 [소스 제어 플러그 인 API 함수](../extensibility/source-control-plug-in-api-functions.md)
