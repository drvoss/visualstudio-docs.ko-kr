---
title: '오류: DCOM 통신을 초기화할 수 없습니다. | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.error.unmarshal_server_failed
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 2a7b27e6-2526-4f32-bc4d-eaee447f24ec
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: fff1c56915fe4a06d66bdb08ce60219642933b1b
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65682525"
---
# <a name="error-unable-to-initiate-dcom-communication"></a>오류: DCOM 통신을 초기화할 수 없음
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

로컬 컴퓨터에서 원격 컴퓨터와 통신을 시도하는 동안 DCOM 오류가 발생했습니다. 원격 서버의 방화벽 때문이거나 원격 컴퓨터의 Windows 인증이 손상되었기 때문일 수 있습니다.  
  
### <a name="to-correct-this-error"></a>이 오류를 해결하려면  
  
- 원격 컴퓨터에서 Windows 방화벽을 사용 하는 경우 참조 [설정 Up the Remote Tools 장치의](https://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c) 로컬 디버깅을 위해 방화벽을 구성 하는 방법에 대 한 지침에 대 한 합니다.  
  
- Windows 인증을 복원하려면 두 컴퓨터를 모두 다시 부팅합니다. 로컬 컴퓨터와 원격 컴퓨터에서 이벤트 로그를 검사하여 Kerberos 오류가 있는지 확인하고 알려진 문제가 있는지 도메인 관리자에게 문의합니다.  
  
## <a name="see-also"></a>참고 항목  
 [Remote Debugging](../debugger/remote-debugging.md)
