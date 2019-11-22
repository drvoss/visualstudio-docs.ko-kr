---
title: '2단계: 프로그램 실행 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 9a8fe90e-c97b-4e98-b6c8-0c6b3962c49d
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ef28781252181dbf765db52dbe6fed1b286516b2
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74295769"
---
# <a name="step-2-run-your-program"></a>2단계: 프로그램 실행
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

새 솔루션을 만들면서 실행되는 프로그램을 실제로 빌드했습니다. 이 프로그램은 아직 많은 작업을 수행하지 않고 단순히 제목 표시줄에 **Form1**이 표시된 빈 창만 표시하지만 실행되고 있는 프로그램이 맞습니다.

 ![link to video](../data-tools/media/playvideo.gif "PlayVideo")For a video version of this topic, see [Tutorial 1: Create a Picture Viewer in Visual Basic - Video 1](https://go.microsoft.com/fwlink/?LinkId=205209) or [Tutorial 1: Create a Picture Viewer in C# - Video 1](https://go.microsoft.com/fwlink/?LinkId=205199). 이러한 비디오에서는 이전 버전의 Visual Studio를 사용하므로 일부 메뉴 명령과 기타 사용자 인터페이스 요소가 약간 다를 수 있습니다. 그러나 개념 및 절차는 Visual Studio의 현재 버전에서 비슷하게 작동합니다.

### <a name="to-run-your-program"></a>프로그램을 실행하려면

1. 다음 메서드 중 하나를 사용해서 프로그램을 실행합니다.

    - **F5** 키를 선택합니다.

    - 메뉴 모음에서 **디버그**, **디버깅 시작**을 차례로 선택합니다.

    - 도구 모음에서 **디버깅 시작** 단추를 선택하면 다음과 같이 표시됩니다.

         ![Start Debugging toolbar button](../ide/media/express-icondebug.png "Express_IconDebug") Start Debugging toolbar button

2. Visual Studio에서 프로그램이 실행되고 **Form1** 창이 표시됩니다. 다음 그림에서는 방금 빌드한 프로그램을 보여 줍니다. 이 프로그램은 현재 실행 중이며, 더 많은 기능이 추가될 예정입니다.

     ![Windows Form application program running](../ide/media/express-firstrun.png "Express_FirstRun") Windows Form Application program running

3. Visual Studio IDE(통합 개발 환경)으로 돌아가서 새 도구 모음을 살펴봅니다. 프로그램을 실행하면 추가 단추가 도구 모음에 나타납니다. 이러한 단추를 사용하면 프로그램 중지 및 시작과 같은 작업을 수행할 수 있으며 발생할 수 있는 모든 오류(버그)를 추적할 수 있습니다. 이 예제에서는 프로그램을 시작하고 중지하는 데에만 이를 사용하도록 합니다.

     ![Debugging toolbar](../ide/media/express-debugtoolbar.png "Express_DebugToolbar") Debugging toolbar

4. 다음 메서드 중 하나를 사용해서 프로그램을 중지합니다.

    - 도구 모음에서 **디버깅 중지** 단추를 선택합니다.

    - 메뉴 모음에서 **디버그**, **디버깅 중지**를 차례로 선택합니다.

    - **Form1** 창의 위쪽 모퉁이에 있는 X 단추를 선택합니다.

    > [!NOTE]
    > IDE 안에서 프로그램을 실행할 때는 주로 프로그램에서 버그(오류)를 찾고 수정하는 작업을 수행하기 때문에 IDE 안에서 프로그램을 실행하는 것을 *디버깅*이라고 합니다. 이 프로그램은 크기가 작고 아직 아무것도 실제로 수행하지는 않지만 마찬가지로 실제 프로그램입니다. 다른 프로그램도 동일한 절차에 따라 실행하고 디버깅합니다. 디버깅에 대한 자세한 내용은 [디버거 기본 사항](../debugger/debugger-basics.md)을 참조하세요.

### <a name="to-continue-or-review"></a>계속하거나 검토하려면

- 다음 자습서 단계로 이동하려면 [3단계: 폼 속성 설정](../ide/step-3-set-your-form-properties.md)을 참조하세요.

- 이전 자습서 단계로 돌아가려면 [1단계: Windows Forms 애플리케이션 프로젝트 만들기](../ide/step-1-create-a-windows-forms-application-project.md)를 참조하세요.
