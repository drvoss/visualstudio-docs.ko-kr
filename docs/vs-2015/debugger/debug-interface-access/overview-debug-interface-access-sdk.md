---
title: 개요 (디버그 인터페이스 액세스 SDK) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- user-defined types
- .dbg files
- modules
- interfaces [DIA SDK]
- DBG files
- procedures [DIA SDK]
- executable files
- COM objects, in DIA SDK
- compilands
- executable images
ms.assetid: 720b4479-a8bc-4fec-860e-80c1a0780405
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 7374b03da42e34e8ac3be8c7cc570769d9cfd1ff
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68179205"
---
# <a name="overview-debug-interface-access-sdk"></a>개요(디버그 인터페이스 액세스 SDK)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

DIA SDK를 사용 하 여 Microsoft 디버그 정보에 액세스할 수 있습니다. DIA SDK는 COM 기반 Microsoft 디버그 정보의 형식을 변경 될 때마다 코드를 다시 작성 하지 않아도 API 집합을 제공 합니다. DIA SDK에서는 디버그 정보에 의해 생성 된.pdb 및.dbg 파일에 있는 이전 버전의 선택 집합을 읽을 수 있습니다 [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] 5.0 이상 버전.  
  
 DIA SDK의 각 인터페이스 달리 명시 하는 경우 제외 하 고 다른 COM 개체를 나타냅니다. 추가 인터페이스 이므로 추가 개체와 같은 명시적 쿼리를 사용 하 여 생성 됩니다 [idiadatasource:: Opensession](../../debugger/debug-interface-access/idiadatasource-opensession.md) 하거나 [idiasession:: Findchildren](../../debugger/debug-interface-access/idiasession-findchildren.md)합니다 를호출하는대신`QueryInterface` 기존 인터페이스 포인터에 대 한 합니다.  
  
## <a name="see-also"></a>참고 항목  
 [IDiaDataSource::openSession](../../debugger/debug-interface-access/idiadatasource-opensession.md)   
 [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)
