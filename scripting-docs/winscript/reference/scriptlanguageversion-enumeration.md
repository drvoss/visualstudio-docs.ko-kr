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
ms.openlocfilehash: 802a9f31cc7e3497c5e5fc54395d988552f75e84
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574371"
---
# <a name="scriptlanguageversion-enumeration"></a>SCRIPTLANGUAGEVERSION 열거형
가능한 스크립팅 버전을 지정 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
typedef enum tagSCRIPTLANGUAGEVERSION{    SCRIPTLANGUAGEVERSION_DEFAULT = 0,    SCRIPTLANGUAGEVERSION_5_7  = 1,    SCRIPTLANGUAGEVERSION_5_8  = 2,    SCRIPTLANGUAGEVERSION_MAX  = 255} SCRIPTLANGUAGEVERSION ;  
```  
  
## <a name="enumeration-values"></a>열거형 값  
  
|||  
|-|-|  
|SCRIPTLANGUAGEVERSION_DEFAULT|기본 버전입니다. 정수 값은 0입니다.|  
|SCRIPTLANGUAGEVERSION_5_7|Windows 스크립팅 버전 5.7. 정수 값은 1입니다.|  
|SCRIPTLANGUAGEVERSION_5_8|Windows 스크립팅 버전 5.8. 정수 값은 2입니다.|  
|SCRIPTLANGUAGEVERSION_MAX|최대 버전입니다. 정수 값은 255입니다.|  
  
## <a name="see-also"></a>참조  
 [액티브 스크립트 상수, 열거형 및 오류 코드](../../winscript/reference/active-script-constants-enumerations-and-error-codes.md)