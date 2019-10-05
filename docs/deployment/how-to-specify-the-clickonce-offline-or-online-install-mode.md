---
title: '방법: 지정 ClickOnce 오프 라인 또는 온라인 설치 모드 | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, specifying install mode
- install mode
- online applications
- offline applications
- ClickOnce install mode
ms.assetid: 0aee5fc1-e966-4bda-9b8f-d9997aeaa779
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a050724733ad87d0c583639fe3b0acfd2d6299f7
ms.sourcegitcommit: 748d9cd7328a30f8c80ce42198a94a4b5e869f26
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67890575"
---
# <a name="how-to-specify-the-clickonce-offline-or-online-install-mode"></a>방법: ClickOnce 오프라인 또는 온라인 설치 모드 지정
합니다 `Install Mode` 에 대 한는 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 응용 프로그램 여부를 결정은 응용 프로그램 사용 가능한 오프 라인 또는 온라인입니다. 선택 하는 경우 **응용 프로그램은 온라인**, 사용자에 액세스할 수 있어야 합니다 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 위치 (웹 페이지 또는 파일 공유) 응용 프로그램을 실행 하기 위해 게시 합니다. 선택 하는 경우 **응용 프로그램을 오프 라인으로**, 항목을 추가 하는 응용 프로그램을 **시작** 메뉴 및 **프로그램 추가 / 제거** 대화 상자, 사용자는 연결 되지 않은 경우 응용 프로그램을 실행할 수 있습니다.

`Install Mode` 에서 설정할 수 있습니다 합니다 **게시** 페이지를 **프로젝트 디자이너**합니다.

> [!NOTE]
> `Install Mode` 게시 마법사를 사용 하 여 설정할 수도 있습니다. 자세한 내용은 [방법: 게시 마법사를 사용하여 ClickOnce 애플리케이션 게시](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)를 참조하세요.

### <a name="to-make-a-clickonce-application-available-online-only"></a>ClickOnce 응용 프로그램을 사용할 수 있도록 온라인만

1. **솔루션 탐색기**에서 프로젝트를 선택한 상태에서 **프로젝트** 메뉴에서 **속성**을 클릭합니다.

2. **게시** 탭을 클릭합니다.

3. 에 **설치 모드 및 설정** 영역에서 클릭 합니다 **응용 프로그램은 온라인** 옵션 단추.

### <a name="to-make-a-clickonce-application-available-online-or-offline"></a>온라인 또는 오프 라인으로 ClickOnce 응용 프로그램을 사용할 수 있도록 하려면

1. **솔루션 탐색기**에서 프로젝트를 선택한 상태에서 **프로젝트** 메뉴에서 **속성**을 클릭합니다.

2. **게시** 탭을 클릭합니다.

3. 에 **설치 모드 및 설정** 영역에서 클릭 합니다 **응용 프로그램을 오프 라인으로** 옵션 단추.

     설치에 응용 프로그램 항목을 추가 합니다 **시작** 메뉴와 **프로그램 추가 / 제거** 제어판에서.

## <a name="see-also"></a>참고자료
- [ClickOnce 애플리케이션 게시](../deployment/publishing-clickonce-applications.md)
- [방법: 게시 마법사를 사용하여 ClickOnce 애플리케이션 게시](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)
- [ClickOnce 배포 전략 선택](../deployment/choosing-a-clickonce-deployment-strategy.md)