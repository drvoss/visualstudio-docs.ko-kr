---
title: OPTNAMECHANGEPFN | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- OPTNAMECHANGEPFN
helpviewer_keywords:
- OPTNAMECHANGEPFN callback function
ms.assetid: 147303f3-c7f1-438a-81b7-db891ea3d076
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4969dff811b6517c0274a35884703a9dc0c693cb
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68194099"
---
# <a name="optnamechangepfn"></a>OPTNAMECHANGEPFN
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

이것이에 대 한 호출에 지정 된 콜백 함수는 [SccSetOption](../extensibility/sccsetoption-function.md) (옵션을 사용 하 여 `SCC_OPT_NAMECHANGEPFN`) 이름 변경에 대 한 소스 제어 플러그 인 다시 IDE 통신에 사용 되 고 합니다.  
  
## <a name="signature"></a>서명  
  
```cpp#  
typedef void (*OPTNAMECHANGEPFN)(  
   LPVOID pvCallerData,  
   LPCSTR pszOldName,  
   LPCSTR pszNewName  
);  
```  
  
## <a name="parameters"></a>매개 변수  
 pvCallerData  
 [in] 에 대 한 이전 호출에 지정 된 사용자 값을 [SccSetOption](../extensibility/sccsetoption-function.md) (옵션을 사용 하 여 `SCC_OPT_USERDATA`).  
  
 pszOldName  
 [in] 파일의 원래 이름입니다.  
  
 pszNewName  
 [in] 파일의 이름은로 바뀌었습니다.  
  
## <a name="return-value"></a>반환 값  
 없음  
  
## <a name="remarks"></a>설명  
 소스 제어 작업을 하는 동안 파일의 이름을 바꾸면, 소스 제어 플러그 인이 콜백을 통해 이름 변경 하는 방법에 대 한 IDE를 알릴 수 있습니다.  
  
 호출 하지 IDE이이 콜백은 지원 하지 않는 경우는 [SccSetOption](../extensibility/sccsetoption-function.md) 를 지정 합니다. 하는 경우 플러그 인을 지원 하지 않으면이 콜백에서 반환 `SCC_E_OPNOTSUPPORTED` 에서 `SccSetOption` IDE 콜백을 설정 하려고 할 때 작동 합니다.  
  
## <a name="see-also"></a>참고 항목  
 [IDE에 의해 구현 된 콜백 함수](../extensibility/callback-functions-implemented-by-the-ide.md)   
 [SccSetOption](../extensibility/sccsetoption-function.md)
