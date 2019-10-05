---
title: '방법: 응용 프로그램 아이콘 지정 (Visual Basic의 경우 C#) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- icons [Visual Studio], application
- application properties [Visual Studio], icons
- application icons [Visual Studio]
ms.assetid: ad8e14ed-adc2-45b6-a0be-818b16d5616f
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 6f4502bcc439d55e36dad43add4c5b9852be21bd
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65685370"
---
# <a name="how-to-specify-an-application-icon-visual-basic-c"></a>방법: 응용 프로그램 아이콘 지정 (Visual Basic의 경우 C#)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

프로젝트에 대한 `Icon` 속성은 컴파일된 애플리케이션에 대해 파일 탐색기 및 Windows 작업 표시줄에서 표시되는 아이콘 파일(.ico)을 지정합니다.  
  
 `Icon` 속성은 **프로젝트 디자이너**의 **응용 프로그램** 창에서 액세스할 수 있습니다. 이 속성에는 리소스나 콘텐츠 파일로 프로젝트에 추가된 아이콘 목록이 포함되어 있습니다.  
  
> [!NOTE]
> 애플리케이션에 대한 아이콘 속성을 설정한 후에는 애플리케이션에서 각 **창** 또는 **폼**의 `Icon` 속성도 설정할 수 있습니다. WPF(Windows Presentation Foundation) 독립 실행형 애플리케이션의 창 아이콘에 대한 자세한 내용은 <xref:System.Windows.Window.Icon%2A>속성을 참조하세요.  
  
### <a name="to-specify-an-application-icon"></a>애플리케이션 아이콘을 지정하려면  
  
1. **솔루션 탐색기**에서 프로젝트 노드(**솔루션** 노드 아님)를 선택합니다.  
  
2. 메뉴 모음에서 **프로젝트**, **속성**을 선택합니다.  
  
3. **프로젝트 디자이너**가 나타나면 **응용 프로그램** 탭을 선택합니다.  
  
4. **(Visual Basic)** **아이콘** 목록에서 아이콘 파일(.ico)을 선택합니다.  
  
     **(C#)** **아이콘**목록 근처에서 **\<찾아보기...>** 단추를 선택한 다음 원하는 아이콘 파일의 위치로 이동합니다.  
  
## <a name="see-also"></a>참고 항목  
 [프로젝트 디자이너, 응용 프로그램 페이지(Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md)   
 [프로젝트 디자이너, 응용 프로그램 페이지(C#)](../ide/reference/application-page-project-designer-csharp.md)   
 [응용 프로그램 속성 관리](../ide/application-properties.md)  
 [방법: 리소스 추가 또는 제거](https://msdn.microsoft.com/7b77bc06-3952-4799-b029-def3f8f7f88d)
