---
title: 문서 및 다이어그램에 사용 사례 연결 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
f1_keywords:
- vs.teamarch.usecasediagram.artifact.properties.artifactlink
- vs.teamarch.usecasediagram.artifact
helpviewer_keywords:
- use case diagrams
ms.assetid: 4c9ed205-9197-4ed5-b39d-ddfa24a0a421
caps.latest.revision: 12
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: ee7657b12741cf65583317ba87bd465e15eb02bb
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63440974"
---
# <a name="link-a-use-case-to-documents-and-diagrams"></a>문서 및 다이어그램에 사용 사례 연결
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

사용 사례 다이어그램의 사용 사례를 다른 다이어그램 또는 문서에 연결할 수 있습니다. 예를 들어 다음과 같은 다이어그램 및 문서에 사용 사례를 연결할 수 있습니다.  
  
- 사용자와 시스템 또는 주요 구성 요소 간의 상호 작용을 통해 사용 사례의 목표가 인식되는 방식을 보여 주는 시퀀스 다이어그램  
  
- 사용 사례를 수행할 때 사용자와 시스템 또는 주요 구성 요소의 자세한 작업을 보여 주는 동작 다이어그램  
  
- 사용 사례를 자세히 설명하는 OneNote 페이지 또는 단락  
  
- 사용 사례를 자세히 설명하는 Word 문서 또는 PowerPoint 프레젠테이션 이러한 문서를 솔루션이나 팀이 액세스할 수 있는 위치(예: SharePoint 사이트)에 유지할 수 있습니다.  
  
  문서에 사용 사례를 연결하려면 사용 사례 다이어그램에 아티팩트를 만들고 사용 사례를 아티팩트에 연결합니다. 아티팩트의 속성에서 다른 다이어그램 또는 문서의 파일 경로를 설정합니다. 아티팩트를 두 번 클릭하면 다른 다이어그램 또는 문서가 열립니다.  
  
  각 사용 사례에 아티팩트를 원하는 수만큼 연결할 수 있습니다. 또한 사용 사례 다이어그램에서 여러 종류의 요소에 아티팩트를 연결할 수도 있습니다.  
  
### <a name="to-open-a-document-associated-with-an-artifact"></a>아티팩트와 연결된 문서를 열려면  
  
- 사용 사례 다이어그램에서 아티팩트 모양을 두 번 클릭합니다.  
  
     연결된 문서가 열립니다.  
  
### <a name="to-link-a-use-case-to-a-diagram-or-file-in-the-same-solution"></a>동일한 솔루션의 다이어그램 또는 파일에 사용 사례를 연결하려면  
  
1. 사용 사례 시나리오를 설명하는 시퀀스 다이어그램 또는 동작 다이어그램과 같은 다이어그램을 그립니다.  
  
2. 사용 사례 다이어그램으로 돌아갑니다.  
  
3. 솔루션 탐색기에서 사용 사례 다이어그램의 빈 부분으로 다이어그램 또는 파일을 끌어옵니다.  
  
4. 아티팩트에서 사용 사례로 연결 된 **종속성**합니다.  
  
### <a name="to-link-to-a-solution-file-such-as-a-word-document-or-powerpoint-presentation"></a>Word 문서 또는 PowerPoint 프레젠테이션과 같은 솔루션 파일에 연결하려면  
  
1. 솔루션에 문서를 추가합니다.  
  
    1. Word 문서를 솔루션과 동일한 Windows 폴더로 이동합니다.  
  
    2. 솔루션 탐색기에서 솔루션을 마우스 오른쪽 **추가**를 클릭 하 고 **기존 항목**합니다.  
  
    3. Word 문서에 이동 하 고 클릭 **추가**합니다.  
  
         Word 문서가 솔루션 탐색기의 솔루션 폴더에 나타납니다.  
  
2. 솔루션 탐색기에서 사용 사례 다이어그램의 빈 부분으로 Word 문서를 끌어옵니다.  
  
     새 아티팩트가 표시됩니다.  
  
3. 아티팩트에서 사용 사례로 연결 된 **종속성**합니다.  
  
### <a name="to-link-to-a-shared-document-onenote-element-or-web-page"></a>공유 문서, OneNote 요소 또는 웹 페이지에 연결하려면  
  
1. 공유 요소의 URL을 가져옵니다. 이 수, 예를 들어, 네트워크 파일 경로 시작을 사용 하는 '\\\\', 웹 페이지 또는 Sharepoint URL 시작 'http://' 또는 링크 하는 OneNote 섹션, 페이지 또는 단락 시작 부분 또는 ' onenote:'.  
  
2. 도구 상자에서 클릭 **아티팩트** 및 사용 사례 다이어그램에서를 클릭 합니다.  
  
3. 선택한 새 아티팩트를 사용 하 여 입력 하거나 URL을 붙여 합니다 **하이퍼링크** 속성입니다.  
  
    > [!NOTE]
    > 일반적인 작업 영역에서 파일을 선택 하는 파일 경로 제공 하려는 경우 (부터 '\\\\'), 또는 Visual Studio 솔루션 내에 있는 파일입니다. 이렇게 하면 파일 경로가 다른 팀 멤버의 컴퓨터에서 또는 솔루션이 이동된 경우에도 유효한 상태로 유지됩니다. Word 문서와 같은 문서 솔루션에 추가 하려면 솔루션 탐색기에서 솔루션을 마우스 오른쪽 단추로 클릭, 가리킨 **추가** 을 클릭 한 다음 **기존 항목**합니다.  
  
## <a name="see-also"></a>참고 항목  
 [UML 사용 사례 다이어그램: 참조](../modeling/uml-use-case-diagrams-reference.md)   
 [UML 사용 사례 다이어그램: 지침](../modeling/uml-use-case-diagrams-guidelines.md)   
 [UML 모델 및 다이어그램 편집](../modeling/edit-uml-models-and-diagrams.md)   
 [앱용 모델 만들기](../modeling/create-models-for-your-app.md)
