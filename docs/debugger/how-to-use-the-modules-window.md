---
title: Dll 및 실행 파일을 보려면
titleSuffix: Visual Studio Modules window
ms.custom: seodec18
ms.date: 11/04/2018
ms.topic: conceptual
f1_keywords:
- vs.debug.modules
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- debugger, Modules window
- Modules window
- executable files, displaying while debugging
- debugging [Visual Studio], displaying modules
- DLLs, displaying while debugging
- modules, displaying
ms.assetid: d840fdca-b035-4452-b652-72580c831896
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 400961eaa14b87d70a685a87be5df48ac92c8281
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62906144"
---
# <a name="view-dlls-and-executables-in-the-modules-window-c-c-visual-basic-f"></a>모듈 창에서 Dll 및 실행 파일 보기 (C#, C++, Visual Basic의 경우 F#)

Visual Studio 디버그 하는 동안 합니다 **모듈** 창을 나열 하 고 Dll 및 실행 파일에 대 한 정보를 보여 줍니다 (*.exe* 파일) 앱이 사용 하 합니다.

> [!NOTE]
> 모듈 창을 SQL 또는 스크립트 디버깅에 사용할 수 없는 경우

## <a name="use-the-modules-window"></a>모듈 창 사용

디버깅할 때 모듈 창에서 열려는 선택 **디버깅할** > **Windows** > **모듈** (누르거나 **Ctrl + Alt + U** ).

기본적으로 **모듈** 창에서는 모듈이 로드 순서대로 정렬됩니다. 창 열별로 정렬 하려면 열 맨 위에 있는 헤더를 선택 합니다.

## <a name="load-symbols"></a>기호 로드

합니다 **기호 상태** 열에는 **모듈** 창 디버깅 기호가 로드 된 모듈을 보여 줍니다. 상태가 **기호 로드를 건너뛰었습니다**를 **찾거나 PDB 파일을 열 수 없습니다**, 또는 **포함/제외 설정으로 로드가 비활성화 되었습니다**, 기호를 수동으로 로드할 수 있습니다. 로드 및 기호를 사용 하는 방법에 대 한 자세한 내용은 참조 하세요. [기호 (.pdb) 및 원본 파일 지정](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)합니다.

**기호를 수동으로 로드하려면**

1. 에 **모듈** 창, 기호에 대 한 모듈이 로드 되지 않은 마우스 오른쪽 단추로 클릭 합니다.

   - 선택 **기호 로드 정보** 이유에 대 한 세부 정보에 대 한 기호가 로드 되지 않았습니다.

   - 선택 **기호 로드** 기호를 수동으로 로드 하려면.

1. 기호를 로드 하지 하는 경우 선택 **기호 설정** 열려는 합니다 **옵션** 대화 상자에서 지정 하거나 위치를 로드 하는 기호를 변경 합니다.

   공용 Microsoft 기호 서버 또는 다른 서버에서 기호를 다운로드할 수도 있고 폴더에서 컴퓨터에 기호를 로드할 수 있습니다. 자세한 내용은 참조 하세요 [기호 위치를 지정 하 고 로드 동작](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md#BKMK_Specify_symbol_locations_and_loading_behavior)합니다.

**기호 로드 동작 설정을 변경 합니다.**

1. **모듈** 창에서 모듈을 마우스 오른쪽 단추로 클릭합니다.

1. 선택 **기호 설정**합니다.

1. 선택 **모든 기호 로드**, 포함 하거나 제외할 모듈을 선택 합니다.

1. **확인**을 선택합니다. 변경 내용은 다음 디버깅 세션에 적용 합니다.

**기호 로드를 특정 모듈에 대 한 동작 변경:**

1. **모듈** 창에서 모듈을 마우스 오른쪽 단추로 클릭합니다.

1. 오른쪽 클릭 메뉴에서 선택 하거나 선택 취소 **항상 자동 부하**합니다. 변경 내용은 다음 디버깅 세션에 적용 합니다.

## <a name="see-also"></a>참고자료
- [실행 중단](/previous-versions/visualstudio/visual-studio-2010/7z9se2d8(v=vs.100))
- [디버거에서 데이터 보기](../debugger/viewing-data-in-the-debugger.md)
- [기호 파일(.pdb) 및 원본 파일 지정](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)