---
title: '방법: Windows 뷰에서 창 검색 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- windows, searching in Windows view
ms.assetid: 30306970-b861-4315-acf8-f86a43d4e73b
caps.latest.revision: 7
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d9d7a64191db82d5fb0b82518d3db1cf1eb1e0ba
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63439073"
---
# <a name="how-to-search-for-a-window-in-windows-view"></a>방법: 창 뷰에서 창 검색
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

검색 조건으로 해당 핸들, 캡션, 클래스 또는 해당 캡션 및 클래스의 조합을 사용 하 여 Windows 보기에서 특정 창에 대 한 검색할 수 있습니다. 또한 검색 시작 방향을 지정할 수 있습니다. 대화 상자의 필드에에서는 창 트리에서 선택한 창의 특성이 표시 됩니다.  
  
 시작 (모든 windows 데스크톱의 자식), 두 번째 수준으로 확장 하 여 트리를 사용 하 여 해당 클래스 이름과 제목으로 windows 바탕 화면 수준을 식별할 수 있도록 합니다. 데스크톱 수준 창을 선택한 후에 해당 수준 특정 자식 창을 찾을 수를 확장할 수 있습니다.  
  
### <a name="to-search-for-a-window-in-windows-view"></a>Windows 뷰에서 창 검색 하려면  
  
1. 따라서 창을 정렬는 Spy + +, 합니다 [Windows 보기](../debugger/windows-view.md) 대상 창과 창에 표시 됩니다.  
  
2. **검색** 메뉴 선택 **창 찾기**합니다.  
  
     합니다 [창 검색 대화 상자](../debugger/window-search-dialog-box.md) 열립니다.  
  
    > [!TIP]
    > 화면이 혼란을 줄이기 위해 선택 된 **spy + + 숨기기** 옵션입니다. 이 옵션은 Spy + +의 주 창을 숨기고 커지고만 합니다 **창 검색** 대화 상자를 다른 응용 프로그램을 기반으로 표시 합니다. Spy + + 주 창을 클릭할 때 복원 됩니다 **확인** 또는 **취소**, 선택을 취소 하면 또는 **Spy + + 숨기기** 옵션입니다.  
  
3. 끌기 합니다 **찾기 도구** 대상 창에 대 한 합니다. 도구를 끌면 합니다 **창 검색** 대화 상자는 선택 된 창의 세부 정보가 표시 됩니다.  
  
     -또는-  
  
     원하는 창 핸들 (예를 들어 디버거)를 알고 있는 경우에 입력할 수 있습니다 합니다 **처리** 상자입니다.  
  
     -또는-  
  
     캡션 및/또는 원하는 창의 클래스를 알고 있는 경우에 입력할 수 있습니다는 **캡션** 및 **클래스** 텍스트 상자 및 선택 취소 합니다 **처리** 텍스트 상자.  
  
4. 선택 **위로** 또는 **아래로** 검색 초기 방향에 대 한 합니다.  
  
5. **확인**을 클릭합니다.  
  
     강조 표시 된 일치 하는 창이 없으면 합니다 [Windows 보기](../debugger/windows-view.md) 창입니다.
