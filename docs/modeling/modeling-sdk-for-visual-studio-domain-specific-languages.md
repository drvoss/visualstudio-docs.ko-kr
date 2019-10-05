---
title: Visual Studio용 모델링 SDK - 도메인별 언어
titleSuffix: ''
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language Tools
- Domain-Specific Language
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4b955dc6f79c689ca30d8d9876d0888b14127490
ms.sourcegitcommit: 6a19c5ece38a70731496a38f2ef20676ff18f8a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/09/2019
ms.locfileid: "65476524"
---
# <a name="modeling-sdk-for-visual-studio---domain-specific-languages"></a>Visual Studio용 모델링 SDK - 도메인별 언어

Modeling SDK for Visual Studio를 사용 하 여 Visual Studio에 통합할 수 있는 강력한 모델 기반 개발 도구를 만들 수 있습니다. 동일한 방식으로 하나 이상의 모델 정의를 만들고 도구 집합으로 통합할 수 있습니다.

MSDK의 핵심은 비즈니스 영역에서 개념을 나타내기 위해 만드는 모델의 정의입니다. 다양 한 코드 및 Visual Studio의 다른 개체와 상호 작용 하는 기능, 다이어그램 뷰 및 코드 및 기타 아티팩트, 모델, 변환에 대 한 명령을 생성 하는 기능 등의 도구를 사용 하 여 모델을 감쌀 수 있습니다. 모델을 개발할 때 다른 모델 및 도구와 결합하여 개발에 중점을 두는 강력한 도구 집합을 구성할 수 있습니다.

MSDK를 사용하여 도메인 관련 언어(DSL) 형태로 모델을 신속하게 개발할 수 있습니다. 특수 편집기를 사용하여 그래픽 표시법과 함께 스키마 또는 추상 구문을 정의하기 시작합니다. 이 정의로부터 VMSDK는 다음을 생성합니다.

- 트랜잭션 기반 저장소에서 실행되는 강력한 형식의 API를 사용하는 모델 구현입니다.

- 트리 기반 탐색기입니다.

- 자신이 정의하는 모델이나 모델의 일부를 사용자가 볼 수 있는 그래픽 편집기입니다.

- 읽을 수 있는 XML에 모델을 저장하는 Serialization 메서드입니다.

- 프로그램 코드 및 텍스트 템플릿을 사용하는 다른 아티팩트를 생성하기 위한 기능입니다.

이런 모든 기능을 사용자 지정하고 확장할 수 있습니다. 그래도 DSL 정의를 업데이트하고 확장을 손실하지 않으면서 기능을 다시 생성할 수 있는 방식으로 확장이 통합됩니다.

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

[관련된 블로그 게시물](https://devblogs.microsoft.com/devops/the-visual-studio-modeling-sdk-is-now-available-with-visual-studio-2017/)