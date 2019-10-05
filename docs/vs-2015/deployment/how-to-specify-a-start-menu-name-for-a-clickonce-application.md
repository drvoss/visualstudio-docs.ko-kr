---
title: '방법: ClickOnce 응용 프로그램에 대 한 시작 메뉴 이름 지정 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- Start menu resource name
- Start menu name
- ClickOnce deployment, Start menu name
ms.assetid: 4b5183b2-2fd4-4433-9310-4a73bb12c4e3
caps.latest.revision: 19
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 30bb4050399bf7a6d9120f7e5454b26ce505af35
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68149765"
---
# <a name="how-to-specify-a-start-menu-name-for-a-clickonce-application"></a>방법: ClickOnce 애플리케이션의 시작 메뉴 이름 지정
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

경우는 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 응용 프로그램 사용 하 여 온라인 및 오프 라인 설치를 항목에 추가 됩니다 합니다 **시작** 메뉴 및 **프로그램 추가 / 제거** 목록입니다. 기본적으로 표시 이름은 응용 프로그램 어셈블리의 이름과 동일 하지만 설정 하 여 표시 이름을 변경할 수 있습니다 **Product name** 에 **게시 옵션** 대화 상자.  
  
 **제품 이름** 표시할 항목의 이름이 됩니다 publish.htm 페이지에서, 설치 된 오프 라인 응용 프로그램에 대 한는 **시작** 메뉴에 표시 되는 이름 수도 있습니다 **추가 또는 제거 프로그램**합니다.  
  
 **게시자 이름** 위의 publish.htm 페이지에 표시 됩니다 **Product name**, 설치 된 오프 라인 응용 프로그램에 대 한도 것에서 응용 프로그램의 아이콘을 포함 하는 폴더의 이름을 **시작**  메뉴.  
  
 설정할 수 있습니다는 **제품 이름** 및 **게시자 이름** 속성에는 **게시 옵션** 에서 사용할 수 있는 대화 상자를 **게시** 페이지 **프로젝트 디자이너**합니다.  
  
### <a name="to-specify-a-start-menu-name"></a>시작 메뉴 이름 지정  
  
1. **솔루션 탐색기**에서 프로젝트를 선택한 상태에서 **프로젝트** 메뉴에서 **속성**을 클릭합니다.  
  
2. **게시** 탭을 클릭합니다.  
  
3. 클릭 합니다 **옵션** 버튼을 클릭 합니다 **게시 옵션** 대화 상자.  
  
4. 클릭 **설명을**합니다.  
  
5. 에 **게시 옵션** 대화 상자에 표시할 이름을 입력 합니다 **Product name**합니다.  
  
6. 게시자 이름을 입력할 수는 필요에 따라 **게시자 이름**합니다.  
  
## <a name="see-also"></a>참고 항목  
 [ClickOnce 응용 프로그램 게시](../deployment/publishing-clickonce-applications.md)   
 [방법: 게시 마법사를 사용하여 ClickOnce 애플리케이션 게시](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)
