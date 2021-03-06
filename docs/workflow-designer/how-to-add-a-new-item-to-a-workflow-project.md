---
title: '워크플로 디자이너-방법: 워크플로 프로젝트에 새 항목을 추가 합니다.'
ms.date: 06/25/2018
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
ms.assetid: 5c6180ca-af10-4513-b0cb-7d478fd84eab
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: dbed404f2cdd69446d8945fc9ff96703eccd161f
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49814236"
---
# <a name="how-to-add-a-new-item-to-a-workflow-project"></a>방법: 워크플로 프로젝트에 새 항목을 추가 합니다.

워크플로 프로젝트를 만든 후 프로젝트에 워크플로 활동, 디자이너 및 기타 친숙 한 Visual Studio 항목을 추가할 수 있습니다.

다음 표에서 워크플로 프로젝트에 추가할 수 있는 Windows WF (Workflow Foundation) 항목을 나열 합니다.


| 이름 | 설명 |
|-| - |
| 동작 | 다른 활동으로 구성할 활동입니다. 선택할 때와 동일한 XAML 파일이 프로젝트에 추가이 항목을 선택 하는 **활동 라이브러리** 새 프로젝트 템플릿. 이 절차에 대 한 자세한 내용은 참조 하세요. [방법: 활동 라이브러리 만들기](../workflow-designer/how-to-create-an-activity-library.md)합니다. |
| 활동 디자이너 | 활동의 디자인 타임 환경을 사용자 지정할 디자이너입니다. 선택할 때와 동일한 파일이 프로젝트에 추가이 항목을 선택 하는 **활동 디자이너 라이브러리** 새 프로젝트 템플릿. 이 절차에 대 한 자세한 내용은 참조 하세요. [방법: 활동 디자이너 라이브러리 만들기](../workflow-designer/how-to-create-an-activity-designer-library.md)합니다. |
| Code 활동 | 코드로 작성된 실행 논리가 포함된 활동입니다. <xref:System.Activities.CodeActivity.Execute%2A> 메서드의 재정의가 포함된 소스 코드 파일이 이미 생성되어 있습니다. |
| WCF 워크플로 서비스 | 워크플로 활동을 사용하여 빌드된 [!INCLUDE[indigo2](../workflow-designer/includes/indigo2_md.md)] 서비스입니다. 선택할 때와 동일한 파일이 프로젝트에 추가이 항목을 선택 하는 **WCF 워크플로 서비스 응용 프로그램** 새 프로젝트 템플릿. 이 절차에 대 한 자세한 내용은 참조 하세요. [방법: WCF 워크플로 서비스 응용 프로그램을 만드는](../workflow-designer/how-to-create-a-wcf-workflow-service-application.md)합니다. |

## <a name="to-add-a-new-item-to-a-workflow-project"></a>워크플로 프로젝트에 새 항목을 추가하려면

1. 에 **프로젝트** 메뉴에서 **새 항목 추가**합니다.

   **새 항목 추가** 대화 상자가 열립니다.

1. 왼쪽 창에서 선택 합니다 **워크플로** 범주를 선택한 다음 워크플로 항목 템플릿 선택 합니다.

   > [!NOTE]
   > 표시 되지 않는 경우는 **워크플로** 범주, 첫 번째 설치를 **Windows Workflow Foundation** Visual Studio 2017 구성 요소입니다. 자세한 지침은 [Windows Workflow Foundation 설치](developing-applications-with-the-workflow-designer.md#install-windows-workflow-foundation)합니다.

1. 항목에 대 한 이름을 입력 합니다 **이름을** 대화 상자의 맨 위에 있는 상자입니다.

1. 선택 **추가** 프로젝트에 항목을 추가 합니다.

## <a name="see-also"></a>참고자료

- [워크플로 프로젝트 만들기](../workflow-designer/creating-a-workflow-project.md)