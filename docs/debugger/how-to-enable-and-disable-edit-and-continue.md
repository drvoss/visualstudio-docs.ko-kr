---
title: '방법: 편집 하며 계속 하기 사용 및 사용 안 함 | Microsoft Docs'
ms.custom: seodec18
ms.date: 10/04/2018
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- /INCREMENTAL linker option
- Apply Code Changes command
- Edit and Continue, disabling
- code changes, applying in break mode
- INCREMENTAL linker option
- Edit and Continue, enabling
- break mode, applying code changes
- Edit and Continue, applying code changes
- Step command
- Go command
ms.assetid: fd961a1c-76fa-420d-ad8f-c1a6c003b0db
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
- cplusplus
ms.openlocfilehash: 2c8486bdcd7bc737d3851eabd88734df4efd80b7
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72430528"
---
# <a name="how-to-enable-and-disable-edit-and-continue-c-vb-c"></a>방법: 편집 하며 계속 하기 사용 및 사용 안C#함 (, C++VB,)

디자인 타임에 Visual Studio **옵션** 대화 상자에서 **편집 하며 계속 하기** 를 사용 하지 않도록 설정 하거나 사용 하도록 설정할 수 있습니다. **편집하며 계속하기**는 디버그 빌드에서만 작동합니다. 자세한 내용은 [편집하며 계속하기](../debugger/edit-and-continue.md)를 참조하세요.

Native C++의 경우 **편집 하며 계속 하기** 를 사용 하려면 `/INCREMENTAL` 옵션을 사용 해야 합니다. 의 C++기능 요구 사항에 대 한 자세한 내용은이 [블로그 게시물](https://devblogs.microsoft.com/cppblog/c-edit-and-continue-in-visual-studio-2015-update-3/) 및 [편집 하며 계속 하기C++() (영문)](../debugger/edit-and-continue-visual-cpp.md)를 참조 하세요.

**편집 하며 계속 하기를 사용 하거나 사용 하지 않도록 설정 하려면:**

1. 디버깅 세션을 진행 하는 경우 디버깅을 중지 합니다 (**디버그**  > **디버깅 중지** **또는** F5 +**F5**).

1. **도구**  > **옵션** > (또는 **디버그**  > **옵션**) > **디버깅**  > **일반**에서 오른쪽 창에 있는 **편집 하며 계속 하기** 를 선택 합니다.

    > [!NOTE]
    > IntelliTrace를 사용하도록 설정되어 있고 IntelliTrace 이벤트 및 호출 정보를 모두 수집하는 경우 편집하며 계속하기를 사용하지 않도록 설정됩니다. 자세한 내용은 [IntelliTrace](../debugger/intellitrace.md)를 참조 하세요.

1. 코드 C++ 의 경우 **네이티브 편집 하며 계속 하기 사용** 이 선택 되어 있는지 확인 하 고 추가 옵션을 설정 합니다.
    - **계속할 때 변경 내용 적용(네이티브 전용)**

      이 확인란이 선택 되어 있으면 중단 상태에서 디버깅을 계속할 때 Visual Studio에서 코드 변경을 자동으로 컴파일하고 적용 합니다. 그렇지 않으면 **디버그**  > **코드 변경 내용을 적용**하 여 변경 내용을 적용 하도록 선택할 수 있습니다.

    - **부실 코드 경고(네이티브 전용)**

      이 옵션이 선택 되 면 부실 코드에 대 한 경고를 표시 합니다.

1. **확인**을 클릭합니다.
