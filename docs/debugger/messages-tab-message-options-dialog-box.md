---
title: 메시지 옵션 대화 상자, 메시지 탭 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- message options, Messages
ms.assetid: fb9fa211-e82c-40a5-9e4b-ba8de07313c0
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: de50e6fe997ce10266cbb51f2fd91c318ab2bd1f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62905534"
---
# <a name="messages-tab-message-options-dialog-box"></a>메시지 옵션 대화 상자, 메시지 탭
사용 하 여는 **메시지** 목록에는 메시지 형식을 선택 하는 탭 [메시지 뷰](../debugger/messages-view.md), 및 메시지 검색 조건을 지정 하려면. 표시할 합니다 [메시지 옵션 대화 상자](../debugger/message-options-dialog-box.md), 선택 **로그 메시지** 에서 합니다 **Spy** 메뉴.

 일반적으로 처음 선택 하면 **메시지 그룹**, 한 다음 개별 선택 하 여 선택 영역을 미세 조정할 **보기로 메시지**합니다. **모든** 단추는 모든 메시지 유형 선택 하며 **None** 단추 형식 선택을 모두 취소 합니다.

 다음 설정을 사용할 합니다 **메시지** 탭:

 **메시지 보기를** 보기에 대 한 특정 메시지를 선택 합니다. 새 메시지 창에서 만든 모든 메시지를 표시할 수 있습니다. 메시지를 필터링 하는 경우는 **메시지** 탭 해당 필터는 새 메시지를 Windows 보기에서 이미 표시 되어 있는 메시지가 없는에 적용 됩니다.

 **메시지 그룹** 보기에 대 한 메시지 그룹을 선택 합니다. 가용성 그룹에는 다음이 포함 됩니다.

- WM_USER: 코드로 WM_USER 보다 크거나 같은 경우

- 등록: 등록 합니다 **RegisterWindowMessage** 호출

- 알 수 없음: 0 (WM_USER-1)과 범위에서 알 수 없는 메시지

  이러한 **메시지 그룹** 아래에 있는 특정 항목에 매핑하지 **표시할 메시지**합니다. 그룹을 선택 하면 선택한 메시지 스트림에 직접 적용 됩니다.

  내에서 확인란을 회색으로 표시 **메시지 그룹** 나타내는 **표시할 메시지** 목록 상자에 해당 그룹의 메시지에 대해 수정한; 해당 그룹의 메시지 유형 중 일부만 선택 됩니다.

  **설정을 기본값으로 저장** 메시지 검색 옵션으로 나중에 사용에 대 한 현재 설정을 저장 합니다. Spy + +를 종료 하는 경우에 이러한 설정은 저장 됩니다.