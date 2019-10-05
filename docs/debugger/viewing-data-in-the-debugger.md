---
title: 디버거에서 데이터의 사용자 지정 뷰 만들기 | Microsoft Docs
ms.date: 01/09/2019
ms.topic: conceptual
f1_keywords:
- vs.debug
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- debugging [Visual Studio], inspecting programs
- debugger, viewing data
ms.assetid: 13e1105f-f987-402e-9108-ec6ac12be042
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 32b3fddd13bd16ac2c846f02f54596ec846374b9
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62930001"
---
# <a name="create-custom-views-of-data-in-the-visual-studio-debugger-c-visual-basic-c"></a>Visual Studio 디버거에서 데이터의 사용자 지정 뷰 만들기 (C#, Visual Basic의 경우 C++)

[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 디버거는 검사 및 프로그램의 상태를 수정 하기 위한 다양 한 도구를 제공 합니다. 이러한 도구의 대부분은 중단 모드에서만 작동합니다.

## <a name="create-custom-views-of-data-in-variable-windows-and-datatips"></a>변수 창과 데이터 팁에서 데이터의 사용자 지정 뷰 만들기

 많은 [디버거 창](../debugger/debugger-windows.md)와 같은 **자동** 및 **조사식** 변수를 검사 하 여 windows를 허용 합니다. 사용자 지정할 수 있습니다 어떻게 C++ 형식, 관리 되는 개체 및 사용자 고유의 형식 및 디버거 변수 창에 표시 됩니다 [DataTips](../debugger/view-data-values-in-data-tips-in-the-code-editor.md)합니다. 자세한 내용은 [의 사용자 지정 뷰 만들기 C++ 개체](../debugger/create-custom-views-of-native-objects.md) 하 고 [개체의 사용자 지정 뷰 만들기](../debugger/create-custom-views-of-dot-managed-objects.md)합니다.

## <a name="create-custom-visualizers"></a>사용자 지정 시각화 도우미 만들기

 시각화 도우미를 사용 하는 의미 있는 방식으로 개체 또는 변수 내용을 볼 수 있습니다. Visual Studio 디버거 시각화 도우미 돋보기 단추를 사용 하 여 열 수 있는 다른 windows 가리킵니다 ![VisualizerIcon](../debugger/media/dbg-tips-visualizer-icon.png "시각화 아이콘") 아이콘입니다. 예를 들어 HTML 시각화 도우미를 HTML 문자열로 해석 및 브라우저에 표시 하는 방법을 보여 줍니다. DataTips에서 시각화 도우미에 액세스할 수 합니다 **조사식** 창 합니다 **자동** 창 및 **지역** 창. 합니다 **간략 한 조사식** 대화 상자는 또한 시각화 도우미를 제공 합니다. 자세한 내용은 [사용자 지정 시각화 도우미 만들기](../debugger/create-custom-visualizers-of-data.md)를 참조하세요.

## <a name="see-also"></a>참고자료

- [디버거 소개](../debugger/debugger-feature-tour.md)
- [명령 창](../ide/reference/command-window.md)
- [디버거 보안](../debugger/debugger-security.md)