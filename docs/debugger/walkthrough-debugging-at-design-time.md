---
title: 디자인 타임에 디버그 | Microsoft Docs
ms.custom: ''
ms.date: 01/10/2019
ms.topic: conceptual
dev_langs:
- VB
helpviewer_keywords:
- debugging [Visual Studio], design-time
- breakpoints, design-time debugging
- Immediate window, design-time debugging
- design-time debugging
ms.assetid: 35bfdd2c-6f60-4be1-ba9d-55fce70ee4d8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: beb16ae52f880e31bd19a185d47b13c02026752f
ms.sourcegitcommit: 939407118f978162a590379997cb33076c57a707
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/13/2020
ms.locfileid: "75916153"
---
# <a name="debug-at-design-time-in-visual-studio-c-ccli-visual-basic-f"></a>Visual Studio에서 디자인 타임에 디버그 (C#, C++/cli, Visual Basic, F#)

응용 프로그램이 실행 되는 동안 대신 디자인 타임에 코드를 디버그 하려면 **직접** 실행 창을 사용할 수 있습니다.

선언적 데이터 바인딩 시나리오와 같이 XAML 디자이너에서 응용 프로그램 뒤의 XAML 코드를 디버그 하려면 **프로세스에 연결을** **사용 하 여 > ** 합니다.

## <a name="use-the-immediate-window"></a>직접 실행 창 사용

Visual Studio **직접** 실행 창을 사용 하 여 응용 프로그램을 실행 하지 않고 함수 또는 서브루틴을 실행할 수 있습니다. 함수 또는 서브루틴이 중단점을 포함 하는 경우 Visual Studio가 중단점에서 중단 됩니다. 그런 다음 디버거 창을 사용하여 프로그램 상태를 조사할 수 있습니다. *디자인 타임에*이 기능을 디버깅 이라고 합니다.

다음 예는 Visual Basic에 있습니다. C#, F#및 C++/cli 앱에서 디자인 타임에 **직접 실행** 창을 사용할 수도 있습니다.

1. 빈 Visual Basic 콘솔 앱에 다음 코드를 붙여 넣습니다.

   ```vb
   Module Module1

       Sub Main()
           MySub()
       End Sub

       Function MyFunction() As Decimal
           Static i As Integer
           i = i + 1
           Return i
       End Function

       Sub MySub()
           MyFunction()

       End Sub
   End Module
   ```

1. 줄 **끝 함수**에서 중단점을 설정 합니다.

1. **디버그** > **Windows** > **즉시**를 선택 하 여 **직접 실행** 창을 엽니다. 창에 `?MyFunction`를 입력 한 다음 **enter**키를 누릅니다.

   중단점이 적중 되 고 **지역** 창의 **MyFunction** 값이 **1**입니다. 앱이 중단 모드에 있는 동안 호출 스택 및 기타 디버깅 창을 검사할 수 있습니다.

1. Visual Studio 도구 모음에서 **계속** 을 선택 합니다. 앱이 종료 되 고 **1** 은 **직접 실행** 창에 반환 됩니다. 여전히 디자인 모드에 있는지 확인 합니다.

1. **직접 실행** 창에 `?MyFunction`를 다시 입력 하 고 **enter**키를 누릅니다. 중단점이 적중 되 고 **지역** 창의 **MyFunction** 값이 **2**입니다.

1. **계속**을 선택 하지 않고 **직접 실행** 창에 `?MySub()`를 입력 한 다음 **enter**키를 누릅니다. 중단점이 적중 되 고 **지역** 창의 **MyFunction** 값이 **3**입니다. 앱이 중단 모드에 있는 동안에는 앱 상태를 검사할 수 있습니다.

1. 선택 **계속**합니다. 중단점은 다시 적중 되며 **지역** 창의 **MyFunction** 값은 이제 **2**입니다. **직접 실행** 창에서 **식을 계산 하 고 값을 반환 하지 않습니다**.

1. **계속** 을 선택 합니다. 앱이 종료 되 고 **2** 가 **직접 실행** 창에 반환 됩니다. 여전히 디자인 모드에 있는지 확인 합니다.

1. **직접 실행** 창의 내용을 지우려면 창을 마우스 오른쪽 단추로 클릭 하 고 **모두 지우기**를 선택 합니다.

## <a name="debug-a-custom-xaml-control-at-design-time-by-attaching-to-xaml-designer"></a>XAML 디자이너에 연결 하 여 디자인 타임에 사용자 지정 XAML 컨트롤 디버그

1. Visual Studio에서 솔루션 또는 프로젝트를 엽니다.

1. 솔루션/프로젝트를 빌드합니다.

1. 디버그할 사용자 지정 컨트롤이 포함 된 XAML 페이지를 엽니다.

   Windows 빌드 16299 이상을 대상으로 하는 UWP 프로젝트의 경우이 단계는 *UwpSurface* 프로세스를 시작 합니다. Windows 빌드 16299 이전의 WPF 또는 UWP 버전의 경우이 단계를 수행 하면 *xdesproc.exe* 프로세스가 시작 됩니다.

1. Visual Studio의 두 번째 인스턴스를 엽니다. 두 번째 인스턴스에서 솔루션 또는 프로젝트를 열지 마세요.

1. Visual Studio의 두 번째 인스턴스에서 **디버그** 메뉴를 열고 **프로세스에 연결 ...을**선택 합니다.

1. 프로젝트 형식 (이전 단계 참조)에 따라 사용 가능한 프로세스 목록에서 *UwpSurface* 또는 *xdesproc.exe* 프로세스를 선택 합니다.

1. **프로세스에 연결** 대화 상자의 **연결 대상** 필드에서 디버깅 하려는 사용자 지정 컨트롤에 대 한 올바른 코드 형식을 선택 합니다.

   사용자 지정 컨트롤이 .NET 언어로 작성 된 경우 **관리 (CoreCLR)** 와 같은 적절 한 .net 코드 형식을 선택 합니다. 사용자 지정 컨트롤 C++을 작성 한 경우 **네이티브**를 선택 합니다.

1. **연결** 단추를 클릭 하 여 Visual Studio의 두 번째 인스턴스를 연결 합니다.

1. Visual Studio의 두 번째 인스턴스에서 디버깅 하려는 사용자 지정 컨트롤과 연결 된 코드 파일을 엽니다. 전체 솔루션이 나 프로젝트가 아닌 파일만 열어야 합니다.

1. 이전에 열린 파일에 필요한 중단점을 추가 합니다.

1. Visual Studio의 첫 번째 인스턴스에서 디버그 하려는 사용자 지정 컨트롤 (이전 단계에서 연 페이지)이 포함 된 XAML 페이지를 닫습니다.

1. Visual Studio의 첫 번째 인스턴스에서 이전 단계에서 닫은 XAML 페이지를 엽니다. 그러면 Visual Studio의 두 번째 인스턴스에서 설정한 첫 번째 중단점에서 디버거가 중지 됩니다.

1. Visual Studio의 두 번째 인스턴스에서 코드를 디버깅 합니다.

## <a name="see-also"></a>참조
- [디버거 소개](../debugger/debugger-feature-tour.md)
- [디버거 보안](../debugger/debugger-security.md)