---
title: 디자인 타임에 디버그 | Microsoft Docs
ms.custom: seodec18
ms.date: 11/21/2018
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
ms.openlocfilehash: 82e82a75ce5ecff8e9b7e6d0b6aaf2e29728fc45
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62901061"
---
# <a name="debug-at-design-time-in-visual-studio-c-c-visual-basic-f"></a>Visual Studio에서 디자인 타임에 디버그 (C#, C++, Visual Basic의 경우 F#)

실행 중인 앱 하는 동안 대신 디자인 타임에 코드를 디버그 하려면, 사용할 수는 **직접 실행** 창입니다.

XAML 코드 숨김 데이터 바인딩 코드와 같은 XAML 디자이너에서 앱을 디버그 하려면 사용할 수 있습니다 **디버깅할** > **프로세스에 연결**합니다.

## <a name="use-the-immediate-window"></a>직접 실행 창 사용

Visual Studio를 사용할 수 있습니다 **직접 실행** 앱을 실행 하지 않고 함수 또는 서브루틴을 실행 하는 창입니다. 함수 또는 서브루틴에 중단점이 있으면 Visual Studio가 중단점에서 중단 됩니다. 그런 다음 디버거 창을 사용하여 프로그램 상태를 조사할 수 있습니다. 이 기능은 이라고 *디자인 타임에 디버깅*합니다.

다음 예제에서는 Visual Basic의 경우 사용할 수도 있습니다는 **직접 실행** 창에서 디자인 타임에 C#, F#, 및 C++ 앱.

1. 새 Visual Basic 콘솔 응용 프로그램에 다음 코드를 붙여 넣습니다.

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

1. 줄에 중단점을 설정할 **End 함수**합니다.

1. 엽니다는 **직접 실행** 선택 하 여 창 **디버그** > **Windows** > **직접 실행**합니다. 형식 `?MyFunction` 창에 다음 키를 누릅니다 **Enter**합니다.

   중단점이 적중, 및의 값 **MyFunction** 에 **지역** 기간은 **1**합니다. 앱이 중단 모드에 있는 동안 호출 스택 창 및 기타 디버깅을 검사할 수 있습니다.

1. 선택 **계속** Visual Studio 도구 모음에서 합니다. 앱이 종료 및 **1** 반환 되는 **직접 실행** 창입니다. 디자인 모드에 있는지 확인 합니다.

1. 형식 `?MyFunction` 에 **즉시** 창을 다시 누릅니다 **Enter**합니다. 중단점이 적중, 및의 값 **MyFunction** 에 **지역** 기간은 **2**합니다.

1. 선택 하지 않고 **계속**, 형식 `?MySub()` 에 **직접 실행** 창과 누릅니다 **Enter**합니다. 중단점이 적중, 및의 값 **MyFunction** 에 **지역** 기간은 **3**합니다. 앱이 중단 모드에 있는 동안 앱 상태를 검사할 수 있습니다.

1. 선택 **계속**합니다. 중단점이 다시 적중 및 값 **MyFunction** 에 **지역** 창이 **2**합니다. 합니다 **직접 실행** 창에 반환 **식을 평가한 및 값이 없는**합니다.

1. 선택 **계속** 다시 합니다. 앱이 종료 및 **2** 반환 되는 **직접 실행** 창입니다. 디자인 모드에 있는지 확인 합니다.

1. 내용을 지울 합니다 **직접 실행** 창에서 선택 창에서 마우스 오른쪽 단추로 클릭 **모두 지우기**합니다.

## <a name="attach-to-an-app-from-the-xaml-designer"></a>XAML 디자이너에서 앱에 연결

일부 선언적 데이터 바인딩 시나리오에서 XAML 디자이너에서 코드 숨김 디버그에 도움이 됩니다.

1. Visual Studio 프로젝트를 추가 하는 새 XAML 페이지와 같은 *temp.xaml*합니다. 새 XAML 페이지를 비워 둡니다.

1. 솔루션을 빌드합니다.

1. 오픈 *temp.xaml*, XAML 디자이너를 로드 하는 *XDesProc.exe*, 또는 *UwpSurface.exe* UWP 앱에서.

1. 새 Visual Studio 인스턴스를 엽니다. 새 인스턴스를 선택 **디버깅할** > **프로세스에 연결**합니다.

1. 에 **프로세스에 연결** 대화 상자에서 디자이너에서 처리할 합니다 **사용 가능한 프로세스** 목록입니다.

   UWP 용 Windows를 대상으로 하는 프로젝트 빌드 16299 또는 디자이너 프로세스는 위의 *UwpSurface.exe*합니다. 16299 이전의 버전의 WPF 또는 UWP, 디자이너 과정이 *XDesProc.exe*합니다.

1. 있는지 확인 합니다 **연결할** 필드와 같은.NET 버전에 올바른 코드 형식으로 설정 됩니다 **관리 코드 (CoreCLR)** 합니다.

1. 선택 **연결**합니다.

1. 프로세스에 연결 하는 동안 다른 Visual Studio 인스턴스로 전환 및 앱의 코드를 디버그 하려면 중단점을 설정 합니다.

   예를 들어 디자인 타임에 TextBlock을 바인딩하는 다음 XAML에 대 한 형식 변환기 코드에 중단점을 설정할 수 있습니다.

    ```xaml
    <TextBlock Text="{Binding title, ConverterParameter=lower, Converter={StaticResource StringFormatConverter}, Mode=TwoWay}"  />
    ```

   페이지 로드 되 면 중단점이 적중 됩니다.

## <a name="see-also"></a>참고자료
- [디버거 소개](../debugger/debugger-feature-tour.md)
- [디버거 보안](../debugger/debugger-security.md)