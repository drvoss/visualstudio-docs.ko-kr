---
title: '방법: Spy + + 시작 | Microsoft Docs'
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
ms.openlocfilehash: cc247a6391df0357905e2cbdb895bec4e469a248
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63387526"
---
# <a name="how-to-start-spy"></a>방법: Spy++ 시작

시작할 수 있습니다 Spy + + 또는 Visual Studio에서 명령 프롬프트에서.

 시작 하는 경우 Spy + +, 선택한 컴퓨터에 대 한 변경할 수 있는 권한을 요청 하 라는 메시지가 표시 되는 경우 **예**합니다.

> [!NOTE]
> Spy + +의 인스턴스 하나만 실행할 수 있습니다. 두 번째 인스턴스를 시작 하려고 하면 현재 실행 중인 인스턴스는 포커스만 발생 합니다.

## <a name="prerequisites"></a>전제 조건

Spy + +는 다음 구성 요소가 필요합니다. 선택 하 여 Visual Studio 설치 관리자에서 이러한 구성 요소를 선택할 수 있습니다 합니다 **개별 구성 요소** 탭을 선택한 후 다음 구성 요소를 선택 합니다.

* 디버깅 및 테스트에서 선택  **C++ 프로 파일링 도구**
* 개발 작업을 선택 **Visual Studio C++ 핵심 기능**

필요한 내용을 변경 하는 경우 이러한 구성 요소 설치에 지시 합니다.

## <a name="start-spy-from-visual-studio"></a>Visual Studio에서 Spy + + 시작

에 **도구** 메뉴에서 **Spy + +** 합니다.

Spy + + 실행 되므로 하지 독립적으로 시작 된 후에 Visual Studio를 닫을 수 있습니다.

> [!NOTE]
> Spy + +를 사용 하 여 메시지를 기록 하는 경우 운영 체제를 훨씬 더 느리게 수행 될 수 있습니다.

## <a name="start-spy-at-a-command-prompt"></a>Spy + + 명령 프롬프트에서 시작

1. 명령 프롬프트 창에서 spyxx.exe 포함 된 폴더로 디렉터리를 변경 합니다. 일반적으로이 폴더의 경로... \\ *Visual Studio 설치 폴더*\Common7\Tools\\합니다.

2. 입력 **spyxx.exe**합니다.

## <a name="see-also"></a>참고자료
- [Spy++ 사용](../debugger/using-spy-increment.md)
- [Spy++ 뷰](../debugger/spy-increment-views.md)
- [Spy++ 참조](../debugger/spy-increment-reference.md)