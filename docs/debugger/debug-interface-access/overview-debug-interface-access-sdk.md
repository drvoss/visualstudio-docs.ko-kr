---
title: 개요 (Debug Interface Access SDK) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1e4269c620247f256d2cfae2e84b76ff60fcf9ba
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72738601"
---
# <a name="overview-debug-interface-access-sdk"></a>개요(디버그 인터페이스 액세스 SDK)
DIA SDK를 사용 하 여 Microsoft 디버그 정보에 액세스 합니다. DIA SDK는 Microsoft에서 디버그 정보 형식을 변경할 때마다 코드를 다시 작성할 필요가 없도록 하는 COM 기반 API 집합을 제공 합니다. DIA SDK를 사용 하면 [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] 버전 5.0 이상에서 생성 된 .pdb 및 dbg 파일에 있는 이전 버전의 디버그 정보를 선택할 수도 있습니다.

 DIA SDK의 각 인터페이스는 별도로 명시 된 경우를 제외 하 고 다른 COM 개체를 나타냅니다. 추가 인터페이스 및 추가 개체는 기존 인터페이스 포인터에 대 한 `QueryInterface`를 호출 하는 대신 [IDiaDataSource:: openSession](../../debugger/debug-interface-access/idiadatasource-opensession.md) 또는 [IDiaSession:: findchildren](../../debugger/debug-interface-access/idiasession-findchildren.md)과 같은 명시적 쿼리를 통해 생성 됩니다.

## <a name="see-also"></a>참조
- [IDiaDataSource::openSession](../../debugger/debug-interface-access/idiadatasource-opensession.md)
- [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)