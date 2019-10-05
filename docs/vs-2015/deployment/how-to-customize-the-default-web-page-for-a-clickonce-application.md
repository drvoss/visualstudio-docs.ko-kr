---
title: '방법: ClickOnce 응용 프로그램에 대 한 기본 웹 페이지를 사용자 지정 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- Publish.htm Web page
- ClickOnce deployment default Web page
- deploying applications [ClickOnce], publishing
- publishing, ClickOnce
ms.assetid: 418de18c-bee9-4f24-9cd9-0252d175070d
caps.latest.revision: 16
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 4ec63fe5ae4b99252321b86b44066c46842a0851
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63433903"
---
# <a name="how-to-customize-the-default-web-page-for-a-clickonce-application"></a>방법: ClickOnce 애플리케이션의 기본 웹 페이지 사용자 지정
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

ClickOnce 응용 프로그램을 웹에 게시할 때 웹 페이지를 자동으로 생성 되어 응용 프로그램과 함께 게시 합니다. 기본 페이지에는 응용 프로그램 및 응용 프로그램을 설치 하거나 필수 구성 요소를 설치 하거나 MSDN에서 도움말에 액세스 하는 링크의 이름을 포함 합니다.  
  
> [!NOTE]
> 페이지를 볼 컴퓨터 및 내용에 따라 페이지에 표시 되는 실제 링크를 포함 하는 필수 구성 요소입니다.  
  
 웹 페이지의 기본 이름은 Publish.htm; 이름을 변경할 수 있습니다 합니다 **프로젝트 디자이너**합니다. 자세한 내용은 [방법: ClickOnce 응용 프로그램의 게시 페이지 지정](../deployment/how-to-specify-a-publish-page-for-a-clickonce-application.md)합니다.  
  
 Publish.htm 웹 페이지 보다 최신 버전이 있는 경우에 게시 됩니다.  
  
> [!NOTE]
> 변경한 사용자 **게시** 설정 Publish.htm 페이지는 한 가지 예외를 사용 하 여 영향을 주지 것입니다:를 추가 하거나 처음 게시 한 후 필수 구성 요소를 제거 하는 경우 필수 구성 요소 목록을 더 이상 정확 하 게 합니다. 변경 내용을 반영 하도록 필수 구성 요소 링크에 대 한 텍스트를 편집 해야 합니다.  
  
### <a name="to-customize-the-publish-web-page"></a>게시 웹 페이지 사용자 지정 하려면  
  
1. 웹 위치를 ClickOnce 응용 프로그램을 게시 합니다. 자세한 내용은 [방법: 게시 마법사를 사용하여 ClickOnce 애플리케이션 게시](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)를 참조하세요.  
  
2. 웹 서버에 Visual Web Designer 또는 다른 HTML 편집기에서 Publish.htm 파일을 엽니다.  
  
3. 필요에 따라 페이지를 사용자 지정 하 고 저장 합니다.  
  
4. 선택 사항입니다. Visual Studio를에서 지정 된 게시 웹 페이지를 덮어쓰지 않도록 하려면 선택 취소 **자동으로 배포 웹 페이지 생성 모든 게시** 게시 옵션 대화 상자에서.  
  
## <a name="see-also"></a>참고 항목  
 [ClickOnce 보안 및 배포](../deployment/clickonce-security-and-deployment.md)   
 [ClickOnce 응용 프로그램 게시](../deployment/publishing-clickonce-applications.md)   
 [방법: ClickOnce 응용 프로그램을 사용 하 여 필수 구성 요소 설치](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md)   
 [방법: ClickOnce 애플리케이션의 게시 페이지 지정](../deployment/how-to-specify-a-publish-page-for-a-clickonce-application.md)
