---
title: Office Word 키보드, 키보드 설정, 옵션 대화 상자
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.Microsoft_Office_Tools.Microsoft_Office_Word.Keyboard
- VS.ToolsOptionsPages.Microsoft_Office_Keyboard_Settings.Microsoft_Office_Word_Keyboard
- VST.WordOptions.KeyboardMappingScheme
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- keyboard shortcuts, Office development in Visual Studio
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 5180aa2f4c5022cedcba2c5377d2ff2ac14ffb28
ms.sourcegitcommit: cc5fd59e5dc99181601b7db8b28d7f8a83a36bab
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/11/2019
ms.locfileid: "66835988"
---
# <a name="microsoft-office-word-keyboard-microsoft-office-keyboard-settings-options-dialog-box"></a>Microsoft Office Word 키보드, Microsoft Office 키보드 설정, 옵션 대화 상자
  Microsoft Office Word 및 Visual Studio 둘 다 바로 가기 키를 처리합니다. Visual Studio에서 Word에 다른 명령에 대 한 동일한 바로 가기 키 조합을 나타낼 수 있습니다. Word Visual Studio에서 문서 수준 프로젝트에서 열려 있는 경우 한 번에 하나의 응용 프로그램 바로 가기 키 명령을 받습니다. 기본적으로 Visual Studio는 모든 바로 가기 키 명령을 수신 하지만 단어를 선택 하 여 문서에 포커스가 있을 때 사용자에 게 받도록 할 수 있습니다 **동적 키보드 구성표**합니다.

 명령에서 현재 바로 가기 키를 처리 하는 응용 프로그램에 할당 되지 않은 바로 가기 키를 사용 하는 경우 바로 가기 키를 다른 응용 프로그램에 전달 됩니다.

 선택 하는 옵션은 변경 하지 않는 Word 프로젝트에 대 한 적용 유지 됩니다. 선택 영역에 Microsoft Office Excel 프로젝트; 영향을 주지 않습니다. Microsoft Office Excel 키보드 옵션을 사용 하 여 Excel에 대 한 모든 변경을 확인 해야 합니다.

## <a name="uielement-list"></a>UI 요소 목록
 **Visual Studio 키보드 구성표** Visual Studio는 Word 문서에 포커스가 있을 경우에 모든 바로 가기 키 명령을 수신 합니다. 예를 들어 키를 눌러 **F5** Visual Studio 문서에 포커스가 있는 동안 솔루션 디버깅이 시작 됩니다.

 **동적 키보드 구성표** 에 포커스가 있을 때에 Visual Studio에 바로 가기 키 명령을 수신 합니다. Word 문서에 포커스가 Word 모든 바로 가기 키 명령을 받습니다. 예를 들어 키를 눌러 **F5** Word 열립니다 Word 문서에 포커스가 있는 동안를 **찾기 및 바꾸기** 사용 하 여 대화 상자를 **이동** 탭이 선택 합니다. 키를 누르면 **F5** Visual Studio Visual Studio에 포커스가 있는 동안 솔루션 디버깅이 시작 됩니다.

## <a name="see-also"></a>참고자료
- [Microsoft Office Excel 키보드, Microsoft Office 키보드 설정, 옵션 대화 상자](../vsto/microsoft-office-excel-keyboard-microsoft-office-keyboard-settings-options-dialog-box.md)
