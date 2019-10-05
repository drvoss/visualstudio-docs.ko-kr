---
title: 앱 (JavaScript) 새로 고침 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- JavaScript debugging, refreshing pages [Windows Store apps]
- debugging, refreshing pages [Windows Store apps]
- DOM Explorer, Refresh [Windows Store apps]
- Refresh [Windows Store apps]
ms.assetid: fd99ee60-fa94-46df-8b17-369f60bfd908
caps.latest.revision: 23
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b5b8be97212f4510002a78e6565fc9884930db89
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63446095"
---
# <a name="refresh-an-app-javascript"></a>앱 새로 고침(JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Windows 및 Windows Phone 적용 됩니다] (.. /Image/windows_and_phone_content.png "windows_and_phone_content")  
  
 디버깅 하 고 다음 JavaScript를 사용 하 여 선택 하 여 스토어 앱을 새로 고침 하는 동안 코드에는 변경할 수는 **새로 고침 Windows 앱** 단추를 **디버그** 도구 모음입니다. 이 단추를 선택하면 디버거를 중지하여 다시 시작하지 않고 응용 프로그램을 다시 로드합니다. 새로 고침 기능을 사용하면 HTML, CSS 및 JavaScript 코드를 수정하고 결과를 빠르게 확인할 수 있습니다. 이 기능은 Windows 스토어 및 Windows Phone 스토어 앱에서 모두 지원됩니다.  
  
 새로 고침을 수행하면 응용 프로그램 상태가 유지되지 않으며 응용 프로그램에 다음 변경 사항이 반영됩니다.  
  
- 패키지 매니페스트에서 지정한 이미지에 대한 변경을 포함하는 패키지 매니페스트 파일 변경.  
  
- SDK 참조 추가 또는 제거와 같은 참조 변경 또는 Windows 런타임 구성 요소에 대한 변경(.winmd 파일).  
  
- .resjson 파일의 문자열에 대한 변경과 같은 리소스 변경.  
  
- 경로 이름 변경, 새 프로젝트 파일 또는 삭제된 파일이 발생되는 프로젝트 파일 변경.  
  
- 선택한 디버깅 디바이스에 대한 변경 또는 파일의 패키지 작업(속성 창)에 대한 변경과 같은 프로젝트 및 항목 속성 변경.  
  
> [!IMPORTANT]
> 참조 또는 패키지 매니페스트를 변경하거나 앞의 목록에 지정된 기타 변경 사항을 수행한 경우, 디버거를 중지했다가 다시 시작해야 HTML, CSS 및 JavaScript 소스 파일이 업데이트됩니다.  
  
### <a name="to-refresh-an-app"></a>응용 프로그램을 새로 고치려면  
  
1. Visual Studio에서 탐색 응용 프로그램 프로젝트 템플릿을 사용하여 새 프로젝트를 만듭니다.  
  
     새 프로젝트는 Windows 스토어 앱, Windows Phone 스토어 앱 또는 유니버설 앱일 수 있습니다.  
  
2. Visual Studio에서 템플릿을 열어 둔 채 디버그 대상을 선택합니다.  
  
     Windows Phone 프로젝트가 현재 시작 프로젝트인 경우 디버그 대상으로 Windows Phone 에뮬레이터를 선택합니다. 선택이 고, 그렇지 **시뮬레이터** 하거나 **로컬 컴퓨터**합니다.  
  
     ![디버그 대상 목록 선택](../debugger/media/js-select-target.png "JS_Select_Target")  
  
3. F5 키를 눌러 디버그 모드에서 응용 프로그램을 실행합니다.  
  
4. Visual Studio로 전환합니다(F12 키 누름).  
  
5. **솔루션 탐색기**를 **페이지** > **홈** 폴더 home.html을 엽니다.  
  
6. 다음에서  
  
    ```html  
    Welcome to yourAppName!  
    ```  
  
     다음과 같은 다른 제목 텍스트로 변경  
  
    ```html  
    Hello!  
    ```  
  
7. 클릭 합니다 **새로 고침 Windows 앱** 같이 단추: ![Windows 응용 프로그램 단추를 새로 고칠](../debugger/media/js-refresh.png "JS_Refresh")합니다. 또는 F4 키를 누릅니다.  
  
8. 응용 프로그램으로 전환합니다. 디버거를 다시 시작하지 않아도 응용 프로그램이 다시 로드되고 새 페이지 제목이 표시됩니다.  
  
## <a name="see-also"></a>참고 항목  
 [빠른 시작: HTML 및 CSS 디버그](../debugger/quickstart-debug-html-and-css.md)
