---
title: Workflow Designer 셸 기능
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- WFDShellFeatures.UI
ms.assetid: 14bfe312-9592-408e-92ce-e98585ad16e7
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4519be8ec5c5d4ba8a611df1880ae770a83cf981
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62433866"
---
# <a name="workflow-designer-shell-features"></a>Workflow Designer 셸 기능

워크플로 디자이너의 세 가지 주요 UI 영역 구성 됩니다: 디자이너 화면, 위에 이동 경로 탐색 막대 및 아래쪽의 셸 합니다. 화면 위쪽에 있는 이동 경로 탐색 막대는 현재 루트 활동의 상위 목록을 표시하는 데 사용됩니다. 자세한 내용은 [방법: 이동 경로 탐색 사용](../workflow-designer/how-to-use-breadcrumb-navigation.md)합니다. 화면 중앙의 디자이너 화면은 워크플로를 작성하는 데 사용됩니다. 화면 아래쪽의 셸에는 현재 뷰를 관리하는 데 사용되는 단추가 포함되어 있습니다.

## <a name="shell-features"></a>셸 기능
 셸 막대 오른쪽에는 워크플로를 확대/축소하고 워크플로의 내용을 화면 크기에 맞추며 개요 맵을 표시하거나 숨기는 데 사용할 수 있는 단추가 있습니다.  바로 가기 키 Ctrl++ 및 Ctrl+-를 사용하여 워크플로를 확대하거나 축소할 수도 있습니다.

## <a name="overview-map"></a>개요 맵
 개요 맵은 모든 자식과 확장된 자식을 포함하여 현재의 이동 경로 탐색 막대에 해당하는 전체 활동을 작은 버전으로 표시합니다. 편집기 안에는 현재 표시된 활동 부분을 강조하는 주황색 테두리의 사각형 뷰포트가 있습니다. 이 사각형을 개요 맵 주위로 끌면 Workflow Designer가 스크롤되면서 편집기 뷰가 바뀝니다.

> [!NOTE]
> 워크플로 디자이너 사용자 인터페이스 가상화 됩니다. 활동 디자이너는 필요한 경우에만 렌더링됩니다. 디자이너 화면에 표시된 적이 없는 워크플로 부분이 있다면 그 부분은 개요 맵에서 흰색으로 나타납니다. 개요 맵 주위를 스크롤하면 워크플로가 완전히 그려집니다.

## <a name="copying-or-saving-workflows-as-images"></a>워크플로를 이미지로 복사 또는 저장
 워크플로를 비트맵 형식으로 복사하거나 비트맵 또는 벡터 형식으로 저장할 수 있습니다. 이미지를 복사하거나 저장하면 모든 자식과 확장된 자식을 포함하여 현재의 경로 탐색 루트의 전체 활동에 대한 뷰를 다른 프로그램으로 내보낼 수 있습니다.

 이미지를 복사 하려면 마우스 오른쪽 단추로 클릭 선택한 디자이너 **이미지로 복사**합니다. 이미지를 저장 하려면 마우스 오른쪽 단추로 클릭는 디자이너 및 선택 **이미지로 저장**합니다. 워크플로는 JPG, PNG, GIF 또는 XPS 형식으로 저장할 수 있습니다. 형식에서 선택 된를 **다른 이름으로 저장** 대화 상자를 **형식으로 저장:** 드롭다운 목록 상자 창의 맨 아래에 있습니다.

## <a name="fonts-and-colors"></a>글꼴 및 색

Visual Studio 내에서 워크플로 디자이너에 사용 된 글꼴이 환경 글꼴에 의해 제어 됩니다. 워크플로 디자이너에 표시 된 색에는 운영 체제 테마에 고대비 색 구성표를 사용 하는 경우 변경 합니다. 워크플로 디자이너에서 변경 내용을 적용 하기 전에 글꼴 또는 색상 설정을 변경한 후 Visual Studio를 다시 시작 해야 합니다.