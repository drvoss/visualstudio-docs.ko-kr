---
title: '방법: WPF 추적 정보 표시 | Microsoft Docs'
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
- WPF, debugging
- debugging, WPF
ms.assetid: be3c6859-06e1-459e-9fd0-46375b5f55ef
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0a91d9f1f58a6905d50e14351bbbaf6fe732c60f
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51771242"
---
# <a name="how-to-display-wpf-trace-information"></a>방법: WPF 추적 정보 표시
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] WPF 응용 프로그램에서 디버그 추적 정보를 수신 하 고 해당 정보를 표시할 수는 **출력** 창입니다. 디버그 추적 정보를 표시 하려면 WPF 추적을 사용할 수 있어야 합니다.  
  
 WPF 추적 설정에는 App.Config 파일을 사용하거나 <xref:System.Diagnostics.PresentationTraceSources> 클래스를 통한 프로그래밍 방식을 사용할 수 있습니다. WPF 추적을 사용 하도록 쉽게 사용 하는 것은 **옵션** 창입니다. 응용 프로그램에 대한 WPF 추적은 지원되지 않습니다.  
  
### <a name="to-enable-or-customize-wpf-trace-information"></a>WPF 추적 정보를 사용하도록 설정하거나 사용자 지정하려면  
  
1.  **도구** 메뉴에서 **옵션**을 선택합니다.  
  
2.  에 **옵션** 왼쪽 상자에서 대화 상자를 열어 합니다 **디버깅** 노드.  
  
3.  아래 **디버깅**, 클릭 **출력 창**합니다.  
  
4.  아래 **일반 출력 설정**를 선택 **모든 디버그 출력**합니다.  
  
5.  오른쪽 상자에서 찾습니다 **WPF 추적 설정**합니다.  
  
6.  엽니다는 **WPF 추적 설정** 노드.  
  
7.  아래 **WPF 추적 설정**를 사용 하도록 설정 하려는 설정의 범주를 클릭 합니다. (예를 들어 **데이터 바인딩**).  
  
     설정 열 드롭다운 목록 컨트롤 옆에 나타나는 **데이터 바인딩** 범주를 클릭 하거나 합니다.  
  
8.  드롭다운 목록을 클릭 하 고 표시할 추적 정보의 유형을 선택 합니다. **모든**, **위험**, **오류**, **경고**,  **정보**, **Verbose**, 또는 **ActivityTracing**합니다.  
  
     **중요 한** 중요 이벤트만 추적 하도록 설정 합니다.  
  
     **오류** 중요 및 오류 이벤트를 추적 하도록 설정 합니다.  
  
     **경고** 은 중요, 오류, 추적 및 이벤트를 경고 하도록 설정 합니다.  
  
     **정보** 중요, 오류, 경고 및 정보 이벤트를 추적 하도록 설정 합니다.  
  
     **Verbose** 중요, 오류, 경고, 정보 및 자세한 정보 표시 이벤트를 추적 하도록 설정 합니다.  
  
     **ActivityTracing** 중지, 시작, 일시 중단, 전송 및 다시 시작 이벤트를 추적 하도록 설정 합니다.  
  
     이러한 추적 정보 수준의 의미에 대한 자세한 내용은 <xref:System.Diagnostics.SourceLevels>를 참조하십시오.  
  
9. **확인**을 클릭합니다.  
  
### <a name="to-disable-wpf-trace-information"></a>WPF 추적 정보를 사용하지 않도록 설정하려면  
  
1.  **도구** 메뉴에서 **옵션**을 선택합니다.  
  
2.  에 **옵션** 왼쪽 상자에서 대화 상자를 열어 합니다 **디버깅** 노드.  
  
3.  아래 **디버깅**, 클릭 **출력 창**합니다.  
  
4.  오른쪽 상자에서 찾습니다 **WPF 추적 설정**합니다.  
  
5.  엽니다는 **WPF 추적 설정** 노드.  
  
6.  아래 **WPF 추적 설정**를 사용 하도록 설정 하려는 설정의 범주를 클릭 합니다. (예를 들어 **데이터 바인딩**).  
  
     설정 열 드롭다운 목록 컨트롤 옆에 나타나는 **데이터 바인딩** 범주를 클릭 하거나 합니다.  
  
7.  드롭다운 목록을 클릭 하 고 선택 **해제**합니다.  
  
8.  **확인**을 클릭합니다.  
  
## <a name="see-also"></a>참고 항목  
 [WPF 디버그](../debugger/debugging-wpf.md)



