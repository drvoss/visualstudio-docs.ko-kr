---
title: Workflow Foundation 프로젝트 만들기
ms.date: 06/25/2018
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
helpviewer_keywords:
- Workflow Designer, creating a workflow project
- creating a workflow project
ms.assetid: 235a125e-ebe7-4a98-bf77-86c8558728fb
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4a4f8ed1effbc459bd2a17e3433738c1b461513b
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/25/2018
ms.locfileid: "36755656"
---
# <a name="workflow-project-templates"></a>워크플로 프로젝트 템플릿

Visual Studio 프로젝트 템플릿을 사용 하 여 워크플로, Windows Communication Foundation (WCF) 워크플로 서비스, 사용자 지정 활동 및 사용자 지정 활동 디자이너를 만들 수 있습니다. 이 문서에서는 Visual Studio에서 사용할 수 있는 프로젝트 템플릿을 사용 하 여 라이브러리 및 응용 프로그램을 만드는 방법을 설명 합니다.

## <a name="create-a-workflow-project"></a>워크플로 프로젝트 만들기

Visual Studio는 4 개의 서로 다른 워크플로 프로젝트 템플릿을 제공:

- 워크플로 콘솔 응용 프로그램

- WCF 워크플로 서비스 응용 프로그램

- 활동 라이브러리

- 활동 디자이너 라이브러리

이러한 서식 파일에 액세스 하려면 먼저 설치 합니다 **Windows Workflow Foundation** Visual Studio 2017 구성 요소입니다. 자세한 지침은 [Windows Workflow Foundation 설치](developing-applications-with-the-workflow-designer.md#install-windows-workflow-foundation)합니다.

1. 설치한 후는 **Windows Workflow Foundation** 구성 요소를 열기를 **새 프로젝트** 선택 하 여 대화 상자 **파일** > **새로만들기**  >  **프로젝트**합니다.

1. 왼쪽 창에서 선택 합니다 **Visual C#** > **워크플로** 범주 (또는 **Visual Basic** > **워크플로**Visual Basic을 선호 하는 경우).

1. 가운데 창에는 프로젝트 템플릿을 선택와 같은 **워크플로 콘솔 응용 프로그램**합니다.

1. 에 **이름을** 상자에서 쉽게 식별할 수 있도록 프로젝트에 대 한 설명이 포함 된 이름을 입력 합니다.

1. 에 **위치** 상자에 프로젝트를 저장 하거나 선택 하려는 디렉터리를 입력 합니다 **찾아보기** 이동 합니다.

1. 에 **솔루션** 상자에 새 솔루션에 대 한 이름을 입력 합니다. 선택 **확인** 응용 프로그램을 만들려고 합니다.

   > [!NOTE]
   > 새 프로젝트를 기존 솔루션에 추가 하려는 경우 Visual Studio에서 해당 솔루션을 열고, 솔루션을 마우스 오른쪽 단추로 클릭 **솔루션 탐색기**, 선택한 **추가** > **새로 만들기 프로젝트** 열려면 합니다 **새 프로젝트** 대화 상자.

## <a name="workflow-console-app"></a>워크플로 콘솔 응용 프로그램

원하는 경우는 **워크플로 콘솔 응용 프로그램** 템플릿, Visual Studio에서 XAML 워크플로 정의 만듭니다. Workflow Designer가 열리고 만들어진 워크플로의 캔버스가 표시 됩니다. 활동이 나 다른 워크플로 항목을 끌어 워크플로 구성 하려면 **도구 상자** 디자인 화면입니다.

## <a name="wcf-workflow-service-app"></a>WCF 워크플로 서비스 응용 프로그램

원하는 경우는 **WCF 워크플로 서비스 응용 프로그램** 템플릿, Visual Studio는 XAML로 서비스 정의 만듭니다. Workflow Designer를 사용 하 여 디자인 뷰로 열립니다는 <xref:System.Activities.Statements.Sequence> 집합을 포함 하는 활동 <xref:System.ServiceModel.Activities.Receive> 및 <xref:System.ServiceModel.Activities.SendReply> 활동입니다.

## <a name="activity-library"></a>활동 라이브러리

원하는 경우는 **활동 라이브러리** 템플릿, Visual Studio는 XAML에서 활동 정의 만듭니다. Workflow Designer가 열리고 사용자 지정 활동의 캔버스가 표시 됩니다. 활동을 끌어 **도구 상자** 을 디자인 화면으로 사용자 지정 활동에 포함 합니다.

> [!NOTE]
> 사용자 지정 활동의 본문에 자식 활동이 하나만 군요. 그러나 해당 자식 활동 수 복합 활동 등을 <xref:System.Activities.Statements.Sequence> 활동 또는 <xref:System.Activities.Statements.Flowchart> 활동.

## <a name="activity-designer-library"></a>활동 디자이너 라이브러리

원하는 경우는 **활동 디자이너 라이브러리** 템플릿, Visual Studio XAML 및 코드 숨김 구현 파일에서 활동 디자이너 정의 만듭니다. Workflow Designer가 열리고 활동 디자이너의 캔버스가 표시 됩니다. 끌어서 Windows Presentation Foundation (WPF)에서 제어 **도구 상자** 사용자 지정 활동 디자이너에서 사용 하는 디자인 화면입니다.

사용자 지정 활동 디자이너를 구현 하는 방법의 예제를 참조 하세요 [방법: 사용자 지정 활동 디자이너를 만드는](/dotnet/framework/windows-workflow-foundation/how-to-create-a-custom-activity-designer)합니다.

> [!NOTE]
> 기본.NET Framework 활동 및 사용자 지정 활동에 대 한 사용자 지정 활동 디자이너를 사용할 수 있습니다.

## <a name="see-also"></a>참고자료

- [Workflow Designer 사용](../workflow-designer/using-the-workflow-designer.md)
- [(.NET Framework) 워크플로 디자인 합니다.](/dotnet/framework/windows-workflow-foundation/designing-workflows)