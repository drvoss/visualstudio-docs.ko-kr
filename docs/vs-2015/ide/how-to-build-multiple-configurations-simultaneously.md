---
title: '방법: 여러 구성 동시 빌드 | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ba830937-3317-4674-8cc2-c0cd565603c5
caps.latest.revision: 12
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: aa16c4c02f92f71d3288896d56b94a6d570c7dd4
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49930416"
---
# <a name="how-to-build-multiple-configurations-simultaneously"></a>방법: 여러 구성 동시 빌드
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**일괄 빌드** 대화 상자를 통해 여러 빌드 구성 또는 모든 빌드 구성을 동시에 사용하여 대부분의 프로젝트 형식을 빌드할 수 있습니다. 그러나 다음과 같은 유형의 프로젝트는 여러 빌드 구성에서 동시에 빌드할 수 없습니다.  
  
1. JavaScript를 사용하여 빌드된 Windows용 [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] 앱  
  
2. 모든 Visual Basic 프로젝트  
  
   빌드 구성에 대한 자세한 내용은 [빌드 구성 이해](../ide/understanding-build-configurations.md)를 참조하세요.  
  
### <a name="to-build-a-project-in-multiple-build-configurations"></a>여러 빌드 구성에서 프로젝트를 빌드하려면  
  
1.  메뉴 모음에서 **빌드**, **일괄 빌드**를 선택합니다.  
  
2.  **빌드** 열에서 프로젝트를 빌드할 구성에 대한 확인란을 선택합니다.  
  
    > [!TIP]
    >  솔루션에 대한 빌드 구성을 만들거나 편집하려면 메뉴 모음에서 **빌드**, **Configuration Manager**를 선택하여 **Configuration Manager** 대화 상자를 엽니다. 솔루션에 대한 빌드 구성을 편집한 후 **일괄 빌드** 대화 상자에서 **다시 빌드** 단추를 클릭하여 솔루션의 프로젝트에 대한 모든 빌드 구성을 업데이트할 수 있습니다.  
  
3.  **빌드** 또는 **다시 빌드** 단추를 선택하여 지정한 구성으로 프로젝트를 빌드합니다.  
  
## <a name="see-also"></a>참고 항목  
 [방법: 구성 만들기 및 편집](../ide/how-to-create-and-edit-configurations.md)   
 [빌드 구성 이해](../ide/understanding-build-configurations.md)   
 [병렬로 여러 프로젝트 빌드](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md)



