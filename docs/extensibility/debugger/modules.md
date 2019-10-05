---
title: 모듈 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- modules
- debugging [Debugging SDK], modules
ms.assetid: c4cf2809-dbdb-4e75-9273-b3d3d77b67d0
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b231ee1eb84f41115a0892cda42a8b7e781e5e53
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66350672"
---
# <a name="modules"></a>모듈
디버거 아키텍처 측면을 *모듈*:

- 코드 예: 실행 파일 또는 DLL의 물리적 컨테이너입니다.

- 해당 기호를 다시 로드 하 고 스스로 설명할 수 있습니다. 모듈 설명 IDE의 모듈 창에 표시 됩니다.

- 로 표시 됩니다는 [IDebugModule2](../../extensibility/debugger/reference/idebugmodule2.md) 모듈을 설명 하는 디버그 엔진에 의해 생성 된 인터페이스입니다.

## <a name="see-also"></a>참고자료
- [디버거 개념](../../extensibility/debugger/debugger-concepts.md)
- [IDebugModule2](../../extensibility/debugger/reference/idebugmodule2.md)