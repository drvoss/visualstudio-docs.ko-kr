---
title: Roslyn 분석기 시작 | Microsoft Docs
ms.date: 04/02/2018
ms.topic: conceptual
ms.assetid: 367c2ec8-3059-46a5-9d1c-57bead0419e7
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 21b2d77d8c038988fa77293280c9ff7ad38cc82e
ms.sourcegitcommit: 90c3187d804ad7544367829d07ed4b47d3f8a72d
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/06/2019
ms.locfileid: "68822333"
---
# <a name="get-started-with-roslyn-analyzers"></a>Roslyn 분석기 시작

Visual Studio에서 라이브 프로젝트 기반 코드 분석기를 사용 하면 API 작성자는 도메인 특정 코드 분석을 NuGet 패키지의 일부로 제공할 수 있습니다. 이러한 분석기는 .NET Compiler Platform (코드 이름 "Roslyn")을 기반으로 하기 때문에 줄을 완료 하기 전에 입력 하는 코드에서 경고를 생성할 수 있습니다 (문제를 검색 하기 위해 코드를 작성 하기 위해 대기 하지 않음). 분석기는 또한 코드를 즉시 정리할 수 있도록 Visual Studio 전구 프롬프트를 통해 자동 코드 수정 사항을 표시할 수 있습니다.

## <a name="get-started"></a>시작

[Roslyn 분석기 개요](../code-quality/roslyn-analyzers-overview.md)

[자습서: 첫 번째 분석기 및 코드 수정 작성](/dotnet/csharp/roslyn-sdk/tutorials/how-to-write-csharp-analyzer-code-fix)

[코드 수정 사항 추가 연습: 분석기 문제에 대 한 사용자 수정 제공](https://msdn.microsoft.com/magazine/dn904670.aspx)

[talk](https://channel9.msdn.com/events/Build/2015/3-725)으로 시청할 수 있는 [Real world Roslyn analyzer](../extensibility/roslyn-analyzers-and-code-aware-library-for-immutablearrays.md)

[GitHub에 대 한 몇 가지 예제는 세 가지 분석기로 그룹화 되어 있습니다.](https://github.com/dotnet/roslyn/blob/master/docs/analyzers/Analyzer%20Samples.md)

## <a name="see-also"></a>참고자료

- [.NET 컴파일러 플랫폼 패키지 버전 참조](roslyn-version-support.md)
- [GitHub OSS 사이트의 추가 문서](https://github.com/dotnet/roslyn/tree/master/docs/analyzers)
- [Roslyn 분석기를 사용 하 여 구현 된 FxCop 규칙](../code-quality/fxcop-rule-port-status.md)
