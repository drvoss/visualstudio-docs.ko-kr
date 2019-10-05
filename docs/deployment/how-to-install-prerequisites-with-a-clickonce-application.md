---
title: '방법: ClickOnce 응용 프로그램을 사용 하 여 필수 구성 요소 설치 | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- deploying applications [ClickOnce], prerequisites
- prerequisites, ClickOnce
- components, bootstrapping
ms.assetid: e964fca5-fdfd-47cf-a1c9-7fb96b1c88b5
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 047ac897931cbb93d8a06406e300d39cd83a9fe4
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63406773"
---
# <a name="how-to-install-prerequisites-with-a-clickonce-application"></a>방법: ClickOnce 애플리케이션의 필수 구성 요소 설치
모든 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 여러 응용 프로그램에서는 다른 필수 구성 요소도; 응용 프로그램 실행 되기 전에 올바른 버전의.NET Framework를 컴퓨터에 설치 되어 있는지 필요 합니다. 게시 하는 경우는 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 응용 프로그램을 응용 프로그램과 함께 패키지로 될 필수 구성 요소 집합을 선택할 수 있습니다. 설치 과정에서 검사를 수행할 경우 이미 존재 합니다; 확인 하려면 각 필수 구성 요소에 대 한 설치 하기 전에 설치는 되지 않은 경우는 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 응용 프로그램입니다.

 대신 패키징하고 필수 구성 요소 게시 구성 요소에 대 한 다운로드 위치를 지정할 수도 있습니다. 예를 들어, 게시 하는 모든 응용 프로그램을 사용 하 여 필수 구성 요소를 포함 하는 대신 사용할 수 있습니다 중앙 집중식된 파일 공유 또는 모든 프로그램 필수 구성 요소에 대 한 설치 관리자를 포함 하는 웹 위치-설치 시 구성 요소 다운로드 되 고 해당 위치에서 설치 합니다.

> [!IMPORTANT]
> 첫 번째 게시 하기 전에 개발 컴퓨터에 필수 구성 요소 설치 관리자 패키지를 추가 해야 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 응용 프로그램입니다. 자세한 내용은 [방법: ClickOnce 애플리케이션의 필수 구성 요소 포함](../deployment/how-to-include-prerequisites-with-a-clickonce-application.md)을 참조하세요.

 필수 구성 요소에서 관리 되는 **필수 구성 요소** 에서 액세스할 수 있는 대화 상자를 **게시** 창의 **프로젝트 디자이너**합니다.

> [!NOTE]
> 필수 구성 요소에 미리 지정 된 목록 외에도 목록에 고유한 구성 요소를 추가할 수 있습니다. 자세한 내용은 [부트스트래퍼 패키지 만들기](../deployment/creating-bootstrapper-packages.md)합니다.

### <a name="to-specify-prerequisites-to-install-with-a-clickonce-application"></a>ClickOnce 응용 프로그램을 사용 하 여 설치할 필수 구성 요소를 지정 하려면

1. **솔루션 탐색기**에서 프로젝트를 선택한 상태에서 **프로젝트** 메뉴에서 **속성**을 클릭합니다.

2. 선택 된 **게시** 창입니다.

3. 클릭 합니다 **필수 구성 요소** 버튼을 클릭 합니다 **필수 구성 요소** 대화 상자.

4. **필수 구성 요소** 대화 상자에서 **필수 구성 요소를 설치하기 위한 설치 프로그램 만들기** 확인란이 선택되어 있는지 확인합니다.

5. 에 **필수 구성 요소** 목록에서 구성 요소를 설치 하 고 클릭 하려는 하 **확인**합니다.

     선택한 구성 요소 패키지 되어 응용 프로그램과 함께 게시 합니다.

### <a name="to-specify-a-different-download-location-for-prerequisites"></a>필수 구성 요소에 대 한 서로 다른 다운로드 위치를 지정 하려면

1. **솔루션 탐색기**에서 프로젝트를 선택한 상태에서 **프로젝트** 메뉴에서 **속성**을 클릭합니다.

2. 선택 된 **게시** 창입니다.

3. 클릭 합니다 **필수 구성 요소** 버튼을 클릭 합니다 **필수 구성 요소** 대화 상자.

4. **필수 구성 요소** 대화 상자에서 **필수 구성 요소를 설치하기 위한 설치 프로그램 만들기** 확인란이 선택되어 있는지 확인합니다.

5. 에 **필수 구성 요소에 대 한 설치 위치를 지정** 섹션에서 **다음 위치에서 필수 조건 다운로드**합니다.

6. 또는 드롭다운 목록에서 위치를 선택 하 고, URL, 파일 경로 또는 FTP 위치를 입력 하 고, 클릭 **확인 합니다.**

    > [!NOTE]
    > 지정된 된 구성 요소에 대 한 설치 관리자가 지정된 된 위치에 있는지 확인 해야 합니다.

## <a name="see-also"></a>참고자료
- [ClickOnce 애플리케이션 게시](../deployment/publishing-clickonce-applications.md)
- [방법: 게시 마법사를 사용하여 ClickOnce 애플리케이션 게시](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)