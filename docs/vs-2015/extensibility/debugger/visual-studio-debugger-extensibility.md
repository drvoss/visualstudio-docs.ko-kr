---
title: Visual Studio 디버거 확장성 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Visual Studio], Debugging SDK
- Debugging SDK
ms.assetid: c088b6a2-c3ad-446b-830d-9c6f41b2934b
caps.latest.revision: 33
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e337e87d162ac59cc6bb45676c1411692dd1a3bb
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65675260"
---
# <a name="visual-studio-debugger-extensibility"></a>Visual Studio 디버거 확장성
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Visual Studio에는 프로그램에서 버그를 추적 하기 위한 강력 하 고 사용 하기 쉬운 도구를 제공 하는 완전 한 대화형 소스 코드 디버거를 포함 합니다. 디버거는 Visual Basic의 경우 전체 지원 C#, C /C++, 및 JavaScript입니다. 그러나 합니다 [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)]되는에서 사용할 수 있습니다 합니다 [Microsoft 다운로드 센터](http://go.microsoft.com/fwlink/?LinkId=214453), 같은 다양 한 기능을 사용 하 여 디버거에서 다른 프로그래밍 언어를 지원할 수 있습니다.  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 디버거를 다시 디버깅 중인 언어와 관련 된 디버깅 구성 공용 프런트 엔드 (즉, 사용자 인터페이스)입니다. 지원 하기 위해 필요한 모든 새 언어에 대 한는 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 디버거는 디버그 엔진 (DE)와 같은 필요한 백 엔드 구성 요소를 만드는 것입니다. 여기는 [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] 제공 됩니다.  
  
 합니다 [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] 모두에 대 한 전체 참조를 포함 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 새 장치를 만드는 데 필요한 요소입니다. 또한, 샘플 및 자습서를 시작 하는 데 도움이 되는 됩니다.  
  
 디버깅 지원을 사용 하 여 언어 프로젝트 시스템의 종단 간 샘플을 참조 합니다 [IronPython 샘플](https://msdn.microsoft.com/4c41695c-12c1-4670-b43b-d8d84c9e4089)합니다.  
  
 다음 섹션에서는 디버거를 사용 하 여 확장 하는 방법에 설명 합니다 [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)]합니다.  
  
## <a name="in-this-section"></a>섹션 내용  
 [시작](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)  
 에 대해 설명 합니다 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 제품 및 SDK를 설치 하는 방법을 디버깅 합니다.  
  
 [사용자 지정 디버그 엔진 만들기](../../extensibility/debugger/creating-a-custom-debug-engine.md)  
 DE 분리에 독일에 대 한 프로그램을 준비 하 고에서 사용자 지정 하는 DE 프로세스를 설명 합니다.  
  
 [CLR 식 계산기 작성](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)  
 식 계산기를 작성 해야 하는지 여부를 설명 합니다.  
  
 [디버그 엔진 구현 전략 선택](../../extensibility/debugger/choosing-a-debug-engine-implementation-strategy.md)  
 프로그램 DE를 구현 하는 방법에 설명 합니다.  
  
 [참조](../../extensibility/debugger/reference/reference-visual-studio-debugging-apis.md)  
 문서는 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 디버깅 API.  
  
 [샘플](../../extensibility/debugger/visual-studio-debugging-samples.md)  
 공용 언어 런타임 식 계산기 샘플 및 디버그 엔진 샘플에 대 한 링크가 포함 되어 있습니다.
