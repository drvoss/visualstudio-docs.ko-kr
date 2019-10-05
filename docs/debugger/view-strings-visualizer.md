---
title: 문자열 시각화 도우미에서 문자열을 보기 | Microsoft Docs
ms.date: 04/08/2019
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JavaScript
helpviewer_keywords:
- string visualizer
- visualizers, string
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ffd19dccb69d3ae05a84ae49a280ff49c14f2809
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62930235"
---
# <a name="view-strings-in-a-string-visualizer-in-visual-studio"></a>Visual Studio에서 문자열 시각화 도우미에서 문자열 보기

Visual Studio에서 디버깅 하는 동안에 기본 제공 문자열 시각화 도우미를 사용 하 여 문자열을 볼 수 있습니다. 문자열 시각화 도우미 데이터 팁 또는 디버거 창에 대해 너무 긴 문자열을 보여 줍니다. 또한 도움이 될 수 있습니다 잘못 된 형식의 문자열을 식별 합니다.

기본 제공 문자열 시각화 도우미에서는 일반 텍스트, XML, HTML 및 JSON 포함 옵션입니다. 와 같은 몇 가지에 대 한 기본 제공 시각화 도우미를 열 수도 있습니다 [DataSet, DataTable 및 DataView](../debugger/dataset-visualizer-dialog-box.md) 개체에서 합니다 **자동** 또는 기타 디버거 창입니다.

> [!NOTE]
> 시각화 도우미에서 XAML 또는 WPF UI 요소를 검사 해야 할 경우 참조 또는 [디버깅 하는 동안 검사할 XAML 속성](../debugger/inspect-xaml-properties-while-debugging.md) 하거나 [WPF 트리 시각화 도우미를 사용 하는 방법을](../debugger/how-to-use-the-wpf-tree-visualizer.md)합니다.

## <a name="open-a-string-visualizer"></a>문자열 시각화 도우미를 열려면

문자열 시각화 도우미를 열려면 디버깅 하는 동안 있습니다 일시 중지 해야 합니다. 일반 텍스트, XML, HTML 또는 JSON 돋보기 아이콘을 선택한 되는 문자열 값이 있는 변수 위로 마우스를 가져가고 ![VisualizerIcon](../debugger/media/dbg-tips-visualizer-icon.png "시각화 아이콘")합니다.

![문자열 시각화 도우미를 열려면](../debugger/media/dbg-tips-string-visualizers.png "열기 문자열 시각화 도우미")

## <a name="view-string-visualizer-data"></a>문자열 시각화 도우미 데이터 보기

문자열 시각화 도우미 창에서 합니다 **식** 변수나 식을 마우스로 가리키면 하는 필드 표시 및 **값** 필드는 문자열 값을 보여 줍니다.

Blank **값** 선택한 시각화 도우미는 문자열을 인식할 수 없습니다 것을 의미 합니다. 예를 들어 합니다 **XML 시각화 도우미** 는 빈 값을 보여 줍니다 **값** 없는 XML 태그를 사용 하 여 텍스트 문자열 또는 JSON 문자열에 대 한 합니다.

인식할 수 없습니다. 선택한 시각화 도우미는 문자열을 보려면 선택 합니다 **텍스트 시각화 도우미**합니다. 합니다 **텍스트 시각화 도우미** 일반 텍스트를 보여 줍니다.

### <a name="view-json-string-data"></a>JSON 문자열 데이터 보기

올바른 형식의 JSON 문자열의 JSON 시각화 도우미에서 다음 그림과 유사합니다. 잘못 된 형식의 JSON 오류 아이콘 (또는 빈 인식할 수 없는 경우)에 표시 될 수 있습니다. JSON 오류를 식별 하려면 복사와 같은 JSON linting 도구에 문자열을 붙여 넣습니다 [JSLint](https://www.jslint.com/)합니다.

![JSON 문자열 시각화 도우미](../debugger/media/dbg-tips-string-visualizer-json.png "JSON 문자열 시각화 도우미")

### <a name="view-xml-string-data"></a>XML 문자열 데이터 보기

올바른 형식의 XML 문자열로 XML 시각화 도우미에서 다음 그림과 유사합니다. 잘못 된 XML은 인식할 수 없는 경우 빈 XML 태그 없이 표시할 수 있습니다.

![XML 문자열 시각화 도우미](../debugger/media/dbg-string-visualizers-xml.png "XML 문자열 시각화 도우미")

### <a name="view-html-string-data"></a>문자열 데이터를 HTML 보기

올바른 형식의 HTML 문자열로 표시 됩니다. 다음 그림에 표시 된 것과 같이 브라우저에서 렌더링 하는 경우. 잘못 된 HTML은 일반 텍스트로 표시할 수 있습니다.

![HTML 문자열 시각화 도우미](../debugger/media/dbg-string-visualizers-html.png "HTML 문자열 시각화 도우미")

## <a name="see-also"></a>참고자료

- [사용자 지정 시각화 도우미 (C#, Visual Basic) 만들기](../debugger/create-custom-visualizers-of-data.md)
- [Mac 용 Visual Studio에서 데이터 시각화](/visualstudio/mac/data-visualizations)