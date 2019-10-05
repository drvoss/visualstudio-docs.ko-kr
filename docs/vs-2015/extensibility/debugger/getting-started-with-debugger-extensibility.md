---
title: 디버거 확장성 시작 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- getting started, Debugging SDK
- debugging [Debugging SDK], getting started
- Debugging SDK, getting started
ms.assetid: d6ce6f43-1409-4bf7-93cd-f3464ca23504
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d1c616c7cf8ed90ec3d76046892167b9b742a1b0
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68152707"
---
# <a name="getting-started-with-debugger-extensibility"></a>디버거 확장성 시작
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

합니다 [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] 만들고 디버거 구성 요소 내에서 프로그램을 디버그 하는 데 사용자 지정 해야 하는 정보를 제공 합니다 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 환경입니다.  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 가 이전에 수행 하는 테스트가 광범위 한 유용성에서 파생 하는 향상 된 추가 디버깅 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 디버거. 사용할 수 있습니다 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 다국어 응용 프로그램을 단계별로 디버깅 즉석에서 응용 프로그램 및 다중 언어 솔루션을 디버깅 하는 동안 변수 편집 구현할 수 있습니다.  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 디버깅 실행된-out-of-process 디버깅 중인 프로그램을 사용 하 여 이며 따라서 응용 프로그램의 프로세스 공간에서 개입 수준이 낮습니다. 따라서 디버깅 프로그램 영향을 주지 않고 디버거를 사용 하 여 상호 작용 하는 구성 요소를 작성할 쉽습니다.  
  
 효율적으로 사용 하는 [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)], 다음 잘 알고 있어야 합니다.  
  
- [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 통합된 개발 환경 (IDE)  
  
- C++ 프로그래밍 언어  
  
- ATL COM  
  
## <a name="in-this-section"></a>섹션 내용  
 [디버거 확장 로드맵](../../extensibility/debugger/roadmap-for-extending-the-debugger.md)  
 컴파일러 및 해당 출력에 따라 제품에서 디버깅을 구현 하는 과정을 간략하게 설명 합니다.  
  
 [디버거 구성 요소](../../extensibility/debugger/debugger-components.md)  
 개요를 제공 합니다 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 디버그 엔진 (DE), 식 계산기 (EE) 및 기호 처리기 (SH)를 포함 하는 구성 요소를 디버깅 합니다.  
  
 [디버거 개념](../../extensibility/debugger/debugger-concepts.md)  
 기본 디버깅 아키텍처 개념을 설명합니다.  
  
 [디버거 컨텍스트](../../extensibility/debugger/debugger-contexts.md)  
 디버그 엔진 (DE) 동시에 코드, 설명서 및 식 평가 컨텍스트 내에서 작동 하는 방법을 설명 합니다. 세 개의 컨텍스트, 위치, 위치 또는 평가를 관련 각각에 대해 설명합니다.  
  
 [디버깅 작업](../../extensibility/debugger/debugging-tasks.md)  
 프로그램을 시작 하 고 식을 계산 하는 등의 다양 한 디버깅 작업에 대 한 링크를 포함 합니다.
