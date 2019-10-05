---
title: 디버그 중 다른 스레드로 전환
ms.custom: seodec18
ms.date: 04/27/2017
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- threads, switching [debugging]
ms.assetid: 5cd76c52-76fa-4fcc-b37e-e9f0ecac0e9e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 31eb3427a441b4b79bbd57d9da9871118173b15c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62849408"
---
# <a name="how-to-switch-to-another-thread-while-debugging-in-visual-studio-c-visual-basic-c"></a>방법: Visual Studio에서 디버깅 중 다른 스레드로 전환 (C#, Visual Basic의 경우 C++)
다중 스레드 응용 프로그램을 디버깅할 때는 스레드는 작업 중인 사용 하 여 다른 스레드로 전환 하려면 여러 가지 방법 중 하나를 사용할 수 있습니다.

> [!NOTE]
> 스레드 실행 되는 순서를 제어 하려는 경우 해야 [동결 및 재개 스레드](../debugger/get-started-debugging-multithreaded-apps.md)합니다.

코드 편집기 및 다른 다중 스레드 디버깅 창에서 스레드를 검사 하는 경우 노란색 화살표는 현재 스레드를 나타냅니다. 끝이 굽은 녹색 화살표가 현재 디버거 컨텍스트는 현재 스레드가 아닌 있는지를 나타냅니다.

### <a name="to-switch-to-any-thread-that-appears"></a>표시 되는 모든 스레드를 전환 하려면

- 에 **스레드** 하거나 **병렬 조사식** 창 스레드를 두 번 클릭 합니다.

### <a name="to-switch-to-a-thread-in-a-source-window"></a>소스 창에서 스레드를 전환하려면

- 왼쪽된 여백에서 스레드 마커 아이콘을 마우스 오른쪽 단추로 ![스레드 마커](../debugger/media/dbg-thread-marker.png "ThreadMarker")를 가리키고 **전환할**, 전환 하려는 스레드의 이름을 클릭 하 고 . 특정 위치의 스레드만 바로 가기 메뉴에 표시됩니다.

     없는 스레드 마커 표시를 마우스 오른쪽 단추로 클릭 합니다 **스레드** 창 확인 **소스의 스레드 표시** 을 선택 합니다.

### <a name="to-switch-to-a-thread-in-the-debug-location-toolbar"></a>디버그 위치 도구 모음에서 스레드로 전환하려면

1. 에 **디버그 위치** 도구 모음에서 클릭 합니다 **스레드** 목록입니다.

2. 목록에서 전환할 스레드를 클릭합니다.

## <a name="see-also"></a>참고 항목
- [다중 스레드 애플리케이션 디버그](../debugger/debug-multithreaded-applications-in-visual-studio.md)
