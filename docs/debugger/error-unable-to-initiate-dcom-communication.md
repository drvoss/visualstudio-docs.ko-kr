---
title: '오류: DCOM 통신을 초기화할 수 없습니다. | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.unmarshal_server_failed
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c34de251125b49c8b3d7aebf301468b9b1d0252a
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/18/2018
ms.locfileid: "31471797"
---
# <a name="error-unable-to-initiate-dcom-communication"></a>오류: DCOM 통신을 초기화할 수 없습니다.
로컬 컴퓨터에서 원격 컴퓨터와 통신을 시도하는 동안 DCOM 오류가 발생했습니다. 원격 서버의 방화벽 때문이거나 원격 컴퓨터의 Windows 인증이 손상되었기 때문일 수 있습니다.  
  
### <a name="to-correct-this-error"></a>이 오류를 해결하려면  
  
-   원격 컴퓨터에서 Windows 방화벽을 사용 하는 경우 참조 [원격 디버깅](../debugger/remote-debugging.md) 로컬 디버깅에 대 한 방화벽을 구성 하는 방법에 대 한 지침은 합니다.  
  
-   Windows 인증을 복원하려면 두 컴퓨터를 모두 다시 부팅합니다. 로컬 컴퓨터와 원격 컴퓨터에서 이벤트 로그를 검사하여 Kerberos 오류가 있는지 확인하고 알려진 문제가 있는지 도메인 관리자에게 문의합니다.  
  
## <a name="see-also"></a>참고 항목  
 [원격 디버깅](../debugger/remote-debugging.md)