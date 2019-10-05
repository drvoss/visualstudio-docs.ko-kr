---
title: SCRIPTLANGUAGEVERSION 열거형 | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 58aa904a-e3ed-41c6-82d6-e91c8279a792
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6aab63989d1ae02f7c75fc9c20a14d59e8a05078
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62840214"
---
# <a name="scriptlanguageversion-enumeration"></a>SCRIPTLANGUAGEVERSION 열거형
버전 스크립팅 가능한을 지정 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
typedef enum tagSCRIPTLANGUAGEVERSION{    SCRIPTLANGUAGEVERSION_DEFAULT = 0,    SCRIPTLANGUAGEVERSION_5_7  = 1,    SCRIPTLANGUAGEVERSION_5_8  = 2,    SCRIPTLANGUAGEVERSION_MAX  = 255} SCRIPTLANGUAGEVERSION ;  
```  
  
## <a name="enumeration-values"></a>열거형 값  
  
|||  
|-|-|  
|SCRIPTLANGUAGEVERSION_DEFAULT|기본 버전입니다. 정수 값은 0입니다.|  
|SCRIPTLANGUAGEVERSION_5_7|Windows 버전 5.7을 스크립팅 합니다. 정수 값은 1입니다.|  
|SCRIPTLANGUAGEVERSION_5_8|Windows 버전 5.8를 스크립팅 합니다. 정수 값은 2입니다.|  
|SCRIPTLANGUAGEVERSION_MAX|최대 버전입니다. 정수 값은 255입니다.|  
  
## <a name="see-also"></a>참고 항목  
 [액티브 스크립트 상수, 열거형 및 오류 코드](../../winscript/reference/active-script-constants-enumerations-and-error-codes.md)