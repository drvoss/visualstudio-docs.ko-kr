---
title: 보안 문제 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- security [Debugging SDK]
- debugging [Debugging SDK], security
ms.assetid: d6ffff0a-afb4-4f38-86d8-476c881c4e4b
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: fb6209882a7a71a68728299064edcc13afabff35
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65704415"
---
# <a name="security-issues"></a>보안 문제
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Visual Studio를 사용 하 여 프로그램을 디버깅 하려면 필요한 권한만 개발자 프로그램을 실행 해야 하는 것과 같은 됩니다. 대부분의 경우 (인터넷 정보 서비스와 같은 다른 서비스와 관련 된 경우가 더 높은 수준의 권한 요구할 수 있음)에 대 한 원격 디버깅 포함 됩니다.  
  
 Visual Studio를 실행 하는 동안 프로세스 디버그 관리자 (PDM) 로컬 컴퓨터에서 디버그 프로세스를 추적 합니다. 원격으로 msvsmon.exe를 호출 하는 프로그램은 원격 디버깅을 처리 하 여 PDM를 사용할 수 있도록 하는 개발자에 의해 시작 됩니다. (해당 msvsmon.exe 서비스 및 해당 컴퓨터에서 원격 디버깅을 사용 하려면 수동으로 시작 해야 note 합니다.) Visual Studio (또는 msvsmon.exe)를 실행 하지 않는 경우에 프로세스 없음 디버깅에 대 한 추적 됩니다.  
  
 즉, 개발자가 자신이 특수 권한 없이 시작 프로그램을 디버깅할 수 있습니다. 개발자는 다른 사용자는 동일한 보안 그룹의 멤버인 경우 다른 사용자가 시작한 프로세스를 디버깅할 수도 수 있습니다. 원격 디버깅을 사용 하려면 반드시 필요한만 필요한 복사할 파일을 원격 컴퓨터 msvsmon.exe를 시작 하 고 (참조 [설정 Up the Remote Tools 장치의](https://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c) 자세한).  
  
## <a name="see-also"></a>참고 항목  
 [디버깅 작업](../../extensibility/debugger/debugging-tasks.md)   
 [프로세스 디버그 관리자](../../extensibility/debugger/process-debug-manager.md)   
 [디바이스에서 원격 도구 설정](https://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c)
