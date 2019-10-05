---
title: 디버거 컨텍스트 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], contexts
ms.assetid: 79808036-b680-4e4c-9c61-4ed43aa11323
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 771a3cd8ae25173f3033b3a3229e516570f5dedc
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68200638"
---
# <a name="debugger-contexts"></a>디버거 컨텍스트
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 디버깅, 디버그 엔진 (DE) 동시에 여러 고유한 컨텍스트 내에서 같이 작동 합니다.  
  
- 프로그램의 실행 스트림의 현재 위치를 설명 하는 코드 컨텍스트.  
  
- 문서 컨텍스트 또는 원본 문서 내의 현재 위치를 설명 하는 위치입니다.  
  
- 식 계산 컨텍스트는 식의 평가 수행 하는 컨텍스트를 설명 합니다.  
  
## <a name="in-this-section"></a>섹션 내용  
 [코드 컨텍스트](../../extensibility/debugger/code-context.md)  
 프로그램의 명령 스트림에 않던 언어 및 오늘날의 런타임 아키텍처 코드를 지침은, 하지만 다른 방법 변수로 표현 되지 않을 수 있습니다 위치 주소로 코드 컨텍스트를 설명 합니다.  
  
 [문서 위치](../../extensibility/debugger/document-position.md)  
 Visual Studio IDE에 알려진 소스 파일의 위치는 추상화를 사용 하 여 디버깅에 문서 위치를 정의 합니다.  
  
 [문서 컨텍스트](../../extensibility/debugger/document-context.md)  
 설명 소스 파일과 관련 된 Visual Studio 디버깅 문서 컨텍스트를 나타냅니다. 도 문서 컨텍스트에 기호 처리기 코드 컨텍스트를 매핑하는 방법에 대해 설명 합니다.  
  
 [식 계산 컨텍스트](../../extensibility/debugger/expression-evaluation-context.md)  
 Visual Studio에서 식 평가 컨텍스트에 대 한 정보를 제공합니다. 예를 들어, 스택 프레임과 연결 된 식 계산 컨텍스트를 로컬 변수, 메서드 매개 변수 및 클래스 멤버를 평가 하는 것에 대 한 컨텍스트를 제공 합니다.  
  
## <a name="related-sections"></a>관련 단원  
 [디버깅 개념](../../extensibility/debugger/debugger-concepts.md)  
 기본 디버깅 아키텍처 개념을 설명합니다.  
  
 [디버깅 구성 요소](../../extensibility/debugger/debugger-components.md)  
 Visual Studio 디버그 엔진 (DE), 식 계산기 (EE) 및 기호 처리기 (SH) 포함 하는 디버깅 구성 요소의 개요를 제공 합니다.  
  
 [디버깅 작업](../../extensibility/debugger/debugging-tasks.md)  
 프로그램을 시작 하 고 식을 계산 하는 등의 다양 한 디버깅 작업에 대 한 링크를 포함 합니다.
