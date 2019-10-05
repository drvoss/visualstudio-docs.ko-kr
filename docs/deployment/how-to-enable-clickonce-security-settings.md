---
title: '방법: ClickOnce 보안 설정 사용 | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- security [Visual Studio], ClickOnce applications
- ClickOnce deployment, security settings
- security settings, ClickOnce deployment
ms.assetid: 73cd3e9d-cd72-4ad2-8cae-94d6bb6b01e0
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e52acc18aa18873076df3d02071616c0399b1f33
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63407128"
---
# <a name="how-to-enable-clickonce-security-settings"></a>방법: ClickOnce 보안 설정 사용
응용 프로그램을 게시 하기 위해 ClickOnce 응용 프로그램에 대 한 코드 액세스 보안을 사용할 수 있어야 합니다. 게시 마법사를 사용 하 여 응용 프로그램을 게시할 때 자동으로 수행 됩니다.

 일부 경우에 코드 액세스 보안을 사용 하도록 설정 하면 성능에 영향을 빌드하거나 응용 프로그램을 디버깅 하는 경우 이러한 경우에 일시적으로 보안 설정을 사용 하지 않도록 설정 하려고 할 수 있습니다.

 ClickOnce 보안 설정 사용 하거나 사용 하지 않도록 설정 수는 **보안** 페이지의 **프로젝트 디자이너**합니다.

### <a name="to-enable-clickonce-security-settings"></a>ClickOnce 보안 설정을 사용 하도록 설정

1. **솔루션 탐색기**에서 프로젝트를 선택한 상태에서 **프로젝트** 메뉴에서 **속성**을 클릭합니다.

2. **보안** 탭을 클릭합니다.

3. **ClickOnce 보안 설정 사용** 확인란을 선택합니다.

     이제 보안 페이지에서 응용 프로그램에 대 한 보안 설정을 지정할 수 있습니다.

    > [!NOTE]
    > 이 확인란을 사용 하 여 응용 프로그램을 게시할 때마다 자동으로 선택 됩니다 합니다 **게시** 마법사.

### <a name="to-disable-clickonce-security-settings"></a>ClickOnce 보안 설정 사용 안 함

1. **솔루션 탐색기**에서 프로젝트를 선택한 상태에서 **프로젝트** 메뉴에서 **속성**을 클릭합니다.

2. **보안** 탭을 클릭합니다.

3. 선택을 취소 합니다 **ClickOnce 보안 설정 사용** 확인란 합니다.

     응용 프로그램이 완전 신뢰 보안 설정과; 실행 수 에 있는 모든 설정 합니다 **보안** 페이지는 무시 됩니다.

    > [!NOTE]
    > 게시 마법사를 사용 하 여 응용 프로그램을 게시할 때마다가 확인란 선택 됩니다. 응용 프로그램이 게시 된 후에 다시 지워야 합니다.

## <a name="see-also"></a>참고자료
- [ClickOnce 애플리케이션 보안](../deployment/securing-clickonce-applications.md)
- [ClickOnce 애플리케이션의 코드 액세스 보안](../deployment/code-access-security-for-clickonce-applications.md)
