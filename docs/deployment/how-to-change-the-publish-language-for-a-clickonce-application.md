---
title: ClickOnce 응용 프로그램에 대 한 언어를 게시 하는 변경
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- Publish language property
- ClickOnce deployment, changing publish language
- publishing, ClickOnce
ms.assetid: ef5024c4-cda1-4970-bc75-32a2a10c92c3
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e80a65b65d75d925decdf60b633a7d51ea9bafce
ms.sourcegitcommit: 117ece52507e86c957a5fd4f28d48a0057e1f581
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/28/2019
ms.locfileid: "66263170"
---
# <a name="how-to-change-the-publish-language-for-a-clickonce-application"></a>방법: ClickOnce 애플리케이션의 게시 언어 변경

게시 하는 경우는 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 응용 프로그램 사용자 인터페이스 언어 및 개발 컴퓨터의 문화권을 기본값으로 설치 중에 표시 합니다. 지역화 된 응용 프로그램을 게시 하는 경우에 언어 및 지역화 된 버전과 일치 하는 문화권을 지정 하는 것이 해야 합니다. 에 의해 결정 되기는 `Publish language` 프로젝트에 대 한 속성입니다.

`Publish language` 에서 속성을 설정할 수 있습니다 합니다 **게시 옵션** 에서 액세스할 수 있는 대화 상자를 **게시** 페이지를 **프로젝트 디자이너**합니다.

> [!NOTE]
> 표시되는 대화 상자와 메뉴 명령은 활성 설정이나 버전에 따라 도움말에서 설명하는 것과 다를 수 있습니다. 설정을 변경하려면 **도구** 메뉴에서 **설정 가져오기 및 내보내기** 를 선택합니다. 자세한 내용은 [재설정 설정](../ide/environment-settings.md#reset-settings)을 참조하세요.

## <a name="to-change-the-publish-language"></a>게시 언어를 변경 하려면

1. **솔루션 탐색기**에서 프로젝트를 선택한 상태에서 **프로젝트** 메뉴에서 **속성**을 클릭합니다.

2. **게시** 탭을 클릭합니다.

3. 클릭 합니다 **옵션** 버튼을 클릭 합니다 **게시 옵션** 대화 상자.

4. 클릭 **설명을**합니다.

5. 에 **게시 옵션** 대화 상자, 언어 및 문화권에서 **게시 언어** 한 다음 클릭 하 고 드롭 다운 목록 **확인**합니다.

## <a name="see-also"></a>참고자료

- [ClickOnce 애플리케이션 게시](../deployment/publishing-clickonce-applications.md)
- [방법: 게시 마법사를 사용하여 ClickOnce 애플리케이션 게시](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)