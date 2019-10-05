---
title: 내보내기 및 코드 맵을 저장 합니다.
ms.date: 05/16/2018
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 70c4cd238b6e5d31eced6a35ff0c7d24ab85a280
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63003123"
---
# <a name="share-code-maps"></a>코드 맵 공유

코드 맵을 Visual Studio 프로젝트의 일환으로, 이미지 또는 XPS 파일에 저장할 수 있습니다.

## <a name="share-a-code-map-with-other-visual-studio-users"></a>다른 Visual Studio 사용자를 사용 하 여 코드 맵 공유

**파일** 메뉴를 사용하여 맵을 저장합니다.

-또는-

맵 도구 모음에서 특정 프로젝트의 일부로 맵을 저장 하려면 **공유** > **이동 \<CodeMapName >에.dgml**를 선택한 다음 저장 하려는 프로젝트는 맵입니다.

![맵을 다른 프로젝트로 이동](../modeling/media/codemapsmovemapmenu.png)

Visual Studio로 map에 저장 된 *.dgml* Visual Studio Enterprise 및 Visual Studio Professional의 다른 사용자와 공유할 수 있는 파일입니다.

> [!NOTE]
> Visual Studio Professional 사용자와 맵을 공유하기 전에 모든 그룹을 확장하고, 숨겨진 노드와 그룹 간 링크를 표시하고, 삭제된 노드 중 다른 작업자가 맵 상에서 볼 수 있도록 하려는 노드를 검색합니다. 그렇지 않으면 다른 사용자가 이러한 항목을 볼 수 없습니다.
>
> 모델링 프로젝트에 있거나 모델링 프로젝트에서 다른 위치로 복사된 맵을 저장할 때 다음 오류가 발생할 수 있습니다.
>
> "프로젝트 디렉터리 외부에 *fileName* 을 저장할 수 없습니다. 연결된 항목이 지원되지 않습니다."
>
> Visual Studio에서 오류가 표시되지만 저장된 버전이 만들어집니다. 이 오류가 발생하지 않게 하려면 모델링 프로젝트 외부에 맵을 만듭니다. 그런 다음 원하는 위치에 그래프를 저장할 수 있습니다. 파일을 솔루션의 다른 위치에 복사하고 저장해 보는 것으로는 문제가 해결되지 않습니다.

## <a name="export-a-code-map-as-an-image"></a>코드 맵을 이미지로 내보내기

코드 맵을 이미지로 내보내면 Microsoft Word 나 PowerPoint 같이 다른 응용 프로그램으로 복사할 수 있습니다.

1. 코드 맵 도구 모음에서 선택 **공유** > **이미지로 메일 보내기** 하거나 **이미지 복사**합니다.

2. 이미지를 다른 애플리케이션에 붙여넣습니다.

## <a name="export-the-map-as-an-xps-file"></a>맵을 XPS 파일로 내보내기

코드 맵을 XPS 파일로 내보내면 Internet Explorer 같이 XML 또는 XAML 뷰어에서 볼 수 있습니다.

1. 코드 맵 도구 모음에서 선택 **공유** > **이식 가능한 XPS로 전자 메일** 하거나 **이식 가능한 XPS로 저장**합니다.

2. 파일을 저장할 위치를 찾습니다.

3. 코드 맵 이름을 지정합니다. 있는지 확인 합니다 **형식으로 저장** 로 설정한 **XPS 파일 (\*.xps)** 합니다. **저장**을 선택합니다.

## <a name="see-also"></a>참고자료

- [코드 맵 사용 하 여 종속성 매핑](../modeling/map-dependencies-across-your-solutions.md)