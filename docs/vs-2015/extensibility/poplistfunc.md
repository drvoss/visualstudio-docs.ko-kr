---
title: POPLISTFUNC | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- POPDIRLISTFUNC
helpviewer_keywords:
- POPLISTFUNC callback function
ms.assetid: b2199fd5-d707-4628-92dd-e2a01e2f507a
caps.latest.revision: 17
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8c3ae2ce451f076c33ea5613b71c6d262c1d7a0e
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63430831"
---
# <a name="poplistfunc"></a>POPLISTFUNC
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

이 콜백은에 제공 되는 [SccPopulateList](../extensibility/sccpopulatelist-function.md) IDE에서 소스 제어 플러그 인 파일 또는 디렉터리의 목록을 업데이트 하는 데 사용 됩니다 (도 제공는 `SccPopulateList` 함수).  
  
 사용자가 선택 하는 경우는 **가져오기** 명령을 IDE에서 IDE를 가져올 수 있는 모든 파일의 목록 상자를 표시 합니다. 그러나 IDE 모르는 사용자; 발생할 수 있는 모든 파일의 정확한 목록을 만 플러그 인에이 목록입니다. 다른 사용자에 게는 소스 코드 제어 프로젝트에 파일을 추가 했지만, 이러한 파일은 목록의 나타나지만 IDE에 대 한 알 수 없습니다. IDE를 가져올 수는 것이 생각 하는 파일의 목록을 작성 합니다. 호출 전에이 목록을 사용자에 게 표시 합니다 [SccPopulateList](../extensibility/sccpopulatelist-function.md) `,` 소스 제어 플러그 인을 제공 추가 하 고 목록에서 파일을 삭제 합니다.  
  
## <a name="signature"></a>서명  
 소스 제어 플러그 인 다음과 같은 프로토타입 사용 하 여 IDE 구현 함수를 호출 하 여 목록을 수정 합니다.  
  
```cpp#  
typedef BOOL (*POPLISTFUNC) (  
   LPVOID pvCallerData,  
   BOOL fAddRemove,  
   LONG nStatus,  
   LPSTR lpFileName  
);  
```  
  
## <a name="parameters"></a>매개 변수  
 pvCallerData  
 합니다 `pvCallerData` (IDE) 호출자가 전달 매개 변수를 [SccPopulateList](../extensibility/sccpopulatelist-function.md)합니다. 소스 제어 플러그 인이 매개 변수의 내용에 대해 아무 것도 가정해 야 합니다.  
  
 fAddRemove  
 하는 경우 `TRUE`, `lpFileName` 파일 목록에 추가 해야 하는 파일이 있습니다. 하는 경우 `FALSE`, `lpFileName` 파일이 파일 목록에서 삭제 해야 합니다.  
  
 nStatus  
 상태의 `lpFileName` (조합 합니다 `SCC_STATUS` 비트; 참조 [파일 상태 코드](../extensibility/file-status-code-enumerator.md) 세부 정보에 대 한).  
  
 lpFileName  
 전체 디렉터리 경로를 추가 하거나 목록에서 삭제할 파일 이름입니다.  
  
## <a name="return-value"></a>반환 값  
  
|값|설명|  
|-----------|-----------------|  
|`TRUE`|플러그 인 수 계속이 함수를 호출 합니다.|  
|`FALSE`|IDE (예: 상황 메모리 부족) 쪽에서 문제가 발생이 했습니다. 플러그 인 작업을 중지 해야 합니다.|  
  
## <a name="remarks"></a>설명  
 소스 제어 플러그 인을 추가 하거나 파일 목록에서 삭제 하려는 각 파일에 대해 전달,이 함수를 호출 합니다 `lpFileName`합니다. `fAddRemove` 플래그 목록에 추가할 새 파일 또는 삭제 하려면 이전 파일을 나타냅니다. `nStatus` 매개 변수는 파일의 상태를 제공 합니다. 반환 하는 플러그 인 SCC 파일 추가 및 삭제 완료 되 면 합니다 [SccPopulateList](../extensibility/sccpopulatelist-function.md) 호출 합니다.  
  
> [!NOTE]
> `SCC_CAP_POPULATELIST` 기능 비트 Visual Studio에 필요 합니다.  
  
## <a name="see-also"></a>참고 항목  
 [IDE에 의해 구현 된 콜백 함수](../extensibility/callback-functions-implemented-by-the-ide.md)   
 [원본 제어 플러그 인](../extensibility/source-control-plug-ins.md)   
 [SccPopulateList](../extensibility/sccpopulatelist-function.md)   
 [파일 상태 코드](../extensibility/file-status-code-enumerator.md)
