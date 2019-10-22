---
title: 문자열 시각화 도우미 대화 상자 | Microsoft Docs
ms.date: 10/10/2018
ms.custom: seoapril2019
ms.topic: reference
f1_keywords:
- vs.debug.stringviewer
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JavaScript
helpviewer_keywords:
- string visualizer
- visualizers, string
ms.assetid: 080fd8f1-72b0-461f-8451-3c84d5dc51df
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 10e7e50ffc0cb61bd036bef65c554e8147eecc09
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72430826"
---
# <a name="string-visualizer-dialog-box"></a>문자열 시각화 도우미 대화 상자

Visual Studio에서 디버깅 하는 동안 기본 제공 문자열 시각화 도우미를 사용 하 여 문자열을 볼 수 있습니다. 문자열 시각화 도우미는 데이터 팁 또는 디버거 창에 너무 긴 문자열을 보여 줍니다. 또한 형식이 잘못 된 문자열을 식별 하는 데 도움이 될 수 있습니다.

기본 제공 문자열 시각화 도우미에는 일반 텍스트, XML, HTML 및 JSON 옵션이 포함 되어 있습니다. **자동** 또는 다른 디버거 창에서 [DataSet, DataTable 및 DataView](../debugger/dataset-visualizer-dialog-box.md) 개체와 같은 몇 가지 다른 형식에 대 한 기본 제공 시각화 도우미를 열 수도 있습니다.

> [!NOTE]
> 시각화 도우미에서 XAML 또는 WPF UI 요소를 검사 해야 하는 경우 [디버깅 하는 동안](../xaml-tools/inspect-xaml-properties-while-debugging.md) 또는 [wpf 트리 시각화 도우미를 사용](../debugger/how-to-use-the-wpf-tree-visualizer.md)하는 방법을 참조 하거나 xaml 속성을 검사 합니다.

문자열 시각화 도우미를 열려면 디버깅 중에 일시 중지 해야 합니다. 일반 텍스트, XML, HTML 또는 JSON 문자열 값을 포함 하는 변수를 마우스로 가리키고 돋보기 아이콘 ![VisualizerIcon](../debugger/media/dbg-tips-visualizer-icon.png "시각화 도우미 아이콘")을 선택 합니다.

## <a name="uielement-list"></a>UI 요소 목록

**식** 필드를 가리키면 변수나 식이 표시 됩니다.

**값** 필드는 문자열 값을 표시 합니다. 빈 **값** 은 선택한 시각화 도우미가 문자열을 인식할 수 없음을 의미 합니다. 예를 들어 **Xml 시각화 도우미** 는 xml 태그가 없는 텍스트 문자열이 나 JSON 문자열에 대 한 빈 **값** 을 보여 줍니다. 선택한 시각화 도우미가 인식할 수 없는 문자열을 보려면 **텍스트 시각화 도우미** 를 대신 선택 합니다. **텍스트 시각화 도우미** 는 일반 텍스트를 표시 합니다.

### <a name="json-string-data"></a>JSON 문자열 데이터

올바른 형식의 JSON 문자열은 JSON 시각화 도우미의 다음 그림과 유사 하 게 표시 됩니다. JSON 형식이 잘못 되 면 오류 아이콘이 표시 될 수 있습니다 (또는 인식할 수 없는 경우 공백). JSON 오류를 식별 하려면 문자열을 복사 하 여 [JSLint](https://www.jslint.com/)와 같은 json lint 도구에 붙여넣습니다.

![JSON 문자열 시각화 도우미](../debugger/media/dbg-tips-string-visualizer-json.png "JSON 문자열 시각화 도우미")

### <a name="xml-string-data"></a>XML 문자열 데이터

올바른 형식의 XML 문자열은 XML 시각화 도우미의 다음 그림과 유사 하 게 표시 됩니다. XML 태그 없이 형식이 잘못 된 XML이 표시 되거나 인식할 수 없는 경우 비어 있습니다.

![XML 문자열 시각화 도우미](../debugger/media/dbg-string-visualizers-xml.png "XML 문자열 시각화 도우미")

### <a name="html-string-data"></a>HTML 문자열 데이터

올바른 형식의 HTML 문자열은 다음 그림과 같이 브라우저에서 렌더링 된 것 처럼 나타납니다. 형식이 잘못 된 HTML은 일반 텍스트로 표시 될 수 있습니다.

![HTML 문자열 시각화 도우미](../debugger/media/dbg-string-visualizers-html.png "HTML 문자열 시각화 도우미")

## <a name="see-also"></a>참조

- [사용자 지정 시각화 도우미C#만들기 (, Visual Basic)](../debugger/create-custom-visualizers-of-data.md)
- [Mac용 Visual Studio의 데이터 시각화](/visualstudio/mac/data-visualizations)