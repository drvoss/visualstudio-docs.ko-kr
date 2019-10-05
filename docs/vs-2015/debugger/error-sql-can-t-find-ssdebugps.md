---
title: '오류: SQL 수&#39;t에서 SSDEBUGPS를 찾을 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.error.sqlde_cant_find_ssdebugps
dev_langs:
- FSharp
- VB
- CSharp
- C++
- SQL
ms.assetid: 596425c8-14c7-4c05-8823-e1c52f420f5e
caps.latest.revision: 9
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 25462a99bd3e773f03af3918a9e25d11ed006c1c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68185205"
---
# <a name="error-sql-can39t-find-ssdebugps"></a>오류: SQL 수&#39;t에서 SSDEBUGPS를 찾을
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

SSDEBUGPS.dll은 SQL Server 디버깅 호스트 구성 요소입니다.  
  
 이 오류는 디버깅을 시작하려고 할 때 발생하며 지정한 파일이 [!INCLUDE[sqprsqlong](../includes/sqprsqlong-md.md)] 컴퓨터에 없음을 나타냅니다. 원격 디버깅 설치를 실행하지 않았거나 어떤 이유로든지 이 파일이 삭제된 경우 이 오류가 발생할 수 있습니다.  
  
 이 오류를 해결하는 데에는 두 가지 방법이 있습니다. 즉, 원격 디버깅 설치 프로그램을 다시 실행하거나 [!INCLUDE[sqprsqlong](../includes/sqprsqlong-md.md)] 머신에 해당 파일을 복사합니다.  
  
 원격 디버깅 설치 프로그램을 다시 실행 하려면의 지침을 따르세요 [원격 디버깅](../debugger/remote-debugging.md)합니다.  
  
 ssdebugps.dll의 복사본을 찾을 수 있으면 이 파일을 [!INCLUDE[sqprsqlong](../includes/sqprsqlong-md.md)] 머신에 복사할 수 있습니다. 이 파일이 있는 경우 위치는 \Program Files\Common Files\Microsoft Shared\SQL Debugging 디렉터리입니다. 다른 할 [!INCLUDE[sqprsqlong](../includes/sqprsqlong-md.md)] 컴퓨터나 컴퓨터 [!INCLUDE[vsprvslong](../includes/vsprvslong-md.md)] 설치 합니다.  
  
### <a name="to-copy-ssdebugpsdll-onto-the-sql-server-2005-machine"></a>SQL Server 2005 컴퓨터에 SSDEBUGPS.dll을 복사하려면  
  
1. [!INCLUDE[sqprsqlong](../includes/sqprsqlong-md.md)] 머신에서 동일한 이름과 경로의 디렉터리에 파일을 복사합니다.  
  
2. **명령 프롬프트**를 열고 다음 명령을 실행하여 파일을 등록합니다.  
  
    ```  
    regsvr32 ssdebugps.dll  
    ```
