---
title: '방법: 최종 사용자를 설치할 위치를 지정 합니다. | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- deploying applications [ClickOnce], specifying an installation URL
- URLs, specifying an installation URL
- installation, specifying installation an URL
- Installation URL property
ms.assetid: 04a804bf-ed55-4a7a-a1e6-f63ed99c0276
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 3139cb337428dfc0c14e5bae47e682ce169bc81d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68159135"
---
# <a name="how-to-specify-the-location-where-end-users-will-install-from"></a>방법: 최종 사용자의 설치 원본 위치 지정
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

게시 하는 경우는 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 응용 프로그램을 다운로드 하 고 응용 프로그램을 설치 하려면 사용자가 일 필요는 없습니다 처음 응용 프로그램을 게시 하는 위치입니다. 예를 들어, 일부 조직에서는 개발자는 응용 프로그램을 스테이징 서버를 게시할 수 있습니다 하 고 관리자는 웹 서버에 응용 프로그램을 이동 합니다.  
  
 이 경우 사용할 수 있습니다는 `Installation URL` 속성을 통해 응용 프로그램을 다운로드 하려면 사용자가 웹 서버를 지정 합니다. 응용 프로그램 매니페스트 업데이트를 검색할 위치를 알 수 있도록이 작업이 필요 합니다.  
  
 `Installation URL` 속성에 설정할 수 있습니다 합니다 **게시** 페이지를 **프로젝트 디자이너**합니다.  
  
 **참고** 는 `Installation URL` 사용 하 여 속성 설정할 수도 있습니다는 **PublishWizard**합니다. 자세한 내용은 [방법: 게시 마법사를 사용하여 ClickOnce 애플리케이션 게시](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)를 참조하세요.  
  
### <a name="to-specify-an-installation-url"></a>설치 URL을 지정 하려면  
  
1. **솔루션 탐색기**에서 프로젝트를 선택한 상태에서 **프로젝트** 메뉴에서 **속성**을 클릭합니다.  
  
2. **게시** 탭을 클릭합니다.  
  
3. 설치 URL 필드에는 형식을 사용 하 여 정규화 된 URL을 사용 하 여 설치 위치를 입력 http://www.microsoft.com/ApplicationName , 형식을 사용 하는 UNC 경로 또는 \\ \Server\ApplicationName 합니다.  
  
## <a name="see-also"></a>참고 항목  
 [방법: Visual Studio에서 파일을 복사 하는 위치 지정](../deployment/how-to-specify-where-visual-studio-copies-the-files.md)   
 [ClickOnce 응용 프로그램 게시](../deployment/publishing-clickonce-applications.md)   
 [방법: 게시 마법사를 사용하여 ClickOnce 애플리케이션 게시](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)
