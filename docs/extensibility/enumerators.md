---
title: 열거자 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, enumerators
ms.assetid: a60030c5-e1d1-47e1-84bb-cbfe838ab479
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2d3a0876dfd3a9d7b9cc86b18f6e9a6ba3b780d3
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66334505"
---
# <a name="enumerators"></a>열거자
이 섹션에서는 소스 제어 플러그 인에 대해 알아야 하는 원본 제어 플러그 인 API 데이터 형식 열거자를 나열 합니다.

## <a name="in-this-section"></a>단원 내용
- [코드 명령을](../extensibility/command-code-enumerator.md) 옵션을 열거 합니다 [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md) 하 고 [SccPopulateList](../extensibility/sccpopulatelist-function.md) 함수.

- [메시지](../extensibility/message-enumerator.md) 인쇄 콜백에 대 한 사용 플래그 열거 [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)합니다.

- [상태 코드를 파일](../extensibility/file-status-code-enumerator.md) 라는 소스 제어에서 파일의 상태를 지정 하는 상수 값을 포함 합니다.

- [디렉터리 상태 코드](../extensibility/directory-status-code-enumerator.md) 라는 소스 제어에서 디렉터리의 상태를 지정 하는 상수 값을 포함 합니다.

## <a name="related-sections"></a>관련 단원
- [소스 제어 플러그 인 만들기](../extensibility/internals/creating-a-source-control-plug-in.md) 소스 제어 플러그 인 SDK를 정의 하 고 포함 된 리소스를 설명 합니다.

- [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md) 라는 사용자 지정된 명령에 대 한 고급 옵션에 대 한 메시지를 표시 합니다.

- [SccPopulateList](../extensibility/sccpopulatelist-function.md) 현재 상태에 대 한 파일 목록을 검사 합니다. 또한에서는 합니다 `pfnPopulate` 파일에 대 한 조건과 일치 하지 않는 경우 호출자에 게 알리도록 함수는 `nCommand`합니다.

- [LPTEXTOUTPROC](../extensibility/lptextoutproc.md) 에서 사용 되는 콜백 함수에 설명 합니다 [SccOpenProject](../extensibility/sccopenproject-function.md) IDE를 통해 플러그 인 소스 제어 메시지를 표시 합니다.

- [원본 제어 플러그 인](../extensibility/source-control-plug-ins.md) 원본 제어 플러그 인 API에 있는 모든 요소의 전체 목록을 제공 합니다.