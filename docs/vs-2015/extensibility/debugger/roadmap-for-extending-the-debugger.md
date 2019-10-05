---
title: 디버거 확장 로드맵 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], roadmap
- Debugging SDK, roadmap
ms.assetid: 1f4096a8-f7aa-4dfa-84e1-6d59263e70bb
caps.latest.revision: 17
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 89a07bc5a5c4c8b7a6054b53610325c654355bc8
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65695953"
---
# <a name="roadmap-for-extending-the-debugger"></a>디버거 확장 로드맵
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

이 설명서에서는 확장에 대 한 가이드 및 참조 정보를 제공 합니다 [!INCLUDE[vs_current_short](../../includes/vs-current-short-md.md)] 사용 하 여 디버거를 [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)]입니다.  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 디버깅 설명서 샘플, 포괄적인 참조 및 디버거를 사용자 지정 하는 일반적인 방법을 보여 주는 몇 가지 대표적인 시나리오에 포함 되어 있습니다.  
  
 컴파일러 및 해당 출력에는 제품에서 디버깅을 구현 하기 위해 필요한를 결정 합니다. 경우에 컴파일러.  
  
- Windows 기본 운영 체제를 대상으로 하 고 쓰기는입니다. PDB 파일에 통합 된 네이티브 코드 디버그 엔진 (DE)를 사용 하 여 프로그램을 디버깅할 수 있습니다 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]합니다. DE 또는 식 계산기를 구현할 필요가 없습니다. 식 계산기 구문의 기록 되는 C++ 프로그래밍 언어입니다.  
  
- Microsoft에도 통합 되어 관리 코드 디버그 엔진 DE, 프로그램을 디버깅할 수 있습니다 하는 MSIL (intermediate language)가 출력 생성 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]합니다. 따라서 식 계산기를 구현만 필요 합니다. 샘플 식 계산기 제공 됩니다. 자세한 내용은 다음 항목을 참조하세요.  
  
     [식 계산](../../extensibility/debugger/expression-evaluation-visual-studio-debugging-sdk.md)  
  
     [식 계산](../../extensibility/debugger/evaluating-expressions.md)  
  
     [식 계산 컨텍스트](../../extensibility/debugger/expression-evaluation-context.md)  
  
     [중단 모드에서 식 계산](../../extensibility/debugger/expression-evaluation-in-break-mode.md)  
  
     [공용 언어 런타임 식 계산기 작성](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)  
  
- 대상 전용 운영 체제나 다른 런타임 환경에 고유한 DE 작성 해야 했습니다. ATL COM을 사용 하 여 간단한 DE를 만드는 자습서가 제공 됩니다. 자세한 내용은 다음 항목을 참조하세요.  
  
     [사용자 지정 디버그 엔진 만들기](../../extensibility/debugger/creating-a-custom-debug-engine.md)  
  
     [자습서: ATL COM을 사용 하 여 디버그 엔진 구축](https://msdn.microsoft.com/9097b71e-1fe7-48f7-bc00-009e25940c24)  
  
     [포트 공급자 구현](../../extensibility/debugger/implementing-a-port-supplier.md)  
  
     [샘플](../../extensibility/debugger/visual-studio-debugging-samples.md)  
  
## <a name="see-also"></a>참고 항목  
 [시작](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)
