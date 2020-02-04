---
title: 관리 코드에 대한 코드 분석
ms.date: 06/12/2019
ms.topic: conceptual
helpviewer_keywords:
- code analysis, managed code
- managed code, code analysis
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: f4e5aad0ffcd6febce411d952b1b36a0669b109a
ms.sourcegitcommit: bb72ce6ec173f3ae06c7ae57322c43690f27553c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2020
ms.locfileid: "76967305"
---
# <a name="overview-of-code-analysis-for-managed-code-in-visual-studio"></a>Visual Studio에서 관리 코드에 대 한 코드 분석 개요

Visual Studio는 [레거시 분석](../code-quality/walkthrough-analyzing-managed-code-for-code-defects.md)을 사용 하 여 관리 되는 어셈블리에 대 한 FxCop 정적 분석 및 최신 [.NET Compiler Platform 기반 코드 분석기](../code-quality/roslyn-analyzers-overview.md)를 사용 하는 두 가지 방법으로 관리 코드의 코드 분석을 수행할 수 있습니다. 사용자가 입력 하는 동안 코드를 실시간으로 분석 하는 .NET Compiler Platform 기반 코드 분석기는 컴파일된 코드만 분석 하는 레거시 FxCop 정적 코드 분석을 대체 합니다.

