---
title: 창 속성 대화 상자, 클래스 탭 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Window Properties dialog box, Class Tab
ms.assetid: eaec9f07-d580-436d-934d-76c4e59439aa
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0917c9a038b42e6302ec1f1782f095ca397a92ef
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62565015"
---
# <a name="class-tab-window-properties-dialog-box"></a>창 속성 대화 상자, 클래스 탭
사용 합니다 **클래스** 선택한 창의 클래스에 대 한 정보 표시를 탭 합니다. 표시할 합니다 [창 속성 대화 상자](../debugger/window-properties-dialog-box.md), 포커스를 이동 하는 [Windows 보기](../debugger/windows-view.md) 창입니다. 트리에서 창 노드를 선택 하 고 선택 **속성** 에서 합니다 **보기** 메뉴.

 다음 설정을 사용할 합니다 **클래스** 탭:

|입력|설명|
|-----------|-----------------|
|**클래스 이름**|이 창 클래스의 이름 (또는 서 수).|
|**클래스 스타일**|클래스 스타일 코드의 조합입니다.|
|**클래스 바이트**|이 창 클래스를 사용 하 여 연결 하는 응용 프로그램별 데이터입니다.|
|**클래스 아톰**|반환 된 클래스에 대 한 atom 합니다 **RegisterClass** 호출 합니다.|
|**인스턴스 핸들**|클래스를 등록 하는 모듈의 인스턴스 핸들입니다. 인스턴스 핸들 고유 하지 않습니다.|
|**창 바이트**|이 클래스의 각 창에 연결 하는 추가 바이트 수입니다. 이러한 바이트의 의미는 응용 프로그램에 의해 결정 됩니다. DWORD 형식의 바이트 값을 확인 하려면 목록 상자를 확장 합니다.|
|**창 프로시저**|현재 주소를 **WndProc** 이 클래스의 windows에 대 한 함수입니다. 이 반해 **창 프로시저** 에 **일반** 서브클래싱된 경우 탭 합니다.|
|**메뉴 이름**|("None" 없음 메뉴의 경우)이이 클래스의 windows와 사용 하 여 연결 된 주 메뉴의 이름입니다.|
|**아이콘 핸들**|("None" 아이콘이 없을 경우)이이 클래스의 windows와 사용 하 여 연결 된 아이콘에 대 한 핸들입니다.|
|**커서 핸들**|("None" 커서가 있는 경우)이이 클래스의 windows와 사용 하 여 연결 된 커서의 핸들입니다.|
|**배경 브러시**|이 클래스 또는 ("none" 이면 브러시 없음) 창 배경을 그리는 미리 정의 된 COLOR_ * 색 중 하나는 windows와 연결 된 배경 브러시에 대 한 핸들입니다.|