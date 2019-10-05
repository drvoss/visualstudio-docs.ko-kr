---
title: 다른 Visual Studio 버전에서 모델 및 다이어그램 읽기
titleSuffix: ''
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- models, versions of Visual Studio
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7d8366c0f87830a77f550dabbce2e8f875171418
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62823983"
---
# <a name="read-models-and-diagrams-in-other-visual-studio-editions"></a>다른 Visual Studio 버전에서 모델 및 다이어그램 읽기

모델 생성을 지원하지 않는 Visual Studio 버전에서 모델을 열면 읽기 전용 모드로 모델이 열립니다. 이 모드에서는 다이어그램의 레이아웃을 변경할 수 있지만 모델을 변경할 수는 없습니다.

모델 생성을 지 원하는 Visual Studio의 버전을 보려면 [아키텍처 및 모델링 도구에 대 한 버전 지원](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)합니다.

## <a name="obtaining-access-to-a-model-and-diagrams"></a>모델 및 다이어그램에 대한 액세스 권한 얻기

종속성 다이어그램을 읽으려면 먼저 Visual Studio를 사용 하 여 모델링 프로젝트를 열려면 하며 다음 그 안에서 다이어그램을 엽니다.

따라서 종속성 다이어그램을 읽으려는 경우 이전에 생성 된 모델링 프로젝트에 액세스할 수 있어야 합니다도. 이렇게 하려면 소스 제어에서 프로젝트에 액세스 하거나 프로젝트 파일의 복사본을 가져옵니다.

> [!NOTE]
> 코드 맵 및 코드에서 생성된 .NET 클래스 다이어그램에는 적용되지 않습니다. 이러한 다이어그램은 모델링 프로젝트와 독립적으로 볼 수 있습니다.

종속성 다이어그램을 읽으려면 해야 하는 파일의 최소 집합은 다음과 같습니다.

- 두 개의 다이어그램 파일 하려는 내용은 예를 들어 다이어그램 **MyDiagram.classdiagram 및 MyDiagram.classdiagram.layout**합니다.

    > [!NOTE]
    > 종속성 다이어그램에 대 한 있어야 라는 파일이 _MyDiagram_**. layerdiagram.suppressions**합니다.

- 모델링 프로젝트 파일 (**MyModel.modelproj**)

- 루트 모델 파일 (**ModelDefinition\MyModel.uml**)

- 다이어그램에서 참조 된 패키지에 대 한 패키지 파일 (**ModelDefinition\MyPackage.uml**)

## <a name="changes-that-you-can-make-in-read-only-mode"></a>읽기 전용 모드에서 수행할 수 있는 변경 내용

모델 생성을 지원하지 않는 Visual Studio 버전에서 모델 및 다이어그램을 열면 모델을 변경할 수 없습니다. 즉, 다이어그램이나 모델 탐색기에 표시되는 요소 및 관계를 변경할 수 없습니다. 그러나 다음과 같이 다이어그램의 레이아웃을 일부 변경할 수 있습니다.

- 다이어그램에서 모양 및 연결선을 다시 정렬합니다.

- 모양을 확장 및 축소합니다.

이러한 변경 내용을 저장할 수 있습니다. 업데이트 된 변경 내용을 다른 사용자에 게 표시 하려는 경우 전송 이상 해야 **.layout** 파일입니다.

## <a name="see-also"></a>참고 항목

- [종속성 다이어그램: 참조](../modeling/layer-diagrams-reference.md)
- [앱용 모델 만들기](../modeling/create-models-for-your-app.md)