---
title: '방법: 프로그램에서 충돌이 발생 하는 DLL 찾기 | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.dll
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger, DLL crashes
- Module List dialog box
- errors [debugger], DLL crashes
- Modules window
- debugging [Visual Studio], DLL crashes
- DLLs, load order of
ms.assetid: ecf62568-8b65-4a41-b8a4-e962ff2dfb71
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b7a9421af9e0caf085feb1afb27b53befe837668
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62894049"
---
# <a name="how-to-find-which-dll-your-program-crashed-in-c-c-visual-basic-f"></a>방법: 프로그램에서 충돌이 발생 하는 DLL 찾기 (C#, C++, Visual Basic의 경우 F#)

 시스템 DLL 또는 다른 사람의 코드를 호출하는 동안 애플리케이션에 충돌이 발생하면 충돌 발생 시 활성 상태였던 DLL을 찾아야 합니다. 사용자 프로그램 외부에서 DLL에 충돌이 발생하는 경우 **모듈** 창을 사용하여 위치를 확인할 수 있습니다.

### <a name="to-find-where-a-crash-occurred-using-the-modules-window"></a>모듈 창을 사용하여 충돌이 발생한 위치를 찾으려면

1. 충돌이 발생한 주소를 기록합니다.

    주소 오류 메시지에 표시 되지 않는 경우 대체 방법을 사용 하 여 DLL을 식별 해야 합니다. 시스템 DLL을 생각 하면 [기호를 로드](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md) 디버깅 하는 경우 Microsoft 기호 서버에서. 그렇지 않은 경우 해야 할 수 있습니다 [덤프 파일을 만들도록](../debugger/using-dump-files.md) 사용 하 여 정보를 대신 힙. 다양 한 [도구](https://blogs.msdn.microsoft.com/andrehal/2009/12/31/what-is-a-dump-and-how-do-i-create-one/) 덤프 파일을 만드는 데 사용할 수 있습니다.

2. **디버그** 메뉴에서 **창**을 선택한 다음, **모듈**을 클릭합니다.

3. **모듈** 창에서 **주소** 열을 찾습니다. 이 열을 표시하려면 스크롤 막대를 사용해야 할 수도 있습니다.

4. 주소별로 DLL을 정렬하려면 열 맨 위에 있는 **주소** 단추를 클릭합니다.

5. 정렬된 목록을 조사하여 충돌 위치가 속하는 주소 범위를 가진 DLL을 찾습니다.

6. **이름** 및 **경로** 열에서 DLL 이름과 경로를 확인합니다.

## <a name="see-also"></a>참고 항목
- [DLL 프로젝트 디버그](../debugger/debugging-dll-projects.md)
- [방법: 모듈 창 사용](../debugger/how-to-use-the-modules-window.md)