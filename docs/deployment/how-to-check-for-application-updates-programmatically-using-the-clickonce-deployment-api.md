---
title: ClickOnce 배포 API를 사용 하 여 자동 앱 업데이트
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, updates
- application updates
ms.assetid: 1a886310-67c8-44e5-a382-c2f0454f887d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9f47c82311f26c5ca469f03783b785545bda2182
ms.sourcegitcommit: 117ece52507e86c957a5fd4f28d48a0057e1f581
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/28/2019
ms.locfileid: "66260828"
---
# <a name="how-to-check-for-application-updates-programmatically-using-the-clickonce-deployment-api"></a>방법: ClickOnce 배포 API를 사용하여 프로그래밍 방식으로 애플리케이션 업데이트 확인
ClickOnce 배포 후 응용 프로그램을 업데이트 하는 두 가지를 제공 합니다. 첫 번째 방법은 특정 간격에 따라 업데이트에 대 한 자동으로 확인 하도록 ClickOnce 배포를 구성할 수 있습니다. 두 번째 메서드를 사용 하는 코드를 작성할 수 있습니다는 <xref:System.Deployment.Application.ApplicationDeployment> 클래스 업데이트를 확인 하려면 사용자 요청과 같은 이벤트를 기반으로 합니다.

 다음 절차를 프로그래밍 방식으로 업데이트를 수행 하기 위한 몇 가지 코드를 표시 및 또한 프로그래밍 방식으로 업데이트 확인을 사용 하도록 설정 하 여 ClickOnce 배포를 구성 하는 방법에 설명 합니다.

 프로그래밍 방식으로 ClickOnce 응용 프로그램을 업데이트 하려면 업데이트의 위치를 지정 해야 합니다. 이 배포 공급자 라고도 합니다. 이 속성을 설정 하는 방법은 참조 하세요 [ClickOnce 업데이트 전략 선택](../deployment/choosing-a-clickonce-update-strategy.md)합니다.

> [!NOTE]
> 또한 한 위치에서 응용 프로그램을 배포 하지만 다른 업데이트 아래에 설명 된 기법을 사용할 수 있습니다. 자세한 내용은 [방법: 배포 업데이트를 위한 대체 위치 지정](../deployment/how-to-specify-an-alternate-location-for-deployment-updates.md)을 참조하세요.

### <a name="to-check-for-updates-programmatically"></a>프로그래밍 방식으로 업데이트를 확인 하려면

1. 원하는 명령줄 또는 시각적 개체 도구를 사용 하 여 새 Windows Forms 응용 프로그램을 만듭니다.

2. 단추, 메뉴 항목을 만들거나 다른 사용자 인터페이스 항목 하려는 사용자가 업데이트를 확인 하려면 선택 합니다. 해당 항목의 이벤트 처리기에서 확인 하 고 업데이트를 설치 하려면 다음 메서드를 호출 합니다.

     [!code-csharp[ClickOnceAPI#6](../deployment/codesnippet/CSharp/how-to-check-for-application-updates-programmatically-using-the-clickonce-deployment-api_1.cs)]
     [!code-cpp[ClickOnceAPI#6](../deployment/codesnippet/CPP/how-to-check-for-application-updates-programmatically-using-the-clickonce-deployment-api_1.cpp)]
     [!code-vb[ClickOnceAPI#6](../deployment/codesnippet/VisualBasic/how-to-check-for-application-updates-programmatically-using-the-clickonce-deployment-api_1.vb)]

3. 응용을 프로그램을 컴파일하십시오.

### <a name="use-mageexe-to-deploy-an-application-that-checks-for-updates-programmatically"></a>Mage.exe를 사용 하 여 프로그래밍 방식으로 업데이트를 확인 하는 응용 프로그램을 배포 하려면

- 에 설명 된 대로 Mage.exe를 사용 하 여 응용 프로그램을 배포 하기 위한 지침에 따라 [연습: 수동으로 ClickOnce 응용 프로그램을 배포](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)합니다. 배포 매니페스트를 생성 하는 Mage.exe를 호출할 때 명령줄 스위치를 사용 하도록 확인 `providerUrl`, ClickOnce 업데이트를 확인 하는 URL을 지정 하 고 있습니다. 응용 프로그램에서 업데이트 됩니다 [ http://www.adatum.com/MyApp ](http://www.adatum.com/MyApp), 예를 들어, 배포 매니페스트를 생성 하는를 호출 하 여 다음과 같이 표시 될 수 있습니다.

    ```cmd
    mage -New Deployment -ToFile WindowsFormsApp1.application -Name "My App 1.0" -Version 1.0.0.0 -AppManifest 1.0.0.0\MyApp.manifest -providerUrl http://www.adatum.com/MyApp/MyApp.application
    ```

### <a name="using-mageuiexe-to-deploy-an-application-that-checks-for-updates-programmatically"></a>MageUI.exe를 사용 하 여 프로그래밍 방식으로 업데이트를 확인 하는 응용 프로그램을 배포 하려면

- 에 설명 된 대로 Mage.exe를 사용 하 여 응용 프로그램을 배포 하기 위한 지침에 따라 [연습: 수동으로 ClickOnce 응용 프로그램을 배포](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)합니다. 에 **배포 옵션** 탭, 설정 합니다 **시작 위치** 필드 ClickOnce 업데이트를 확인 하는 응용 프로그램 매니페스트를 합니다. 에 **업데이트 옵션** 탭을 선택 취소 합니다 **이 응용 프로그램의 업데이트 확인** 확인란 합니다.

## <a name="net-framework-security"></a>.NET Framework 보안
 프로그래밍 방식으로 업데이트를 사용 하도록 응용 프로그램에 완전 신뢰 권한이 있어야 합니다.

## <a name="see-also"></a>참고자료
- [방법: 배포 업데이트를 위한 대체 위치를 지정 합니다.](../deployment/how-to-specify-an-alternate-location-for-deployment-updates.md)
- [ClickOnce 업데이트 전략 선택](../deployment/choosing-a-clickonce-update-strategy.md)
- [ClickOnce 애플리케이션 게시](../deployment/publishing-clickonce-applications.md)