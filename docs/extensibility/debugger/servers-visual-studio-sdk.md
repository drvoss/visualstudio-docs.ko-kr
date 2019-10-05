---
title: 서버 (Visual Studio SDK) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- servers, debugging
- debugging [Debugging SDK], servers
ms.assetid: 62236d64-7956-448c-9ac3-5528f3edac1d
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ebd991a5bb61211a33cc965668c48644bdcf9a27
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66348590"
---
# <a name="servers-visual-studio-sdk"></a>서버(Visual Studio SDK)
디버거 아키텍처에는 *server*:

- 포트 및 포트 공급 업체의 컨테이너 이며 세션 디버그 관리자 (SDM) 및 디버그 엔진에 포트 및 포트 공급자 통신 합니다.

- 이름별로 자신을 식별 하 고 해당 포트 및 포트 공급자를 열거할 수 있습니다.

- 로 표시 됩니다는 [IDebugCoreServer2](../../extensibility/debugger/reference/idebugcoreserver2.md) 만 Visual Studio (Visual Studio 실행의 각 인스턴스에 대해 서버 인스턴스 하나)에서 구현 되는 인터페이스입니다.

## <a name="see-also"></a>참고자료
- [포트](../../extensibility/debugger/ports.md)
- [포트 공급자](../../extensibility/debugger/port-suppliers.md)
- [디버거 개념](../../extensibility/debugger/debugger-concepts.md)
- [IDebugCoreServer2](../../extensibility/debugger/reference/idebugcoreserver2.md)