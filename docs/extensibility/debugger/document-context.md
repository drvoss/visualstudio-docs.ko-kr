---
title: 컨텍스트 문서 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], contexts
ms.assetid: 8e8b5702-5c16-4988-953d-69dd807d8b84
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ef82c6533eddf32dd8315193531a57e2e7328ad9
ms.sourcegitcommit: 36835f1b3ec004829d6aedf01938494465587436
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/23/2018
ms.locfileid: "39203562"
---
# <a name="document-context"></a>문서 컨텍스트
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 디버깅 하는 *문서 컨텍스트*:  
  
-   소스 파일의 위치를 나타냅니다. 문서 컨텍스트를 사용 하는 원본 파일을 나타날 수 없는 언어에 대 한 런타임 환경에서 일반적으로 생성 된 문서의 위치를 식별 합니다. 예를 들어, 스크립팅 엔진에서 스크립트 문서를 생성할 수 있습니다. 자세한 내용은 [위치에 문서](../../extensibility/debugger/document-position.md)합니다.  
  
-   코드 컨텍스트에 해당 하는 소스 문서의 위치를 설명 합니다. 기호 처리기 코드 컨텍스트를 컨텍스트 설명서, 컴파일러 또는 인터프리터에서 생성 되는 정보를 사용 하 여 매핑됩니다.  
  
-   에 의해 구현 되는 [IDebugDocumentContext2](../../extensibility/debugger/reference/idebugdocumentcontext2.md) 인터페이스입니다.  
  
## <a name="see-also"></a>참고자료  
 [코드 컨텍스트](../../extensibility/debugger/code-context.md)   
 [기호 공급자](../../extensibility/debugger/symbol-provider.md)   
 [기호 공급자 인터페이스](../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [디버거 컨텍스트](../../extensibility/debugger/debugger-contexts.md)