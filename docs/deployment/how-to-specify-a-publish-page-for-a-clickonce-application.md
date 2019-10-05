---
title: '방법: ClickOnce 응용 프로그램의 게시 페이지 지정 | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- deploying applications [ClickOnce], specifying publish page
- Publish Page property
- publishing, ClickOnce
- ClickOnce deployment, specifying publish page
ms.assetid: 9d70eebb-bdee-4b42-8e7e-7a07e199bdf7
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 29d83dd1a232ae1cf0437c1ab6d4662acef2900d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62928344"
---
# <a name="how-to-specify-a-publish-page-for-a-clickonce-application"></a>방법: ClickOnce 애플리케이션의 게시 페이지 지정
게시 하는 경우는 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 응용 프로그램을 기본 웹 페이지 (publish.htm)를 생성 되 고 응용 프로그램과 함께 게시 합니다. 이 페이지에 설명 하는 도움말 항목에 대 한 링크 및 응용 프로그램 및/또는 필수 구성 요소를 설치 하기 위한 링크를 사용 하는, 응용 프로그램의 이름을 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]입니다. 합니다 **게시 페이지** 프로젝트에 대 한 속성을 사용 하면 웹 페이지의 이름을 지정할 수 있습니다 프로그램 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 응용 프로그램입니다.

 게시 페이지 지정 되 면를 게시 하면 다음에 해당 복사할 게시 위치입니다. 해당 덮어쓰지 않고 다시 게시 하는 경우. 페이지의 모양을 사용자 지정 하려는 경우 변경 내용을 손실에 대 한 걱정 없이를 수행할 수 있습니다. 자세한 내용은 [방법: ClickOnce 기본 웹 페이지 사용자 지정](../deployment/how-to-customize-the-default-web-page-for-a-clickonce-application.md)을 참조하세요.

 **게시 페이지** 속성에서 설정할 수 있습니다 합니다 **게시 옵션** 에서 액세스할 수 있는 대화 상자를 **게시** 창은 **프로젝트 디자이너**.

### <a name="to-specify-a-custom-web-page-for-a-clickonce-application"></a>ClickOnce 응용 프로그램에 대 한 사용자 지정 웹 페이지를 지정 하려면

1. **솔루션 탐색기**에서 프로젝트를 선택한 상태에서 **프로젝트** 메뉴에서 **속성**을 클릭합니다.

2. 선택 된 **게시** 창입니다.

3. 클릭 합니다 **옵션** 버튼을 클릭 합니다 **게시 옵션** 대화 상자.

4. 클릭 **배포**합니다.

5. 에 **게시 옵션** 대화 상자에서 확인 합니다 **게시 한 후 웹 페이지를 열고 배포** 확인란을 선택 (선택 됩니다 기본적으로).

6. 에 **배포 웹 페이지** 상자, 웹 페이지에 대 한 이름을 입력 한 다음 클릭 **확인**합니다.

### <a name="to-prevent-the-publish-page-from-launching-each-time-you-publish"></a>게시 페이지 게시 될 때마다 시작 하지 않도록 설정 하려면

1. **솔루션 탐색기**에서 프로젝트를 선택한 상태에서 **프로젝트** 메뉴에서 **속성**을 클릭합니다.

2. 선택 된 **게시** 창입니다.

3. 클릭 합니다 **옵션** 버튼을 클릭 합니다 **게시 옵션** 대화 상자.

4. 클릭 **배포**합니다.

5. 에 **게시 옵션** 대화 상자, 일반 합니다 **게시 한 후 웹 페이지를 열고 배포** 확인란 합니다.

## <a name="see-also"></a>참고자료
- [ClickOnce 애플리케이션 게시](../deployment/publishing-clickonce-applications.md)
- [방법: 게시 마법사를 사용하여 ClickOnce 애플리케이션 게시](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)
- [방법: ClickOnce 기본 웹 페이지 사용자 지정](../deployment/how-to-customize-the-default-web-page-for-a-clickonce-application.md)