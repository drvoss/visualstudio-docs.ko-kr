---
title: '방법: 사용 하도록 설정 하 고 편집 하며 계속 하기를 사용 하지 않도록 설정 | Microsoft Docs'
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
ms.openlocfilehash: 3bee60a54576ab816c63cf60f2226ebbbaf50c44
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63388479"
---
# <a name="how-to-enable-and-disable-edit-and-continue-c-vb-c"></a>방법: 사용 하도록 설정 하 고 편집 하며 계속 하기를 사용 하지 않도록 설정 (C#, VB, C++)

사용 하지 않도록 설정 하거나 활성화할 수 있습니다 **편집 하며 계속 하기** Visual studio에서 **옵션** 디자인 타임에 대화 상자. **편집하며 계속하기**는 디버그 빌드에서만 작동합니다. 자세한 내용은 [편집하며 계속하기](../debugger/edit-and-continue.md)를 참조하세요.

네이티브 C++를 **편집 하며 계속 하기** 사용 해야 합니다 `/INCREMENTAL` 옵션입니다. 기능 요구 사항에 대 한 자세한 내용은 C++를 참조 하세요 [블로그 게시물](https://devblogs.microsoft.com/cppblog/c-edit-and-continue-in-visual-studio-2015-update-3/) 및 [편집 하며 계속 하기 (Visual C++)](../debugger/edit-and-continue-visual-cpp.md).

**편집 하며 계속 하기를 사용할지 설정 합니다.**

1. 디버깅 세션의 경우 디버깅을 중지 (**디버깅할** > **디버깅 중지** 하거나 **Shift**+**F5**) .

1. **도구가** > **옵션** > (또는 **디버그** > **옵션**) > **디버깅**  >  **일반**선택 **편집 하며 계속 하기** 오른쪽 창에서.

    > [!NOTE]
    > IntelliTrace를 사용하도록 설정되어 있고 IntelliTrace 이벤트 및 호출 정보를 모두 수집하는 경우 편집하며 계속하기를 사용하지 않도록 설정됩니다. 자세한 내용은 [IntelliTrace](../debugger/intellitrace.md)합니다.

1. 에 대 한 C++ 코드, 반드시 **네이티브 편집 하며 계속 하기** 선택 하 고 추가 옵션을 설정 합니다.
    - **계속할 때 변경 내용 적용(네이티브 전용)**

      선택 하면 Visual Studio 자동으로 컴파일하고 중단 상태에서 디버깅을 계속 하면 코드 변경 내용을 적용 합니다. 그렇지 않은 경우 사용 하 여 변경 내용을 적용 하도록 선택할 수 있습니다 **디버깅할** > **코드 변경 내용 적용**합니다.

    - **부실 코드 경고(네이티브 전용)**

      선택 하 고, 부실 코드 경고를 제공 합니다.

1. **확인**을 클릭합니다.
