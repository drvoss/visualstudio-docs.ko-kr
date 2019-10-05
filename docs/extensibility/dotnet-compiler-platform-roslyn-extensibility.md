---
title: .NET 컴파일러 플랫폼 (&quot;Roslyn&quot;) 확장성 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 564201b3-1e18-4b88-b615-42c2f57f3fe8
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b910d1eb8dcbbe6696c447a7c3a94db533dbbcb3
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66347911"
---
# <a name="net-compiler-platform-quotroslynquot-extensibility"></a>.NET 컴파일러 플랫폼 (&quot;Roslyn&quot;) 확장성
.NET 컴파일러 플랫폼 ("Roslyn")의 핵심 임무는 C# 및 Visual Basic 컴파일러를 열고 도구를 허용 하 고 프로그램에 대 한 풍부한 정보 컴파일러에서 공유 하는 개발자가 있습니다. 코드 분석 도구는 코드 품질 향상 및 생성기 응용 프로그램을 만드는 데 코드입니다. 도구가 더 스마트에 점점 더 많은 컴파일러만 처리 하는 전체 코드 기술 자료의 액세스 해야 있습니다. 불투명 변환기 (소스 코드 및 개체 코드) 대신, Roslyn 컴파일러 도구 및 응용 프로그램에서 코드 관련 작업에 사용할 수 있는 Api를 제공 합니다.

 가장은 Roslyn 컴파일러, 해당 Api, 샘플 및 연습 및 이러한 Api를 기반으로 구축 된 실제 도구에서 완벽 하 게 오픈 소스로 [github.com/dotnet/roslyn](https://github.com/dotnet/Roslyn)합니다. 자세히 알아보고 Roslyn 시작 OSS 사이트로 이동 하세요. 최신 정보에 대 한 링크를 보면 C# 기능과 Visual Basic Roslyn Api를 활용 하 여 도구 작성기를 시작 하는 최종 사용자와 링크를 사용할 수 있습니다.

## <a name="see-also"></a>참고자료
- [Roslyn 분석기 시작](../extensibility/getting-started-with-roslyn-analyzers.md)