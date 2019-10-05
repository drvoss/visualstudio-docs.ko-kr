---
title: ClickOnce 응용 프로그램에 대 한 기본 웹 페이지 사용자 지정
ms.date: 11/04/2016
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 66d304be4e2435b6ec1ecafe8aeb473b83fa1033
ms.sourcegitcommit: 117ece52507e86c957a5fd4f28d48a0057e1f581
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/28/2019
ms.locfileid: "66263328"
---
# <a name="how-to-customize-the-default-web-page-for-a-clickonce-application"></a>방법: ClickOnce 애플리케이션의 기본 웹 페이지 사용자 지정
ClickOnce 응용 프로그램을 웹에 게시할 때 웹 페이지를 자동으로 생성 되어 응용 프로그램과 함께 게시 합니다. 기본 페이지에는 응용 프로그램 및 응용 프로그램을 설치 하거나 필수 구성 요소를 설치 하거나 MSDN에서 도움말에 액세스 하는 링크의 이름을 포함 합니다.

> [!NOTE]
> 페이지를 볼 컴퓨터 및 내용에 따라 페이지에 표시 되는 실제 링크를 포함 하는 필수 구성 요소입니다.

 웹 페이지의 기본 이름은 *Publish.htm*;에서 이름을 변경할 수 있습니다 합니다 **프로젝트 디자이너**합니다. 자세한 내용은 [방법: ClickOnce 애플리케이션의 게시 페이지 지정](../deployment/how-to-specify-a-publish-page-for-a-clickonce-application.md)을 참조하세요.

 합니다 *Publish.htm* 보다 최신 버전이 있는 경우에 웹 페이지를 게시 합니다.

> [!NOTE]
> 변경한 사용자 **게시** 설정에 영향을 주지 것입니다는 *Publish.htm* 페이지에서 한 가지 예외로: 필수 조건 목록에는 추가 하거나 처음 게시 한 후 필수 구성 요소를 제거 하는 경우 더 이상 정확 하 게 됩니다. 변경 내용을 반영 하도록 필수 구성 요소 링크에 대 한 텍스트를 편집 해야 합니다.

### <a name="to-customize-the-publish-web-page"></a>게시 웹 페이지 사용자 지정 하려면

1. 웹 위치를 ClickOnce 응용 프로그램을 게시 합니다. 자세한 내용은 [방법: 게시 마법사를 사용하여 ClickOnce 애플리케이션 게시](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)를 참조하세요.

2. 웹 서버에서 엽니다는 *Publish.htm* Visual Web Designer 또는 다른 HTML 편집기에서 파일입니다.

3. 필요에 따라 페이지를 사용자 지정 하 고 저장 합니다.

4. 선택 사항입니다. Visual Studio를에서 지정 된 게시 웹 페이지를 덮어쓰지 않도록 하려면 선택 취소 **자동으로 배포 웹 페이지를 생성 모든 게시** 에 **게시 옵션** 대화 상자.

## <a name="see-also"></a>참고자료
- [ClickOnce 보안 및 배포](../deployment/clickonce-security-and-deployment.md)
- [ClickOnce 애플리케이션 게시](../deployment/publishing-clickonce-applications.md)
- [방법: ClickOnce 응용 프로그램을 사용 하 여 필수 구성 요소 설치](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md)
- [방법: ClickOnce 애플리케이션의 게시 페이지 지정](../deployment/how-to-specify-a-publish-page-for-a-clickonce-application.md)