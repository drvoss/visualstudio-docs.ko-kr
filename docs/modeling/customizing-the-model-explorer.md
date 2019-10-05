---
title: 모델 탐색기 사용자 지정
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.dsltools.dsldesigner.explorerbehavior
helpviewer_keywords:
- Domain-Specific Language Tools, Domain-Specific Language Explorer
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 65ada4a061fd928a074c9fcdb24fab60a277c457
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63445849"
---
# <a name="customizing-the-model-explorer"></a>모델 탐색기 사용자 지정
변경할 수 있습니다 탐색기의 동작과 모양을 도메인별 언어 디자이너에 대 한 다음과 같습니다.

- 창 제목을 변경 합니다.

- 탭 아이콘을 변경 합니다.

- 노드에 대 한 아이콘을 변경 합니다.

- 노드를 숨깁니다.

## <a name="changing-the-window-title"></a>창 제목 변경
 생성 된 탐색기의 창 제목을 변경 하려면 선택 **탐색기 동작** 에 **DSL 탐색기**, 한 다음 합니다 **속성** 창에서  **제목** 속성을 추가할 제목입니다.

## <a name="changing-the-tab-icon"></a>탭 아이콘 변경
 탐색기에 대 한 탭 아이콘을 변경 하려면.bmp 파일에는 16 x 16 픽셀 아이콘을 사용 합니다. \DslPackage\Resources\ 폴더에서 아이콘 파일을 저장 하 고 파일 이름을 변경한 **ModelExplorerToolWindowBitmaps.bmp**합니다. 예를 들어, 있습니다 수.bmp 형식으로 Visual Studio setup.ico 아이콘 파일을 변경 하 고 이름을 **DSLLanguageName\DslPackage\Resources\ModelExplorerToolWindowBitmaps.bmp**합니다. 와 함께 도킹 될 때 생성된 된 디자이너 탐색기 탭에이 아이콘이 표시 됩니다 **솔루션 탐색기**합니다.

## <a name="setting-custom-icons-on-explorer-nodes"></a>탐색기 노드에서 사용자 지정 아이콘 설정
 탐색기 노드 설정을 사용 하 여 탐색기에서 노드를 사용자 지정할 수 있습니다. 다음 절차에는 노드에 아이콘을 추가 하는 방법을 보여 줍니다.

#### <a name="to-add-an-icon-to-an-explorer-node"></a>탐색기 노드에 아이콘을 추가 하려면

1. 만들기는 [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] 작업 흐름 솔루션 템플릿을 사용 하 여 솔루션입니다.

2. 에 16 x 16 픽셀 아이콘을 포함 하는.bmp 파일을 저장 합니다 **Dsl\Resources** 솔루션에서 폴더.

3. 에 **DSL 탐색기**를 마우스 오른쪽 단추로 클릭 **탐색기 동작** 클릭 하 고 **새 탐색기 노드 설정을 추가**합니다.

    **ExplorerNodeSettings** 노드 아래에 나타납니다 합니다 **사용자 지정 노드 설정** 노드.

4. 선택 **ExplorerNodeSettings**, 한 다음는 **속성** 창에서 **클래스** 하 **행위자**합니다.

5. 설정할 **아이콘을 표시 하려면** 아이콘 파일의 경로입니다.

6. 모든 템플릿 변환 하 고 빌드 후 솔루션을 실행 합니다.

7. 생성된 된 디자이너에서 샘플 다이어그램을 엽니다.

    세 가지 탐색기에 표시 됩니다 **행위자** 아이콘에 있는 노드.

> [!NOTE]
> 생성 된 탐색기에 표시 되는 모든 요소에 대 한 노드 아이콘을 사용 하도록 설정한 경우 모든 탐색기 노드 아이콘이 표시 됩니다. 아이콘 없음에 설정한 경우 노드는 기본 아이콘이 표시 됩니다.

## <a name="changing-the-name-displayed-on-an-explorer-node"></a>탐색기 노드에 표시 되는 이름 변경
 탐색기에서 모델 요소의 이름이 표시 되는 방식을 변경할 수 있습니다. 다음 절차의 이름을 표시 하는 방법을 보여 줍니다 합니다 **태스크** 에서 참조 되는 **주석** 주석 노드에서.

#### <a name="to-display-a-property"></a>속성을 표시 하려면

1. 이전 절차에서 만든 솔루션을 엽니다.

2. 있는지 확인 합니다 **주석** 속성 이름 가진 role의 복합성을 설정 하 여 단일 도메인 클래스만 참조 **주제** 0.. 1로 합니다. 속성 이름이 되어서는 **주체**, 관계 이름 수 있어야 하 고 **CommentReferencesSubject**합니다.

3. 에 **DSL 탐색기**를 마우스 오른쪽 단추로 클릭 **탐색기 동작** 클릭 하 고 **새 탐색기 노드 설정을 추가**합니다.

     **ExplorerNodeSettings** 노드 아래에 나타납니다 합니다 **사용자 지정 노드 설정** 노드.

4. 선택 **ExplorerNodeSettings**, 한 다음는 **속성** 창에서 **클래스** 하 **주석**합니다.

5. 마우스 오른쪽 단추로 클릭 합니다 **주석** 노드를 차례로 클릭 한 다음 **새 속성 경로 추가**합니다.

     이라는 새 노드가 나타납니다 **속성을 표시**합니다.

6. 선택 **속성을 표시**, 한 다음는 **속성** 창에서 값 필드를 클릭 **속성 경로**합니다. 선택 **주석**, 한 다음 **CommentReferencesSubject**, 한 다음 **FlowElement**합니다. 결과 경로 유사 **CommentReferencesSubject.Subject/! 주체**합니다.

7. 값 필드에 **속성**를 선택 **이름**합니다.

8. 모든 템플릿 변환 하 고 빌드 후 솔루션을 실행 합니다.

9. 생성된 된 디자이너에서 샘플 다이어그램을 엽니다.

10. 그리기를 **주석 연결선** 주석 요소 사이 및 **Task1** 다이어그램의 요소입니다.

     탐색기 노드의 주석으로 표시 됩니다 **Task1**합니다.

## <a name="hiding-nodes"></a>노드 숨기기
 해당 경로를 추가 하 여 탐색기에서 노드를 숨길 수 있습니다 합니다 **숨겨진 노드** 노드의 합니다 **DSL 탐색기**합니다. 다음 절차를 숨기는 방법을 보여 줍니다 **주석** 노드.

#### <a name="to-hide-an-explorer-node"></a>탐색기 노드를 숨기려면

1. 이전 절차에서 만든 솔루션을 엽니다.

2. 에 **DSL 탐색기**를 마우스 오른쪽 단추로 클릭 **탐색기 동작** 클릭 하 고 **새 도메인 경로 추가**합니다.

     A **도메인 경로** 노드 아래에 나타납니다 **숨겨진 노드**합니다.

3. 선택 **도메인 경로**, 한 다음는 **속성** 창에서 값 필드를 클릭 **경로 정의**합니다. 선택 **FlowGraph**, 한 다음 **FlowGraphHasComments**합니다. 결과 경로 유사 **FlowGraphHasComments.Comments**

4. 모든 템플릿 변환 하 고 빌드 후 솔루션을 실행 합니다.

5. 생성된 된 디자이너에서 샘플 다이어그램을 엽니다.

     탐색기를만 표시 됩니다는 **행위자** 노드를 표시 되지 않아야 하 고는 **주석** 노드.

## <a name="see-also"></a>참고자료

- [도메인 특정 언어 도구 용어집](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)