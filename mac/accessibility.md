---
title: 접근성
description: 이 문서에서는 Mac용 Visual Studio의 액세스 가능성 기능과 사용하도록 설정하는 방법을 소개합니다.
author: conceptdev
ms.author: crdun
ms.date: 04/17/2019
ms.assetid: 2C4AAC2E-3B4A-4496-8BE0-1F5A7F81D1CA
ms.openlocfilehash: 13b8d40a6ab31d7178e95a3896afa1c85c804f6c
ms.sourcegitcommit: a124076dfd6b4e5aecda4d01984fee7b0c034745
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2019
ms.locfileid: "68787638"
---
# <a name="accessibility"></a>접근성

Mac용 Visual Studio에는 다음 내게 필요한 옵션 기능이 포함되어 있어서 다른 능력을 가진 사용자도 더욱 쉽게 액세스할 수 있습니다.

- Solution Pad 및 Editor Pad의 텍스트 확대
- 편집기의 텍스트 크기 옵션
- 편집기의 색 사용자 지정
- 키보드 탐색
- 바로 가기 사용자 지정
- 메서드 및 매개 변수의 코드 완성

Apple에서는 이 기능 외에도 VoiceOver 및 받아쓰기와 같은 특별한 요구 사항을 가진 사용자를 지원하는 다양한 도구를 제공합니다.

macOS의 내게 필요한 옵션 기능에 대한 자세한 내용은 [Apple 웹 사이트](https://www.apple.com/accessibility/mac/)를 참조하세요.

## <a name="enabling-macos-assistive-technologies-in-visual-studio-for-mac"></a>Mac용 Visual Studio에서 macOS 보조 기술 사용

Mac용 Visual Studio의 macOS 보조 기술 지원은 기본적으로 꺼집니다. 사용하도록 설정하려면 다음 단계를 수행합니다.

1. **Visual Studio(메뉴) > 기본 설정 > 기타 > 내게 필요한 옵션**으로 이동합니다.

2. **내게 필요한 옵션 사용** 확인란을 선택합니다.

   ![기본 설정 내게 필요한 옵션 확인란](media/accessibility-preferences.png)

3. **Visual Studio 다시 시작** 단추를 선택하여 Visual Studio를 다시 시작하고 Apple의 보조 기술 지원을 사용하도록 설정합니다.

## <a name="how-to-use-keyboard-navigation"></a>방법: 키보드 탐색 사용

키보드 탐색 지원은 macOS에 바로 기본 제공되지만, 가장 포괄적인 환경을 포함하려면 **모든 컨트롤**을 탐색하도록 macOS를 설정해야 합니다.

![시스템 기본 설정 키보드 모든 컨트롤](media/accessibility-preferences-keyboard.png)

**전체 키보드 액세스**를 **모든 컨트롤**로 설정하면 창이나 대화 상자에서 모든 컨트롤을 탐색할 수 있습니다. 그런 후 다음을 사용하여 컨트롤을 선택할 수 있습니다.

- Tab 키: 컨트롤을 따라 앞으로 이동
- Shift+Tab: 컨트롤을 따라 뒤로 이동
- 화살표 키: 화살표 방향으로 컨트롤 간 이동
- Ctrl+Tab: 텍스트 영역 상자 밖으로 이동
- 스페이스바를 누르면 현재 포커스가 있는 컨트롤이 활성화됩니다.

## <a name="how-to-enable-and-use-voiceover"></a>방법: VoiceOver 활성화 및 사용

VoiceOver를 사용하거나 사용하지 않도록 설정하려면 **&#8984;+F5**를 누릅니다.

VoiceOver 명령은 이 가이드에서 **VO+_키_** 로 나타납니다. 여기서 **VO**는 **VoiceOver 유틸리티** 애플리케이션에 설정된 한정자를 나타냅니다. 기본 한정자는 **Ctrl+Alt**입니다. 예를 들어 VoiceOver 한정자에 따라 **VO+M**은 **Ctrl+Alt+M**을 의미합니다. 간단하게 커서 키를 **왼쪽** 및 **오른쪽** 등으로 나타내기도 합니다.

Mac용 Visual Studio 사용자 인터페이스를 탐색하려면 다음 키 조합을 사용합니다.

- **VO+오른쪽/왼쪽**: 사용자 인터페이스 요소 간 탐색
  - VoiceOver는 컨트롤의 레이블 및 유형을 알리고 컨트롤을 조작하는 방법을 설명합니다.
- **VO+Shift+아래쪽/위쪽**: 요소에 들어가거나 요소에서 나갑니다.
  - 요소 내부에 있으면 **VO+왼쪽/오른쪽**을 사용하여 해당 요소 내에 있는 여러 요소를 탐색할 수 있습니다.
- **VO+스페이스바**: 컨트롤을 선택/조작합니다.
- **VO+M**: Mac용 Visual Studio 메뉴 모음을 조작합니다.

VoiceOver 사용에 대한 자세한 내용과 전체 명령 목록을 보려면 다음 가이드를 참조하세요.

- [Apple VoiceOver 시작 가이드](https://support.apple.com/en-us/guide/voiceover-guide/welcome/web)
- [macOS의 VoiceOver 명령](http://lab.dotjay.com/notes/voiceover-commands/)

## <a name="see-also"></a>참고 항목

- [Visual Studio의 액세스 가능성 기능(Windows에서)](/visualstudio/ide/reference/accessibility-features-of-visual-studio)
