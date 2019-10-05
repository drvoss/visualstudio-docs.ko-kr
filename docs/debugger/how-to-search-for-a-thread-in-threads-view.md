---
title: '방법: 스레드 뷰에서 스레드 검색 | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- threads, searching
ms.assetid: 5609a9b3-c279-4426-9e2e-dd87896a6d6f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fd4014ca9eb99dce383b9de34e26794555b9fbef
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/12/2019
ms.locfileid: "64798524"
---
# <a name="how-to-search-for-a-thread-in-threads-view"></a>방법: 스레드 뷰에서 스레드 검색
스레드 뷰에서 특정 스레드에 대 한 검색 조건으로 스레드 ID 또는 모듈 문자열을 사용 하 여 검색할 수 있습니다. 또한 검색 시작 방향을 지정할 수 있습니다. 대화 상자의 필드에에서는 스레드 트리에서 선택한 스레드의 특성이 표시 됩니다.

### <a name="to-search-for-a-thread-in-threads-view"></a>스레드 뷰에서 스레드 검색 하려면

1. 따라서 창을 정렬는 Spy + + 및 활성 [스레드 뷰](../debugger/threads-view.md) 창이 표시 됩니다.

2. **검색** 메뉴 선택 **스레드 찾기**합니다.

    합니다 [스레드 검색 대화 상자](../debugger/thread-search-dialog-box.md) 열립니다.

3. 검색 조건으로 스레드 ID 또는 모듈 문자열을 입력 합니다.

4. 값을 지정 하지 않을 필드의 선택을 취소 합니다.

   > [!TIP]
   > 모듈을 소유 하는 모든 스레드를 찾으려면의 선택을 취소 합니다 **스레드** 텍스트 상자 및 형식 모듈의 이름 합니다 **모듈** 상자. 사용 하 여 **다음 찾기** 스레드에 대 한 검색을 계속 하려면.

5. 선택 **위로** 또는 **아래로** 검색 초기 방향에 대 한 합니다.

6. **확인**을 클릭합니다.

   일치 하는 스레드가 있으면 스레드 보기 창에서 강조 표시 됩니다.