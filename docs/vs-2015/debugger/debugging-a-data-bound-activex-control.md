---
title: 데이터 바인딩된 ActiveX 컨트롤 디버깅 | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- data-bound controls, ActiveX
- ActiveX controls, debugging
- controls [Visual Studio], ActiveX
ms.assetid: 9f6e1f00-e25b-48a9-8484-7e67a1232461
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ae8863b8622987c0676646f45b5659945971c464
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51768872"
---
# <a name="debugging-a-data-bound-activex-control"></a>데이터 바인딩된 ActiveX 컨트롤 디버깅
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

데이터 소스 컨트롤에 바인딩될 ActiveX 컨트롤을 개발하는 경우에는 사용자의 컨테이너 응용 프로그램을 만들고 해당 컨테이너를 사용하여 ActiveX 컨트롤을 디버깅할 수 있습니다.  
  
 예를 들어, 대화 상자 기반 MFC 응용 프로그램을 만들고 대화 상자에 데이터 바인딩된 컨트롤과 데이터 소스 컨트롤을 넣을 수 있습니다. 이 MFC 응용 프로그램은 런타임 테스팅 및 데이터 바인딩된 ActiveX 컨트롤을 디버깅하는 컨테이너 실행 파일로 사용할 수 있습니다.  
  
## <a name="using-the-test-container"></a>테스트 컨테이너 사용  
 컨테이너를 쉽게 변경하여 컨트롤이나 컨테이너에 대한 다양한 인터페이스를 사용하려면, Activex Test Container를 디버그 세션의 실행 파일로 사용하십시오. ActiveX Test Container를 클릭 **옵션** 에서 합니다 **컨테이너** 다양 한 인터페이스를 사용 하도록 설정 하려면 메뉴. 자세한 내용은 [속성 및 이벤트 테스트 컨테이너를 사용 하 여 테스트](http://msdn.microsoft.com/library/626867cf-fe53-4c30-8973-55bb93ef3917)합니다.  
  
 디버깅할 때 컨테이너 코드를 한 단계씩 실행하려면 컨테이너의 디버그 버전을 사용하거나 ActiveX Test Container의 디버그 버전을 사용하십시오. 자세한 내용은 [TSTCON 샘플: ActiveX Control Test Container](http://msdn.microsoft.com/en-us/72fa40ef-27d3-400c-813f-10b03236e600)합니다.  
  
## <a name="see-also"></a>참고 항목  
 [COM 및 ActiveX 디버깅](../debugger/com-and-activex-debugging.md)   
 [ActiveX 컨트롤](http://msdn.microsoft.com/library/52aaec4d-3889-402e-b57d-758078f8ac57)



