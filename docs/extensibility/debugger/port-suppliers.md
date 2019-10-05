---
title: 공급 업체 포트 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- port suppliers
- debugging [Debugging SDK], port suppliers
ms.assetid: a8f3db96-1a13-4e93-9ef6-0861880369e0
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5909587cbed118d618ea1605c8a169024028adf0
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66351468"
---
# <a name="port-suppliers"></a>포트 공급자
디버거 아키텍처에는 *포트 공급자*:

- 서버에 포함 하 고 해당 서버에 요청에서 포트를 제공 합니다.

- 추가 하 고 포함 하는 서버에서 포트를 제거할 수 있습니다.

- 서버에 제공 된 모든 포트를 열거할 수 있습니다.

- 로 표시 됩니다는 [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md) 레지스트리를 통해 Visual Studio를 사용 하 여 등록 되는 인터페이스입니다. 이 인터페이스를 호출 하 여 얻을 수 있습니다 [GetPortSupplier](../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md)합니다.

  [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 기본 포트 공급자와 기본 포트를 제공합니다. 사용자 지정 포트를 구현 해야 하는 경우 사용자 지정 포트 공급자도 해야 해당 사용자 지정 포트를 제공 하도록 구현 해야 합니다.

## <a name="see-also"></a>참고자료
- [서버](../../extensibility/debugger/servers-visual-studio-sdk.md)
- [포트](../../extensibility/debugger/ports.md)
- [디버거 개념](../../extensibility/debugger/debugger-concepts.md)
- [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md)
- [GetPortSupplier](../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md)