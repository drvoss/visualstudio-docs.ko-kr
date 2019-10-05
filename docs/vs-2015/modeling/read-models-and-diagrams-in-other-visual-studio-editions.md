---
title: 다른 Visual Studio 버전에서 모델 및 다이어그램 읽기 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- models, versions of Visual Studio
ms.assetid: 46eee279-a9e4-4742-a024-5bd2cf032b86
caps.latest.revision: 22
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 21dc0cb7f02639ca6faa89ae4c067f21e083d6d3
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63387508"
---
# <a name="read-models-and-diagrams-in-other-visual-studio-editions"></a>다른 Visual Studio 버전에서 모델 및 다이어그램 읽기
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

모델 생성을 지원하지 않는 Visual Studio 버전에서 모델을 열면 읽기 전용 모드로 모델이 열립니다. 이 모드에서는 다이어그램의 레이아웃을 변경할 수 있지만 모델을 변경할 수는 없습니다.  
  
 모델 생성을 지 원하는 Visual Studio의 버전을 보려면 [아키텍처 및 모델링 도구에 대 한 버전 지원](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)합니다.  
  
## <a name="obtaining-access-to-a-model-and-diagrams"></a>모델 및 다이어그램에 대한 액세스 권한 얻기  
 UML 다이어그램 또는 레이어 다이어그램을 읽으려면 먼저 Visual Studio를 사용 하 여 모델링 프로젝트를 열려면 하며 다음 그 안에서 다이어그램을 엽니다.  
  
 이런 이유로 UML 다이어그램 또는 레이어 다이어그램을 읽으려면 다이어그램이 생성된 모델링 프로젝트에 대한 액세스 권한도 있어야 합니다. 이 작업을 수행하려면 [!INCLUDE[esprscc](../includes/esprscc-md.md)]에서 프로젝트에서 액세스하거나 프로젝트 파일의 복사본을 가져옵니다.  
  
> [!NOTE]
> 코드 맵 및 코드에서 생성된 .NET 클래스 다이어그램에는 적용되지 않습니다. 이러한 다이어그램은 모델링 프로젝트와 독립적으로 볼 수 있습니다.  
  
 UML 다이어그램 또는 레이어 다이어그램을 읽는 데 필요한 최소 파일 집합은 다음과 같습니다.  
  
- 두 개의 다이어그램 파일 하려는 내용은 예를 들어 다이어그램 **MyDiagram.classdiagram 및 MyDiagram.classdiagram.layout**합니다.  
  
    > [!NOTE]
    > 레이어 다이어그램에 대 한 있어야 라는 파일이 _MyDiagram_**. layerdiagram.suppressions**합니다.  
  
- 모델링 프로젝트 파일 (**MyModel.modelproj**)  
  
- 루트 모델 파일 (**ModelDefinition\MyModel.uml**)  
  
- 다이어그램에서 참조 된 패키지에 대 한 패키지 파일 (**ModelDefinition\MyPackage.uml**)  
  
## <a name="changes-that-you-can-make-in-read-only-mode"></a>읽기 전용 모드에서 수행할 수 있는 변경 내용  
 모델 생성을 지원하지 않는 Visual Studio 버전에서 모델 및 다이어그램을 열면 모델을 변경할 수 없습니다. 즉, 다이어그램이나 모델 탐색기에 표시되는 요소 및 관계를 변경할 수 없습니다. 그러나 다음과 같이 다이어그램의 레이아웃을 일부 변경할 수 있습니다.  
  
- 다이어그램에서 모양 및 연결선을 다시 정렬합니다.  
  
- 모양을 확장 및 축소합니다.  
  
  이러한 변경 내용을 저장할 수 있습니다. 업데이트 된 변경 내용을 다른 사용자에 게 표시 하려는 경우 전송 이상 해야 **.layout** 파일입니다.  
  
## <a name="RelatedTopics"></a>관련 항목  
  
|제목|설명|  
|-----------|-----------------|  
|[레이어 다이어그램: 참조](../modeling/layer-diagrams-reference.md)|레이어 다이어그램에는 기존 아키텍처 또는 제안된 아키텍처의 구조가 표시됩니다. 코드가 작성되면 레이어 다이어그램에 대해 자동으로 유효성을 검사할 수 있습니다.|  
|[UML 동작 다이어그램: 참조](../modeling/uml-activity-diagrams-reference.md)|동작 다이어그램에는 비즈니스 프로세스 또는 소프트웨어의 작업 흐름이 표시됩니다.|  
|[UML 클래스 다이어그램: 참조](../modeling/uml-class-diagrams-reference.md)|클래스 다이어그램에는 코드, 데이터베이스 스키마, 통신 프로토콜 또는 비즈니스 도메인 설명에 사용되는 용어집과 같은 여러 컨텍스트에서 사용되는 형식 및 관계가 표시됩니다.|  
|[UML 구성 요소 다이어그램: 참조](../modeling/uml-component-diagrams-reference.md)|구성 요소 다이어그램에는 소프트웨어 디자인의 분리 가능 파트 및 해당 인터페이스가 표시됩니다.|  
|[UML 시퀀스 다이어그램: 참조](../modeling/uml-sequence-diagrams-reference.md)|시퀀스 다이어그램에는 소프트웨어 디자인의 요소 간 상호 작용이 표시됩니다.|  
|[UML 사용 사례 다이어그램: 참조](../modeling/uml-use-case-diagrams-reference.md)|사용 사례 다이어그램에는 시스템 사용자 및 특정 목표를 달성하기 위해 수행할 수 있는 동작이 표시됩니다.|  
  
## <a name="see-also"></a>참고 항목  
 [앱용 모델 만들기](../modeling/create-models-for-your-app.md)
