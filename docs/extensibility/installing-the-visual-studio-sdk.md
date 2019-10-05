---
title: Visual Studio SDK 설치 | Microsoft Docs
ms.date: 07/12/2018
ms.topic: conceptual
ms.assetid: c730edb6-5099-4c16-85a8-08def09f1455
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4208c20cc3e7da34efaf98af16f0f41d54613824
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66340754"
---
# <a name="install-the-visual-studio-sdk"></a>Visual Studio SDK 설치

Visual Studio SDK (소프트웨어 개발 키트)는 Visual Studio 설치에서 선택적 기능입니다. 또한 VS SDK를 나중에 설치할 수 있습니다.

## <a name="install-the-visual-studio-sdk-as-part-of-a-visual-studio-installation"></a>Visual Studio 설치의 일부로 Visual Studio SDK 설치

Visual Studio 설치에서 VS SDK를 포함 하려면 설치를 **Visual Studio 확장 개발** 워크 로드 아래 **기타 도구 집합**합니다. 이 워크 로드는 Visual Studio SDK 및 필수 설치 됩니다. 추가 선택 하거나 구성 요소를 선택 하 여 설치를 조정할 수 있습니다 합니다 **요약** 보기.

## <a name="install-the-visual-studio-sdk-after-installing-visual-studio"></a>Visual Studio를 설치한 후 Visual Studio SDK를 설치 합니다.

Visual Studio 설치를 완료 한 후 Visual Studio SDK를 설치 하려면 Visual Studio 설치 관리자를 다시 실행 하 고 선택 합니다 **Visual Studio 확장 개발** 워크 로드.

## <a name="install-the-visual-studio-sdk-from-a-solution"></a>솔루션에서 Visual Studio SDK를 설치 합니다.

메시지가 표시 되는 확장성 프로젝트를 사용 하 여 솔루션을를 열면 먼저 VS SDK를 설치 하지 않고는 **누락 된 기능 설치** 설치 하는 대화는 **Visual Studio 확장 개발** 워크 로드:

![설치 확장 개발](../extensibility/media/install-extension-development.png "설치 확장 개발")

## <a name="install-the-visual-studio-sdk-from-the-command-line"></a>명령줄에서 Visual Studio SDK를 설치 합니다.

모든 Visual Studio 워크 로드 또는 구성 요소를 사용 하 여 설치할 수도 있습니다는 **Visual Studio 확장 개발** 작업 (ID: Microsoft.VisualStudio.Workload.VisualStudioExtension) 명령줄에서. 참조 [명령줄 매개 변수를 사용 하 여 Visual Studio 설치](../install/use-command-line-parameters-to-install-visual-studio.md) 일반 지침은 워크 로드 또는 구성 요소 식별자를 확인 하 고 적절 한 명령줄 스위치에 대 한 자세한 내용은 합니다.

Visual Studio의 설치 된 버전과 일치 하는 Visual Studio 설치 관리자를 사용 해야 하는 참고 합니다. 예를 들어, Visual Studio Enterprise를 컴퓨터에 설치 된 경우 Visual Studio Enterprise 설치 관리자를 실행 해야 합니다 (*vs_enterprise.exe*).