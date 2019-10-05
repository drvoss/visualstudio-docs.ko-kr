---
title: 레거시 활동 디자이너를 사용 하 여 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- activities, configuring
- custom activities
- Activity Designer
- child activities, adding
- activities, adding child
- activities, creating custom
ms.assetid: 2fea8a05-6e58-423d-94bf-a822b15ffb80
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 5755c6a3b4ece5b40c7799d83bdf33966d5c2b3e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62855779"
---
# <a name="using-the-legacy-activity-designer"></a>레거시 활동 디자이너 사용
이 항목에서는 레거시 [!INCLUDE[wfd1](../includes/wfd1-md.md)]에서 활동 디자이너를 사용하는 방법에 대해 설명합니다. 레거시 디자이너는 [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] 또는 [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)]를 대상으로 하는 경우에 사용합니다.  
  
 활동 디자이너를 사용하면 사용자 지정 활동을 직접 만들 수 있습니다.  
  
## <a name="creating-a-custom-activity"></a>사용자 지정 활동 만들기  
 활동 디자이너를 사용하여 사용자 지정 활동을 만들려면 다음 단계를 따르세요.  
  
1. 에 **프로젝트** 메뉴에서 클릭 **활동 추가**합니다.  
  
2. 선택 된 **활동** 또는 **활동 (코드 분리)** 템플릿.  
  
   1. 사용 된 **활동** 활동 정의와 사용자 코드가 같은 코드 파일에 사용 하 여 작업을 만들기 위한 템플릿.  
  
   2. 사용 된 **활동 (코드 분리)** 별도 코드 파일에 사용자 코드가 있는 워크플로 마크업으로 표현 된 활동 정의 사용 하 여 작업을 만들기 위한 템플릿.  
  
3. 활동 이름을 입력 하거나 기본 이름을 유지 하 고, 클릭 **추가**합니다.  
  
   형식의 새 프로젝트를 만들어 사용자 지정 활동 집합을 만들 수도 있습니다 **Workflow Activity Library**합니다. 이 프로젝트 형식에 대 한 자세한 내용은 참조 하세요. [방법: 워크플로 활동 라이브러리 (레거시) 만들기](../workflow-designer/how-to-create-a-workflow-activity-library-legacy.md)합니다.  
  
## <a name="configuring-an-activity"></a>활동 구성  
 활동 디자이너가 활성 상태일 때 속성 브라우저를 사용하여 다음 표에 나열된 속성을 구성할 수 있습니다.  
  
|속성|설명|  
|--------------|--------------|  
|**이름**|활동 이름입니다.|  
|**기본 클래스**|활동이 파생되는 기본 클래스입니다. 기본 클래스는 [SequenceActivity](http://go.microsoft.com/fwlink?LinkID=65020)합니다. 에 **속성** 창에서 클릭 합니다 **기본 클래스** 줄임표 **[...]**  다른 기본 클래스를 선택 합니다 [찾아.NET 유형 선택 대화 상자 (레거시)](../workflow-designer/browse-and-select-a-dotnet-type-dialog-box-legacy.md)합니다.|  
|**설명**|활동의 사용자 정의 설명입니다.|  
|**사용**|로 **True** 기본적으로 작업 실행 및 유효성 검사를 사용 하도록 설정 합니다. 로 **False** 활동 실행 및 유효성 검사를 사용 하지 않도록 설정 합니다. 활동 실행 및 유효성 검사에 대 한 정보를 참조 하세요 [워크플로 활동 개발](http://go.microsoft.com/fwlink?LinkID=65024)합니다.|  
  
## <a name="adding-child-activities"></a>자식 활동 추가  
 도구 상자에서 디자인 중인 활동으로 자식 활동을 끌어 놓을 수 있습니다. 그런 다음 속성 브라우저를 사용하여 각 자식 활동을 구성할 수 있습니다.  
  
## <a name="see-also"></a>참고 항목  
 [워크플로 활동 개발](http://go.microsoft.com/fwlink?LinkID=65024)   
 [사용자 지정 활동 만들기](http://go.microsoft.com/fwlink?LinkID=65021)   
 [레거시 워크플로 활동](../workflow-designer/legacy-workflow-activities.md)   
 [사용자 지정 활동 샘플](http://go.microsoft.com/fwlink?LinkID=65022)   
 [방법: 워크플로 활동 라이브러리 (레거시) 만들기](../workflow-designer/how-to-create-a-workflow-activity-library-legacy.md)   
 [레거시 워크플로 디자이너 사용](../workflow-designer/using-the-legacy-workflow-designer.md)