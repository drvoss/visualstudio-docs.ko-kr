---
title: '방법: 디자이너를 사용 하 여 ClickOnce 응용 프로그램의 URL 활성화 해제 | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- disallowURLActivation
- URL activation, ClickOnce applications
- ClickOnce deployment, URL activation
ms.assetid: a337a582-e67c-409a-b52e-607cd1a8fc57
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 97357dd92525be2d36b552c5f3df49080f46d29b
ms.sourcegitcommit: 0e5289414d90a314ca0d560c0c3fe9c88cb2217c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/19/2018
ms.locfileid: "39152037"
---
# <a name="how-to-disable-url-activation-of-clickonce-applications-by-using-the-designer"></a>방법: 디자이너를 사용 하 여 ClickOnce 응용 프로그램의 URL 활성화를 사용 하지 않도록 설정
일반적으로 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 응용 프로그램은 웹 서버에서 설치 된 후에 즉시 자동으로 시작 됩니다. 보안상의 이유로이 동작을 사용 하지 않도록 설정 하 여 사용자가 응용 프로그램을 시작 하도록 설정할 수 있습니다 합니다 **시작** 메뉴 대신 합니다. 다음 절차에서는 URL 활성화를 사용하지 않도록 설정하는 방법에 대해 설명합니다.  
  
 이 방법은 웹 서버에서 사용자 컴퓨터에 설치된 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 응용 프로그램에 대해서만 사용할 수 있습니다. 해당 URL을 사용해 서만 시작할 수 있는 온라인 전용 응용 프로그램에 사용할 수 없습니다. 참조 및 설치 된 온라인 전용 응용 프로그램 간의 차이점에 대 한 자세한 내용은 [ClickOnce 배포 전략 선택](../deployment/choosing-a-clickonce-deployment-strategy.md)합니다.  
  
 이 절차에서는 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]합니다. 사용 하 여이 작업을 수행할 수도 있습니다는 [!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)]합니다. 자세한 내용은 [방법: ClickOnce 응용의 URL 활성화 해제](../deployment/how-to-disable-url-activation-of-clickonce-applications.md)합니다.  
  
## <a name="procedure"></a>프로시저  
  
#### <a name="to-disable-url-activation-for-your-application"></a>응용 프로그램의 URL 활성화를 사용하지 않도록 설정하려면  
  
1.  프로젝트 이름을 마우스 오른쪽 단추로 클릭 **솔루션 탐색기**, 클릭 **속성**합니다.  
  
2.  에 **속성** 페이지를 클릭 합니다 **게시** 탭 합니다.  
  
3.  **옵션**을 클릭합니다.  
  
4.  클릭 **매니페스트**합니다.  
  
5.  라는 레이블이 있는 확인란을 선택 **응용 프로그램 URL을 통해 활성화 되 고 차단**합니다.  
  
6.  응용 프로그램을 배포합니다.  
  
## <a name="see-also"></a>참고자료  
 [ClickOnce 응용 프로그램 게시](../deployment/publishing-clickonce-applications.md)