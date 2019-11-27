---
title: '방법: 시각화 도우미 설치 | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- debugger, visualizers
- visualizers, installing
ms.assetid: 3310ef43-515c-4d97-b0f9-51047247d3da
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1df72c6978f5ab34a86c74dbc1ea349db5aa4457
ms.sourcegitcommit: b5cb0eb09369677514ee1f44d5d7050d34c7fbc1
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/26/2019
ms.locfileid: "74491312"
---
# <a name="how-to-install-a-visualizer"></a>방법: 시각화 도우미 설치
시각화 도우미를 만든 후에는 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]에서 사용할 수 있도록 이 시각화 도우미를 설치해야 합니다. 시각화 도우미를 설치하는 과정은 간단합니다.

> [!NOTE]
> UWP 앱에서는 표준 텍스트, HTML, XML 및 JSON 시각화 도우미만 지원 됩니다. 사용자가 만든 사용자 지정 시각화 도우미는 지원되지 않습니다.

### <a name="to-install-a-visualizer-for-visual-studio-2019"></a>Visual Studio 2019에 대 한 시각화 도우미를 설치 하려면
  
1. 빌드한 시각화 도우미가 들어 있는 DLL을 찾습니다.

2. 다음 위치 중 하나에 [디버거 쪽](create-custom-visualizers-of-data.md#to-create-the-debugger-side) DLL을 복사 합니다.

    - *VisualStudioInstallPath* `\Common7\Packages\Debugger\Visualizers`

    - `My Documents\` *VisualStudioVersion* `\Visualizers`
    
3. 다음 위치 중 하나에 [디버기 쪽](create-custom-visualizers-of-data.md#to-create-the-debuggee-side) DLL을 복사 합니다.

    - *VisualStudioInstallPath* `\Common7\Packages\Debugger\Visualizers\` *프레임 워크*

    - `My Documents\` *VisualStudioVersion* `\Visualizers\` *Framework*

    여기서 *프레임 워크* 는 다음 중 하나입니다.
    - `.NET Framework` 런타임을 실행 중인 디버기에 대 한 `net2.0`입니다.
    - `netstandard 2.0` (`.NET Framework v4.6.1+` 또는 `.NET Core 2.0+`)를 지 원하는 런타임을 사용 하 여 디버기에 대 한 `netstandard2.0` 합니다.
    - `.NET Core` 런타임을 실행 중인 디버기에 대 한 `netcoreapp`입니다. (`.NET Core 2.0+`지원)

4. 디버깅 세션을 다시 시작합니다.

### <a name="to-install-a-visualizer-for-visual-studio-2017-and-older"></a>Visual Studio 2017 및 이전 버전에 대 한 시각화 도우미를 설치 하려면

> [!IMPORTANT]
> .NET Framework 시각화 도우미가 Visual Studio 2017 이상에서 지원 됩니다.

1. 빌드한 시각화 도우미가 들어 있는 DLL을 찾습니다.

2. 이 DLL을 다음 위치 중 한 곳에 복사합니다.

    - *VisualStudioInstallPath* `\Common7\Packages\Debugger\Visualizers`

    - `My Documents\` *VisualStudioVersion* `\Visualizers`

3. 디버깅 세션을 다시 시작합니다.

> [!NOTE]
> 원격 디버깅에 관리되는 시각화 도우미를 사용하려면 원격 컴퓨터의 동일한 경로에 DLL을 복사합니다.

## <a name="see-also"></a>참고 항목
- [Create Custom Visualizers of Data](../debugger/create-custom-visualizers-of-data.md)(데이터의 사용자 지정 시각화 도우미 만들기)
- [방법: 시각화 도우미 작성](create-custom-visualizers-of-data.md)
