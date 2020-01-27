---
title: '방법: Spy + + 시작 시작 Microsoft Docs'
ms.date: 12/16/2018
ms.topic: conceptual
helpviewer_keywords:
- Spy++, starting
ms.assetid: 1d36813a-dc2a-4fda-9b3d-a38928a62ced
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 70874d70dd5f845e7b627f2aeb7ae51bafe45995
ms.sourcegitcommit: 7b07e7b5e06e2e13f622445c568b78a284e1a40d
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/23/2020
ms.locfileid: "76542622"
---
# <a name="how-to-start-spy"></a>방법: Spy++ 시작

Visual Studio 또는 명령 프롬프트에서 Spy + +를 시작할 수 있습니다.

 Spy + +를 시작할 때 컴퓨터를 변경할 수 있는 권한을 요청 하는 메시지가 표시 되 면 **예**를 선택 합니다.

> [!NOTE]
> Spy + +의 인스턴스는 하나만 실행할 수 있습니다. 두 번째 인스턴스를 시작 하려고 하면 현재 실행 중인 인스턴스가 포커스를 가져오도록 합니다.

## <a name="prerequisites"></a>전제 조건

Spy + +에는 다음 구성 요소가 필요 합니다. **개별 구성 요소** 탭을 선택 하 고 다음 구성 요소를 선택 하 여 Visual Studio 설치 관리자에서 이러한 구성 요소를 선택할 수 있습니다.

* 디버깅 및 테스트에서  **C++ 프로 파일링 도구를 선택 합니다.**
* 개발 활동에서  **C++ 핵심 기능을 선택 합니다.**

변경한 경우에는 프롬프트에 따라 이러한 구성 요소를 설치 합니다.

## <a name="start-spy-from-visual-studio"></a>Visual Studio에서 Spy + + 시작

**도구** 메뉴에서 **Spy + +** 를 선택 합니다.

Spy + +는 독립적으로 실행 되므로 시작한 후 Visual Studio를 닫을 수 있습니다.

> [!NOTE]
> Spy + +를 사용 하 여 메시지를 기록 하는 경우 운영 체제가 느리게 실행 될 수 있습니다.

## <a name="start-spy-at-a-command-prompt"></a>명령 프롬프트에서 Spy + + 시작

1. 명령 프롬프트 창에서 spyxx를 포함 하는 폴더로 디렉터리를 변경 합니다. 일반적으로이 폴더의 경로는 .입니다. *Visual Studio 설치 폴더*\Common7\Tools\\을\\합니다.

2. **Spyxx**를 입력 합니다.

## <a name="see-also"></a>참조
- [Spy++ 사용](../debugger/using-spy-increment.md)
- [Spy++ 뷰](../debugger/spy-increment-views.md)
- [Spy++ 참조](../debugger/spy-increment-reference.md)
