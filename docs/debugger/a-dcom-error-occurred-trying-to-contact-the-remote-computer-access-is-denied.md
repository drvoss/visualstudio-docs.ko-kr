---
title: 원격 컴퓨터에 접속하려고 시도하는 동안 DCOM 오류가 발생했습니다. 액세스가 거부되었습니다. | Microsoft 문서
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.remote.dcom_access_denied
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- remote debugging, DCOM error
- remote DCOM access denied error
- DCOM, access errors
ms.assetid: 9d7dfc1b-9fe0-4f54-9c50-9c0e0f8358c5
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 193c93e7c29d3ea9fa13c08c9d77e4e88026d814
ms.sourcegitcommit: 97204b85caadbcf14baeb6738710e287a196673e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/25/2018
ms.locfileid: "49900516"
---
# <a name="a-dcom-error-occurred-trying-to-contact-the-remote-computer-access-is-denied"></a>원격 컴퓨터에 접속하려고 시도하는 동안 DCOM 오류가 발생했습니다. 액세스가 거부되었습니다.
원격 디버깅은 다음과 같은 상황에서 원격 컴퓨터와 로컬 컴퓨터 간의 통신에 DCOM을 사용합니다.  
  
- 디버거를로 **기본 호환성 모드** 또는 **관리 되는 호환성 모드** 체크 인 합니다 **도구 > 옵션 > 디버깅** 페이지  
  
- 관리되는 C++(C++/CLI) 코드를 디버깅하는 경우  
  
- Visual Studio 2013의 경우 **네이티브 편집 하며 계속 하기 사용** 체크 인 합니다 **도구 > 옵션 > 디버깅** 페이지  
  
- 일부 타사 디버깅 시나리오  
  
  이 오류는 Visual Studio 프로세스가 DCOM을 통해 원격 디버거 프로세스에 자신을 인증할 수 없는 경우(또는 제공된 자격 증명이 불충분한 것으로 간주되는 경우) 발생합니다. 다음 해결 방법 중 하나 이상으로 문제를 해결할 수 있습니다.  
  
- **기본 호환성 모드** 및 **관리되는 호환성 모드**를 해제합니다.  
  
- Visual Studio 2013에서 **네이티브 편집하며 계속하기 사용**을 해제합니다.  
  
- 두 컴퓨터를 다시 부팅합니다.  
  
- 원격 디버깅을 수행하려면 자격 증명을 입력해야 하는 경우 자격 증명을 저장하는 옵션을 선택합니다.  
  
## <a name="see-also"></a>참고 항목  
 [원격 디버깅 오류 및 문제 해결](../debugger/remote-debugging-errors-and-troubleshooting.md)   
 [Remote Debugging](../debugger/remote-debugging.md)