---
title: 디버깅이란 무엇인가요?
description: 앱을 디버그 하는 것을 이해합니다
ms.custom: debug-experiment
ms.date: 10/17/2018
ms.topic: conceptual
helpviewer_keywords:
- debugger
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c01317f3b8fa92cf1bc17c3745f708e0d3f26e5b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62901233"
---
# <a name="what-is-debugging"></a>디버깅이란 무엇인가요?

Visual Studio 디버거는 강력한 도구입니다. 와 같은 몇 가지 용어에 설명 하려고 사용 하는 방법을 알아보겠습니다, 전에 *디버거*를 *디버깅*, 및 *디버그 모드*합니다. 이 이렇게 하면 찾기 및 버그를 해결 하는 방법에 대 한 나중에 설명할 때 지시할 동일한 작업에 대 한 합니다.

## <a name="debugger-vs-debugging"></a>디버깅 및 디버거

용어 *디버깅* 는 많은 다른 작업을 의미할 수 있습니다 하지만 문자 그대로 대부분의 코드에서 버그를 제거 합니다. 이제이 작업을 수행 하는 방법 많이 있습니다. 예를 들어, 코드 분석기를 사용 하 여 또는 입력 오류를 찾는 코드를 스캔 하 여 디버깅할 수 있습니다. 성능 프로파일러를 사용 하 여 코드를 디버깅할 수 있습니다. 사용 하 여 디버깅할 수 있습니다 또는 한 *디버거*합니다.

디버거는 실행 중인 앱에 연결 하 고 코드를 검사할 수 있는 전문적인된 개발자 도구. Visual Studio의 디버깅 설명서에서이 일반적으로 "디버깅"를 말할 때는 의미 합니다.

## <a name="debug-mode-vs-running-your-app"></a>디버그 모드 및 앱 실행

처음으로 Visual Studio에서 앱을 실행 하는 경우 녹색 화살표 단추를 눌러 시작할 수 있습니다 ![디버깅 시작](../debugger/media/dbg-tour-start-debugging.png "디버깅 시작") 도구 모음에서 (또는 **F5**). 기본적으로 **디버그** 값 왼쪽 드롭다운 목록에 표시 됩니다. 이 응용 프로그램을 디버깅 하는 실행 중인 작업을 수행 하는 인상이 있다면 Visual Studio를 처음 접하는 경우 앱-자신이-하지만이 기본적으로 두 가지 매우 다른 작업입니다.

![디버그 빌드를 선택 합니다.](../debugger/media/what-is-debugging-debug-build.png)

A **디버그** 값 디버그 구성을 나타냅니다. 앱을 시작 하는 경우 (녹색 화살표를 눌러 또는 **F5**), 디버그 구성에서 앱 시작 *디버그 모드*, 즉 with 실행 하는 앱에 디버거를 연결 합니다. 이렇게 하면 전체 디버깅 앱에서 버그를 찾을 수 있도록 하는 데 사용할 수 있는 기능 집합이 있습니다.

프로젝트가 열려 있으면 선택가 표시 된 드롭다운 선택기 **디버그** 선택한 **릴리스** 대신 합니다.

![릴리스 빌드를 선택 합니다.](../debugger/media/what-is-debugging-release-build.png)

이 설정은 전환 하면 프로젝트를 변경 하면 디버그 구성에서 릴리스 구성으로 합니다. Visual Studio 프로젝트에는 사용하는 프로그램에 대한 별도의 릴리스 및 디버그 구성이 있습니다. 최종 릴리스 배포용 릴리스 버전과 디버그 버전은 디버깅용 빌드할 수 있습니다. 릴리스 빌드 성능을 위해 최적화 되어 있지만 디버그 빌드는 디버깅에 대 한 더 나은.

## <a name="when-to-use-a-debugger"></a>디버거를 사용 하는 경우

디버거는 찾고 앱에서 버그를 수정 하는 필수 도구입니다. 그러나 상황에 맞는 king, 이며 프로그램 disposable 신속 하 게 버그 또는 오류를 제거 하는 데 필요한 모든 도구를 활용 하는 것이 중요 합니다. 경우에 따라 오른쪽 "도구"를 더 잘 코딩 사례 수 있습니다. 다른 도구 및 디버거를 사용 하는 경우 학습, 또한 디버거를 보다 효과적으로 사용 하는 방법을 배웁니다.

## <a name="next-steps"></a>다음 단계

이 문서에서는 몇 가지 일반적인 디버깅 개념을 알아보았습니다. 다음으로 Visual Studio를 사용 하 여 디버그 하는 방법 및 버그가 줄어들었습니다를 사용 하 여 코드를 작성 하는 방법을 학습을 시작할 수 있습니다. 다음 문서 표시 C# 코드 예제를 보려면 하지만 개념은 Visual Studio에서 지 원하는 모든 언어에 적용 합니다.

> [!div class="nextstepaction"]
> [완전 초보자를 위한 디버깅](../debugger/debugging-absolute-beginners.md)

> [!div class="nextstepaction"]
> [디버깅 기술 및 도구](../debugger/write-better-code-with-visual-studio.md)
