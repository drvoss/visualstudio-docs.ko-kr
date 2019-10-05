---
title: 디버거 확장 로드맵 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], roadmap
- Debugging SDK, roadmap
ms.assetid: 1f4096a8-f7aa-4dfa-84e1-6d59263e70bb
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 89788f97937d05a3ca4858ed35fd854593ce3357
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66315898"
---
# <a name="roadmap-for-extending-the-debugger"></a>디버거 확장 로드맵
이 설명서에서는 확장에 대 한 가이드 및 참조 정보를 제공 합니다 [!INCLUDE[vs_current_short](../../code-quality/includes/vs_current_short_md.md)] 사용 하 여 디버거를 [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]입니다.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 디버깅 설명서 샘플, 포괄적인 참조 및 디버거를 사용자 지정 하는 일반적인 방법을 보여 주는 몇 가지 대표적인 시나리오에 포함 되어 있습니다.

 컴파일러 및 해당 출력 제품에 디버깅을 설정 하는 데 필요한 항목을 결정 합니다. 경우에 컴파일러.

- Windows 기본 운영 체제를 대상으로 하 고 기록 된 *합니다. PDB* 파일에 통합 된 네이티브 코드 디버그 엔진 (DE)를 사용 하 여 프로그램을 디버깅할 수 있습니다 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]합니다. DE 또는 식 계산기를 구현 하지 않아도 됩니다. 식 계산기 구문의 기록 되는 C++ 프로그래밍 언어입니다.

- Microsoft에도 통합 되어 관리 코드 디버그 엔진 DE, 프로그램을 디버깅할 수 있습니다 하는 MSIL (intermediate language)가 출력 생성 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]합니다. 따라서 식 계산기를 구현만 필요 합니다. 샘플 식 계산기 제공 됩니다. 자세한 내용은 다음 항목을 참조하세요.

   [식 계산](../../extensibility/debugger/expression-evaluation-visual-studio-debugging-sdk.md)

   [식 계산](../../extensibility/debugger/evaluating-expressions.md)

   [식 계산 컨텍스트](../../extensibility/debugger/expression-evaluation-context.md)

   [중단 모드에서 식 계산](../../extensibility/debugger/expression-evaluation-in-break-mode.md)

   [공용 언어 런타임 식 계산기 작성](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)

- 대상 전용 운영 체제나 다른 런타임 환경에 고유한 DE 작성 해야 했습니다. ATL COM을 사용 하 여 간단한 DE를 만드는 자습서가 제공 됩니다. 자세한 내용은 다음 항목을 참조하세요.

   [사용자 지정 디버그 엔진 만들기](../../extensibility/debugger/creating-a-custom-debug-engine.md)

   [자습서: ATL COM을 사용 하 여 디버그 엔진 구축](https://msdn.microsoft.com/library/9097b71e-1fe7-48f7-bc00-009e25940c24)

   [포트 공급자 구현](../../extensibility/debugger/implementing-a-port-supplier.md)

   [샘플](../../extensibility/debugger/visual-studio-debugging-samples.md)

## <a name="see-also"></a>참고자료
- [시작](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)