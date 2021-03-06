---
title: '방법: VSTO 추가 기능을 비활성화 된 다시 사용 하도록 설정'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VST.Warning.DisabledAddIn
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- disabled add-ins
- add-ins [Office development in Visual Studio], disabled
- add-ins [Office development in Visual Studio], enabling
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: c81e44b548f4d1139810780731741a489e624047
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/06/2018
ms.locfileid: "35675131"
---
# <a name="how-to-re-enable-a-vsto-add-in-that-has-been-disabled"></a>방법: VSTO 추가 기능을 비활성화 된 다시 사용 하도록 설정
  Microsoft Office 응용 프로그램에서는 예기치 않게 동작하는 VSTO 추가 기능을 사용하지 않도록 설정할 수 있습니다. 디버그하려고 할 때 응용 프로그램이 VSTO 추가 기능을 로드하지 않는 경우 응용 프로그램에서 VSTO 추가 기능을 하드 비활성화 또는 소프트 비활성화했을 수 있습니다.  
  
 [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]  
  
## <a name="hard-disabled-vsto-add-ins"></a>하드 비활성화 된 VSTO 추가 기능  
 하드 비활성화는 VSTO 추가 기능으로 인해 응용 프로그램이 예기치 않게 종료 하는 경우 발생할 수 있습니다. 또한 개발 컴퓨터에서 VSTO 추가 기능의 <xref:Microsoft.Office.Tools.AddIn.Startup> 이벤트 처리기가 실행되고 있는 동안 디버거를 중지하는 경우 발생합니다.  
  
### <a name="to-re-enable-a-vsto-add-in"></a>VSTO 추가 기능을 다시 활성화하려면  
  
1.  응용 프로그램에서 **파일** 탭을 클릭합니다.  
  
2.  *ApplicationName* **옵션** 단추를 클릭합니다.  
  
3.  범주 창에서 **추가 기능**을 클릭합니다.  
  
4.  세부 정보 창에서 VSTO 추가 기능이 **사용하지 않는 응용 프로그램 추가 기능** 목록에 표시되는지 확인합니다.  
  
     **이름** 열은 어셈블리의 이름을 지정하고 **위치** 열은 응용 프로그램 매니페스트의 전체 경로를 지정합니다.  
  
5.  **관리** 상자에서 **사용할 수 없는 항목**을 클릭한 다음 **이동**을 클릭합니다.  
  
6.  VSTO 추가 기능을 선택하고 **사용**을 클릭합니다.  
  
7.  **닫기**를 클릭합니다.  
  
## <a name="soft-disabled-vsto-add-ins"></a>소프트 비활성화 된 VSTO 추가 기능  
 소프트 비활성화는 VSTO 추가 기능에서 응용 프로그램이 예기치 않게 닫히지 않는 오류를 생성하는 경우 수행됩니다. 예를 들어 <xref:Microsoft.Office.Tools.AddIn.Startup> 이벤트 처리기가 실행되는 동안 처리되지 않은 예외가 발생하는 경우 응용 프로그램에서 VSTO 추가 기능을 소프트 비활성화할 수 있습니다.  
  
> [!NOTE]  
>  소프트 비활성화된 VSTO 추가 기능을 다시 활성화하면 응용 프로그램이 즉시 VSTO 추가 기능을 로드하려고 시도합니다. 응용 프로그램이 처음에 VSTO 추가 기능을 소프트 비활성화하도록 만든 문제가 해결되지 않은 경우 응용 프로그램에서 VSTO 추가 기능을 다시 소프트 비활성화합니다.  
  
### <a name="to-re-enable-a-vsto-add-in"></a>VSTO 추가 기능을 다시 활성화하려면  
  
1.  응용 프로그램에서 **파일** 탭을 클릭합니다.  
  
2.  *ApplicationName* **옵션** 단추를 클릭합니다.  
  
3.  범주 창에서 **추가 기능**을 클릭합니다.  
  
4.  세부 정보 창에서 VSTO 추가 기능이 **비활성 응용 프로그램 추가 기능** 목록에 표시되는지 확인합니다.  
  
     **이름** 열은 어셈블리의 이름을 지정하고 **위치** 열은 응용 프로그램 매니페스트의 전체 경로를 지정합니다.  
  
5.  **관리** 상자에서 **COM 추가 기능**을 클릭한 다음 **이동**을 클릭합니다.  
  
6.  **COM 추가 기능** 대화 상자에서 사용할 수 없는 VSTO 추가 기능 옆에 있는 확인란을 선택합니다.  
  
7.  **확인**을 클릭합니다.  
  
## <a name="see-also"></a>참고자료  
 [Office 솔루션 빌드](../vsto/building-office-solutions.md)   
 [Office 프로젝트 디버깅](../vsto/debugging-office-projects.md)   
 [VSTO 추가 기능 프로그래밍](../vsto/programming-vsto-add-ins.md)  
  
  