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
ms.openlocfilehash: 11ad6280ad1213008bbb8ca8f6311ca34231d308
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72732438"
---
# <a name="how-to-switch-to-another-thread-while-debugging-in-visual-studio-c-visual-basic-c"></a>방법: Visual Studio에서 디버깅 하는 동안 다른 스레드로 전환 (C#, Visual Basic, C++)
다중 스레드 응용 프로그램을 디버깅 하는 경우 여러 메서드 중 하나를 사용 하 여 작업 중인 스레드에서 다른 스레드로 전환할 수 있습니다.

> [!NOTE]
> 스레드가 실행 되는 순서를 제어 하려면 [스레드를 중지 하 고 재개](../debugger/get-started-debugging-multithreaded-apps.md)해야 합니다.

코드 편집기 및 다른 다중 스레드 디버깅 창에서 스레드를 검사 하는 경우 노란색 화살표는 현재 스레드를 나타냅니다. 녹색이 있는 녹색 화살표는 현재 스레드가 아닌 스레드에 현재 디버거 컨텍스트가 있음을 나타냅니다.

### <a name="to-switch-to-any-thread-that-appears"></a>표시 되는 스레드로 전환 하려면

- **스레드** 또는 **병렬 조사식** 창에서 스레드를 두 번 클릭 합니다.

### <a name="to-switch-to-a-thread-in-a-source-window"></a>소스 창에서 스레드를 전환하려면

- 왼쪽 여백에서 스레드 마커 아이콘 ![스레드 마커](../debugger/media/dbg-thread-marker.png "ThreadMarker")를 마우스 오른쪽 단추로 클릭 하 고 **전환**을 가리킨 다음 전환 하려는 스레드의 이름을 클릭 합니다. 특정 위치의 스레드만 바로 가기 메뉴에 표시됩니다.

     스레드 마커가 나타나지 않으면 **스레드** 창을 마우스 오른쪽 단추로 클릭 하 고 **소스에 스레드 표시** 가 선택 되어 있는지 확인 합니다.

### <a name="to-switch-to-a-thread-in-the-debug-location-toolbar"></a>디버그 위치 도구 모음에서 스레드로 전환하려면

1. **디버그 위치** 도구 모음에서 **스레드** 목록을 클릭 합니다.

2. 목록에서 전환할 스레드를 클릭합니다.

## <a name="see-also"></a>참조
- [다중 스레드 애플리케이션 디버그](../debugger/debug-multithreaded-applications-in-visual-studio.md)
