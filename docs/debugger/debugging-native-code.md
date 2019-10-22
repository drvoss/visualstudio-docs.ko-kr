---
title: 네이티브 코드 디버깅 | Microsoft Docs
ms.date: 04/11/2017
ms.topic: conceptual
f1_keywords:
- vs.debug
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging native code
- debugging [C++], native code
- debugging [Visual Studio], native code
- native code, debugging
ms.assetid: d94eee90-7e0d-4cac-88c1-9831030daa5e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: e51918122834dd6b50952b9cc81a1d24a6477dd0
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72431769"
---
# <a name="debugging-native-code"></a>네이티브 코드 디버깅
이 단원에서는 네이티브 애플리케이션의 몇 가지 일반적인 디버깅 문제와 기술에 대해 설명합니다. 이 단원에서 설명하는 기술은 높은 수준의 기술입니다. Visual Studio 디버거를 사용 하는 방법에 대 한 자세한 내용은 [디버거에서 먼저 확인](../debugger/debugger-feature-tour.md)을 참조 하세요.

## <a name="in-this-section"></a>단원 내용
 [방법: 최적화 된 코드 디버깅](../debugger/how-to-debug-optimized-code.md) 최적화 된 코드를 디버깅 하기 위한 팁, 특히 프로그램의 최적화 되지 않은 버전을 디버깅 해야 하는 이유, 디버그 및 릴리스 구성에 대 한 기본 최적화 설정, 최적화 된 코드에만 표시 되는 버그를 찾기 위한 팁 제공 (켜기 디버그 빌드 구성의 최적화).

 [Debugbreak 및 __debugbreak](../debugger/debugbreak-and-debugbreak.md) Win32 `DebugBreak` 함수에 대해 설명 하 고 Platform SDK의 해당 참조 항목에 대 한 링크를 제공 합니다. `__debugbreak` 내장 함수도 설명합니다.

 [C/C++ 어설션](../debugger/c-cpp-assertions.md) 어설션 문에 대해 설명 하 고, 사용 하는 방법, 작업 결과를 확인 하 고, 오류 조건을 테스트 하 고, `_DEBUG`와의 상호 작용 및 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]에서 지원 되는 어설션의 유형을 설명 합니다.

 [방법: 인라인 어셈블리 코드 디버그](../debugger/how-to-debug-inline-assembly-code.md) 디스어셈블리 창을 사용 하 여 어셈블리 지침 및 레지스터 창을 보는 방법에 대 한 간략 한 지침을 제공 하 여 레지스터 내용을 확인 하 고 해당 창과 관련 된 항목에 대 한 링크를 제공 합니다.

 [MFC 디버깅 기술](../debugger/mfc-debugging-techniques.md) AfxDebugBreak, TRACE 매크로, MFC의 메모리 누수 탐지, mfc 어설션, mfc 디버그 빌드의 크기 감소를 비롯 하 여 MFC 프로그램의 디버깅 기술에 대 한 링크를 제공 합니다.

 [CRT 디버깅 기술](../debugger/crt-debugging-techniques.md) CRT 디버그 라이브러리 사용, 보고용 매크로, malloc와 _malloc_dbg의 차이, 디버그 후크 함수 작성, CRT 디버그 힙 등을 비롯 한 C 런타임 라이브러리에 대 한 디버깅 기술에 대 한 링크를 제공 합니다.

 [네이티브 코드 디버그 faq](../debugger/debugging-native-code-faqs.md) 프로그램 디버깅 C++ 에 대 한 자주 묻는 질문에 대 한 대답을 제공 합니다.

 [COM 및 ActiveX 디버깅](../debugger/com-and-activex-debugging.md) Com 및 ActiveX 디버깅에 사용할 수 있는 도구를 포함 하 여 COM 및 ActiveX 응용 프로그램 디버깅에 대 한 정보를 제공 합니다.

 [방법: 삽입 된 코드 디버그](../debugger/how-to-debug-injected-code.md) 특성을 사용 하는 디버깅 코드에 대 한 지침을 제공 합니다. 여기에는 소스 주석을 표시하는 방법, 삽입한 코드를 보는 방법, 현재 실행 위치에서 디스어셈블리 코드를 보는 방법 등의 내용이 들어 있습니다.

 [연습: 병렬 응용 프로그램 디버깅](../debugger/walkthrough-debugging-a-parallel-application.md) 병렬 **작업** 및 **병렬 스택** 도구 창을 사용 하 여 병렬 응용 프로그램을 디버깅 하는 방법을 설명 합니다.

## <a name="related-sections"></a>관련 단원
 [프로젝트 디버깅 C++ 준비](../debugger/debugging-preparation-visual-cpp-project-types.md) C++ 프로젝트 템플릿에서 만든 네이티브 프로젝트 형식을 디버깅 하는 방법을 설명 하는 항목에 대 한 링크를 제공 합니다.

 [DLL 프로젝트 디버깅](../debugger/debugging-dll-projects.md) 네이티브 및 관리 되는 Dll을 디버깅 하는 방법에 대 한 정보를 제공 합니다.

 [디버거를 먼저 확인 합니다](../debugger/debugger-feature-tour.md) . 디버깅 설명서의 더 큰 섹션에 대 한 링크를 제공 합니다. 이러한 정보에는 디버거의 새로운 기능, 설정 및 준비, 중단점, 예외 처리, 편집하며 계속하기, 관리 코드 디버깅, 네이티브 코드 디버깅, SQL 디버깅, 사용자 인터페이스 참조 등이 있습니다.

## <a name="see-also"></a>관련 항목:

- [디버거 보안](../debugger/debugger-security.md)
- [Visual Studio의 디버깅](../debugger/index.yml)