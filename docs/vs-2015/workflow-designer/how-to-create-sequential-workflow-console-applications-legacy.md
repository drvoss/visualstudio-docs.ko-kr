---
title: '방법: 순차 워크플로 콘솔 응용 프로그램 만들기 (레거시) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- workflows, console applications
- sequential workflows, console applications
- console applications, sequential workflow
ms.assetid: 9f7be7fa-551f-42c6-a9bb-f5ae8ab83625
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 932b770f38f75d26028eceb6c0addc2ababeef6d
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65696354"
---
# <a name="how-to-create-sequential-workflow-console-applications-legacy"></a>방법: 순차 워크플로 콘솔 애플리케이션 만들기(레거시)
[!INCLUDE[wfd1](../includes/wfd1-md.md)]에서 제공하는 레거시 [!INCLUDE[vs2010](../includes/vs2010-md.md)]를 사용하여 순차 워크플로 콘솔 애플리케이션 프로젝트를 만들려면 다음 단계를 따릅니다. 레거시 [!INCLUDE[wfd2](../includes/wfd2-md.md)]는 [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] 또는 [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)]를 대상으로 해야 하는 경우에 사용합니다.  
  
### <a name="to-create-a-sequential-workflow-console-application"></a>순차 워크플로 콘솔 애플리케이션을 만들려면  
  
1. Visual Studio를 시작합니다.  
  
2. **파일** 메뉴에서 **새로 만들기**를 가리킨 다음, **프로젝트**를 선택합니다.  
  
     **새 프로젝트** 대화 상자가 열립니다.  
  
3. 중 하나를 선택 합니다 **.NET Framework 3.0** 옵션 또는 **.NET Framework 3.5** 목록 맨 위에 있는 드롭다운에서 옵션을 **새 프로젝트** 레거시 디자이너에 액세스 하려면 창입니다.  
  
    > [!NOTE]
    > 기본 옵션 [!INCLUDE[vs2010](../includes/vs2010-md.md)] 됩니다 **.NET Framework 4**합니다. 이 옵션은 [!INCLUDE[wf](../includes/wf-md.md)]을 대상으로 하는 [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)] 애플리케이션을 만드는 데 사용합니다.  
  
4. 에 **프로젝트 형식** 창, 선택 Visual C# 프로젝트나 Visual Basic 프로젝트 (아래 **다른 언어**)를 선택한 후 **워크플로**합니다.  
  
5. 에 **템플릿을** 창 **순차 워크플로 콘솔 응용 프로그램**합니다.  
  
6. 에 **이름을** 상자에서 쉽게 식별할 수 있도록 프로젝트에 대 한 설명이 포함 된 이름을 입력 합니다.  
  
7. 에 **위치** 상자에 프로젝트를 저장할 또는 클릭 하려는 디렉터리를 입력 합니다 **찾아보기** 이동 합니다.  
  
     Windows Forms 디자이너가 열리며 사용자가 만든 프로젝트의 Form1이 나타납니다.  
  
8. **확인**을 클릭합니다.  
  
     워크플로 디자이너가 열리며 사용자가 만든 순차 워크플로의 워크플로 디자인 화면이 나타납니다.  
  
9. 활동을 끌어 합니다 **도구 상자** 에서 디자인 화면에는 **에 작업 놓기** 영역을 지정 합니다.  
  
## <a name="see-also"></a>참고 항목  
 [레거시 워크플로 프로젝트 만들기](../workflow-designer/creating-legacy-workflow-projects.md)   
 [워크플로 개발](https://msdn.microsoft.com/557bcb1f-a7ab-49f6-8df7-2706b7001301)