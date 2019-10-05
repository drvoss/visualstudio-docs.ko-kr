---
title: 문서 위치 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], contexts
ms.assetid: b59d739c-7572-427f-a70d-4e5df63d02c1
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fecc50de842f628c54878af5fc91b5aeb3adefa4
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66345711"
---
# <a name="document-position"></a>문서 위치
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 디버깅을 *위치를 문서화*:

- IDE에 알려진 소스 파일의 위치는 추상화를 제공 합니다. 대부분의 언어에 대 한 현재 문서 위치 수 생각할 수 원본 파일의 위치입니다.

- 디버그 엔진에는 소스 문서의 위치를 설명합니다.

- 에 의해 구현 되는 [IDebugDocumentPosition2](../../extensibility/debugger/reference/idebugdocumentposition2.md) 인터페이스입니다.

## <a name="see-also"></a>참고자료
- [코드 컨텍스트](../../extensibility/debugger/code-context.md)
- [문서 컨텍스트](../../extensibility/debugger/document-context.md)
- [기호 공급자](../../extensibility/debugger/symbol-provider.md)
- [기호 공급자 인터페이스](../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [디버거 컨텍스트](../../extensibility/debugger/debugger-contexts.md)