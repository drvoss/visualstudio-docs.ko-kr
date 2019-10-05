---
title: '연습: 사용 하 여 SDK 만들기 C# 또는 Visual Basic | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: ef96a249-5eef-402a-a8d5-d74cb49239bd
caps.latest.revision: 21
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 44b1083a9de4a5fe3e86ae37814f6df85f8c1e56
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63435501"
---
# <a name="walkthrough-creating-an-sdk-using-c-or-visual-basic"></a>연습: C# 또는 Visual Basic을 사용하여 SDK 만들기
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

이 연습에서는 Visual C#을 사용 하 여 간단한 수학 라이브러리 SDK를 만들고 다음 SDK는 Visual Studio 확장 (VSIX)로 패키지 하는 방법에 알아봅니다. 다음 절차를 완료 합니다.  
  
- [SimpleMath Windows 런타임 구성 요소를 만들려면](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md#createClassLibrary)  
  
- [SimpleMathVSIX 확장 프로젝트를 만들려면](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md#createVSIX)  
  
- [클래스 라이브러리를 사용 하는 샘플 앱을 만들려면](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md#createSample)  
  
## <a name="prerequisites"></a>전제 조건  
 이 연습을 수행하려면 Visual Studio SDK를 설치해야 합니다. 자세한 내용은 [Visual Studio SDK](../extensibility/visual-studio-sdk.md)합니다.  
  
## <a name="createClassLibrary"></a> SimpleMath Windows 런타임 구성 요소를 만들려면  
  
1. 메뉴 모음에서 **파일**, **새로 만들기**하십시오 **새 프로젝트**.  
  
2. 템플릿 목록에서 확장 **Visual C#** 또는 **Visual Basic**를 선택 합니다 **Windows 스토어** 노드를 선택한 후는 **Windows 런타임 구성 요소** 템플릿.  
  
3. 에 **이름** 상자에서 지정 **SimpleMath**를 선택한 후는 **확인** 단추입니다.  
  
4. **솔루션 탐색기**에 대 한 바로 가기 메뉴를 열고 합니다 **SimpleMath** 프로젝트 노드를 선택한 후 **속성**합니다.  
  
5. 이름 바꾸기 **Class1.cs** 하 **Arithmetic.cs** 다음 코드와 일치 하도록 업데이트 합니다.  
  
     [!code-csharp[CreatingAnSDKUsingWinRT#3](../snippets/csharp/VS_Snippets_VSSDK/creatingansdkusingwinrt/cs/winrtmath/arithmetic.cs#3)]
     [!code-vb[CreatingAnSDKUsingWinRT#3](../snippets/visualbasic/VS_Snippets_VSSDK/creatingansdkusingwinrt/vb/winrtmath/arithmetic.vb#3)]  
  
6. **솔루션 탐색기**에 대 한 바로 가기 메뉴를 열고 합니다 **솔루션 'SimpleMath'** 노드를 선택한 후 **Configuration Manager**합니다.  
  
     합니다 **Configuration Manager** 대화 상자가 열립니다.  
  
7. 에 **활성 솔루션 구성** 목록에서 선택 **릴리스**합니다.  
  
8. 에 **구성** 열 되어 있는지 확인 **SimpleMath** 행으로 설정 됩니다 **릴리스**를 선택한 후는 **닫기** 단추를는 변경 내용입니다.  
  
    > [!IMPORTANT]
    > SimpleMath 구성 요소에 대 한 SDK에는 하나의 구성만 포함 됩니다. 이 구성은 릴리스 빌드의 경우 해야 합니다. 또는 구성 요소를 사용 하는 앱에 대 한 인증을 전달 하지는[!INCLUDE[win8_appstore_long](../includes/win8-appstore-long-md.md)]합니다.  
  
9. **솔루션 탐색기**에 대 한 바로 가기 메뉴를 열고 합니다 **SimpleMath** 프로젝트 노드를 선택한 후 **빌드**합니다.  
  
## <a name="createVSIX"></a> SimpleMathVSIX 확장 프로젝트를 만들려면  
  
1. 에 대 한 바로 가기 메뉴를 **솔루션 'SimpleMath'** 노드를 선택 **추가**에 **새 프로젝트**합니다.  
  
2. 템플릿 목록에서 확장 **Visual C#** 또는 **Visual Basic**를 선택 합니다 **확장성** 노드를 선택한 후 합니다 **VSIX 프로젝트** 템플릿입니다.  
  
3. 에 **이름** 상자에서 지정 **SimpleMathVSIX**를 선택한 후는 **확인** 단추입니다.  
  
4. **솔루션 탐색기**를 선택 합니다 **source.extension.vsixmanifest** 항목입니다.  
  
5. 메뉴 모음에서 **보기**, **코드**를 차례로 선택합니다.  
  
6. 다음 XML의 기존 XML로 바꿉니다.  
  
     [!code-xml[CreatingAnSDKUsingWinRT#1](../../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-csharp-or-visual-basic_2.xml)]
  
7. **솔루션 탐색기**를 선택 합니다 **SimpleMathVSIX** 프로젝트입니다.  
  
8. 메뉴 모음에서 선택 **프로젝트**하십시오 **새 항목 추가**합니다.  
  
9. 목록의 **공통 항목**를 확장 하 고 **데이터**를 선택한 후 **XML 파일**.  
  
10. 에 **이름** 상자에서 지정 `SDKManifest.xml`를 선택한 후는 **추가** 단추입니다.  
  
11. **솔루션 탐색기**에 대 한 바로 가기 메뉴를 열고 `SDKManifest.xml`, 선택 **속성**의 값을 변경한 후 합니다 **VSIX에 포함** 속성**True**합니다.  
  
12. 파일의 내용을 다음 XML로 바꿉니다.  
  
     [!code-xml[CreatingAnSDKUsingWinRT#1](../snippets/csharp/VS_Snippets_VSSDK/creatingansdkusingwinrt/cs/winrtmathvsix/sdkmanifest.xml#1)]
     [!code-xml[CreatingAnSDKUsingWinRT#1](../snippets/visualbasic/VS_Snippets_VSSDK/creatingansdkusingwinrt/vb/winrtmathvsix/sdkmanifest.xml#1)]  
  
13. **솔루션 탐색기**에 대 한 바로 가기 메뉴를 열고 합니다 **SimpleMathVSIX** 프로젝트를 선택 **추가**를 선택한 후 **새 폴더**합니다.  
  
14. 폴더 이름 바꾸기 `references`합니다.  
  
15. 바로 가기 메뉴를 열고 합니다 **참조** 폴더 선택 **추가**를 선택한 후 **새 폴더**합니다.  
  
16. 에 하위 폴더 이름 바꾸기 `commonconfiguration`, 하위 폴더를 만들고 하위 폴더의 이름을 `neutral`입니다.  
  
17. 첫 번째 폴더 이름 바꾸기이 이번 이전 네 단계를 반복 `redist`합니다.  
  
     이제 프로젝트에는 다음 폴더 구조가 포함 됩니다.  
  
    ```  
    references\commonconfiguration\neutral  
    redist\commonconfiguration\neutral  
    ```  
  
18. **솔루션 탐색기**에 대 한 바로 가기 메뉴를 열고 합니다 **SimpleMath** 프로젝트를 선택한 후 **파일 탐색기에서 폴더 열기**합니다.  
  
19. **파일 탐색기**bin\Release 폴더로 이동, SimpleMath.winmd 파일에 대 한 바로 가기 메뉴를 열고 선택한 **복사**합니다.  
  
20. **솔루션 탐색기**, references\commonconfiguration\neutral 폴더에 파일을 붙여 합니다 **SimpleMathVSIX** 프로젝트입니다.  
  
21. Redist\commonconfiguration\neutral 폴더 SimpleMath.pri 파일을 넣는 이전 단계를 반복 합니다 **SimpleMathVSIX** 프로젝트입니다.  
  
22. **솔루션 탐색기**, 선택 **SimpleMath.winmd**합니다.  
  
23. 메뉴 모음에서 선택 **뷰**하십시오 **속성** (키보드: F4 키 선택).  
  
24. 에 **속성** 창에서를 **빌드 작업** 속성을 **콘텐츠**, 변경한 후를 **VSIX에 포함** 속성 **True**합니다.  
  
25. **솔루션 탐색기**,이 프로세스를 반복 **SimpleMath.pri**합니다.  
  
26. **솔루션 탐색기**를 선택 합니다 **SimpleMathVSIX** 프로젝트입니다.  
  
27. 메뉴 모음에서 **빌드**하십시오 **SimpleMathVSIX 빌드**합니다.  
  
28. **솔루션 탐색기**에 대 한 바로 가기 메뉴를 열고 합니다 **SimpleMathVSIX** 프로젝트를 선택한 후 **파일 탐색기에서 폴더 열기**합니다.  
  
29. **파일 탐색기**\bin\Release 폴더를 탐색 하 고 다음 SimpleMathVSIX.vsix 설치를 실행 합니다.  
  
30. 선택 된 **설치** 단추, 설치가 완료 되기를 기다린 후 다음 Visual Studio를 다시 시작 합니다.  
  
## <a name="createSample"></a> 클래스 라이브러리를 사용 하는 샘플 앱을 만들려면  
  
1. 메뉴 모음에서 **파일**, **새로 만들기**하십시오 **새 프로젝트**.  
  
2. 템플릿 목록에서 확장 **Visual C#** 또는 **Visual Basic**를 선택한 후는 **Windows 스토어** 노드.  
  
3. 선택 합니다 **비어 있는 앱** 서식 파일을 프로젝트의 이름 **ArithmeticUI**를 선택한 후는 **확인** 단추입니다.  
  
4. **솔루션 탐색기**에 대 한 바로 가기 메뉴를 열고 합니다 **ArithmeticUI** 프로젝트를 선택한 후 **추가**를 **참조**합니다.  
  
5. 참조 형식의 목록에서 확장 **Windows**를 선택한 후 **확장**합니다.  
  
6. 세부 정보 창에서 선택 합니다 **간단한 수학 SDK** 확장 합니다.  
  
    SDK에 대 한 추가 정보가 표시 됩니다. 선택할 수 있습니다는 **자세한 정보** 열려면 링크 http://www.msdn.microsoft.com처럼이 연습의 앞부분에서 SDKManifest.xml 파일에 지정 합니다.  
  
7. **참조 관리자** 대화 상자를 선택 합니다 **간단한 수학 SDK** 확인란을 선택한 후는 **확인** 단추.  
  
8. 메뉴 모음에서 **뷰**하십시오 **개체 브라우저**합니다.  
  
9. 에 **찾아보기** 목록에서 선택 **간단한 수학**합니다.  
  
     이제 SDK의 새로운 기능을 탐색할 수 있습니다.  
  
10. **솔루션 탐색기**MainPage.xaml을 열고 다음 XAML로 해당 내용을 바꿉니다.  
  
     [!code-xml[CreatingAnSDKUsingWinRTDemoApp#1](../snippets/csharp/VS_Snippets_VSSDK/creatingansdkusingwinrtdemoapp/cs/winrtmathtest/mainpage.xaml#1)]
     [!code-xml[CreatingAnSDKUsingWinRTDemoApp#1](../snippets/visualbasic/VS_Snippets_VSSDK/creatingansdkusingwinrtdemoapp/vb/winrtmathtest/mainpage.xaml#1)]  
  
11. 다음 코드와 일치 하도록 MainPage.xaml.cs를 업데이트 합니다.  
  
     [!code-csharp[CreatingAnSDKUsingWinRTDemoApp#2](../snippets/csharp/VS_Snippets_VSSDK/creatingansdkusingwinrtdemoapp/cs/winrtmathtest/mainpage.xaml.cs#2)]
     [!code-vb[CreatingAnSDKUsingWinRTDemoApp#2](../snippets/visualbasic/VS_Snippets_VSSDK/creatingansdkusingwinrtdemoapp/vb/winrtmathtest/mainpage.xaml.vb#2)]  
  
12. 앱을 실행 하려면 F5 키를 선택 합니다.  
  
13. 앱에서 임의의 두 숫자로 입력 작업을 선택한 다음 선택 합니다 **=** 단추입니다.  
  
     올바른 결과 표시 합니다.  
  
    성공적으로 만들고 확장명 SDK를 사용 합니다.  
  
## <a name="see-also"></a>참고 항목  
 [연습: 사용 하 여 SDK 만들기C++](../extensibility/walkthrough-creating-an-sdk-using-cpp.md)   
 [연습: JavaScript를 사용 하 여 SDK 만들기](walkthrough-creating-an-sdk-using-javascript.md)   
 [소프트웨어 개발 키트 만들기](../extensibility/creating-a-software-development-kit.md)
