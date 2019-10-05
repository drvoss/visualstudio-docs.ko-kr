---
title: '연습: 사용 하 여 SDK 만들기 C++ | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: 36ea793b-3832-41a1-b906-69e680ad5e1d
caps.latest.revision: 33
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1312d61b2d287a5dd8cb757b73e818a9e9cb2241
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68202063"
---
# <a name="walkthrough-creating-an-sdk-using-c"></a>연습: C++를 사용하여 SDK 만들기
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

이 연습에는 네이티브를 만드는 방법을 보여 줍니다 C++ 수학 라이브러리 SDK, SDK로는 VSIX Visual Studio Extension (), 패키지 및를 사용 하 여 앱을 만듭니다. 이 연습에서는 이러한 단계로 구분 됩니다.  
  
- [네이티브 및 Windows 런타임 라이브러리를 만들려면](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createClassLibrary)  
  
- [NativeMathVSIX 확장 프로젝트를 만들려면](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createVSIX)  
  
- [클래스 라이브러리를 사용 하는 샘플 앱을 만들려면](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createSample)  
  
## <a name="prerequisites"></a>필수 구성 요소  
 이 연습을 수행하려면 Visual Studio SDK를 설치해야 합니다. 자세한 내용은 [Visual Studio SDK](../extensibility/visual-studio-sdk.md)합니다.  
  
## <a name="createClassLibrary"></a> 네이티브 및 Windows 런타임 라이브러리를 만들려면  
  
1. 메뉴 모음에서 **파일**, **새로 만들기**, **프로젝트**를 차례로 선택합니다.  
  
2. 템플릿 목록에서 확장 **Visual C++** , **Windows 스토어**를 선택한 후의 **DLL (Windows 스토어 앱)** 템플릿. 에 **이름** 상자에서 지정 `NativeMath`를 선택한 후는 **확인** 단추입니다.  
  
3. 다음 코드와 일치 하도록 NativeMath.h를 업데이트 합니다.  
  
     [!code-cpp[CreatingAnSDKUsingCpp#1](../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcpp/cpp/nativemath/nativemath.h#1)]  
  
4. 이 코드와 일치 하도록 업데이트 NativeMath.cpp:  
  
     [!code-cpp[CreatingAnSDKUsingCpp#2](../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcpp/cpp/nativemath/nativemath.cpp#2)]  
  
5. **솔루션 탐색기**에 대 한 바로 가기 메뉴를 열고 **솔루션 'NativeMath'** 를 선택한 후 **추가**를 **새 프로젝트**합니다.  
  
6. 템플릿 목록에서 확장 **Visual C++** 를 선택한 후 합니다 **Windows 런타임 구성 요소** 템플릿. 에 **이름** 상자에서 지정 `NativeMathWRT`를 선택한 후는 **확인** 단추입니다.  
  
7. 이 코드와 일치 하도록 업데이트 Class1.h:  
  
     [!code-cpp[CreatingAnSDKUsingCpp#3](../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcpp/cpp/nativemathwrt/class1.h#3)]  
  
8. 이 코드와 일치 하도록 업데이트 Class1.cpp:  
  
     [!code-cpp[CreatingAnSDKUsingCpp#4](../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcpp/cpp/nativemathwrt/class1.cpp#4)]  
  
9. 메뉴 모음에서 **빌드**, **솔루션 빌드**를 선택합니다.  
  
## <a name="createVSIX"></a> NativeMathVSIX 확장 프로젝트를 만들려면  
  
1. **솔루션 탐색기**에 대 한 바로 가기 메뉴를 열고 **솔루션 'NativeMath'** 를 선택한 후 **추가**를 **새 프로젝트**합니다.  
  
2. 템플릿 목록에서 확장 **Visual C#** 를 **확장성**를 선택한 후 **VSIX 패키지**합니다. 에 **이름** 상자에서 지정 **NativeMathVSIX**를 선택한 후는 **확인** 단추입니다.  
  
3. VSIX 매니페스트 디자이너에 표시 되 면 닫습니다.  
  
4. **솔루션 탐색기**에 대 한 바로 가기 메뉴를 열고 **source.extension.vsixmanifest**를 선택한 후 **코드 보기**합니다.  
  
5. 기존 XML를 바꾸려면 다음 XML을 사용 합니다.  
  
    [!code-xml[CreatingAnSDKUsingCpp#6](../../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-cpp_6.xml)]
  
6. **솔루션 탐색기**에 대 한 바로 가기 메뉴를 열고 합니다 **NativeMathVSIX** 프로젝트를 선택한 후 **추가**를 **새 항목**합니다.  
  
7. 목록에서 **Visual C# 항목**를 확장 하 고 **데이터**를 선택한 후 **XML 파일**합니다. 에 **이름** 상자에서 지정 `SDKManifest.xml`를 선택한 후는 **확인** 단추입니다.  
  
8. 이 XML을 사용 하 여 파일의 내용을 바꿉니다.  
  
     [!code-xml[CreatingAnSDKUsingCpp#5](../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcpp/cpp/nativemathvsix/sdkmanifest.xml#5)]  
  
9. **솔루션 탐색기**를 **NativeMathVSIX** 프로젝트에서이 폴더 구조를 만듭니다.  
  
    ```  
  
    \DesignTime  
          \CommonConfiguration  
                \Neutral  
                      \Include  
          \Debug  
                \x86  
    \Redist  
          \Debug  
                \x86  
    \References  
          \CommonConfiguration  
                \Neutral  
    ```  
  
10. **솔루션 탐색기**에 대 한 바로 가기 메뉴를 열고 **솔루션 'NativeMath'** 를 선택한 후 **파일 탐색기에서 폴더 열기**합니다.  
  
11. **파일 탐색기**, \NativeMath\NativeMath.h, 복사 및 다음 **솔루션 탐색기**를 **NativeMathVSIX** 프로젝트는 \DesignTime\에 붙여 넣습니다 CommonConfiguration\Neutral\Include\ 폴더입니다.  
  
     \Debug\NativeMath\NativeMath.lib을 복사한 다음 \DesignTime\Debug\x86\ 폴더에 붙여 넣습니다.  
  
     \Debug\NativeMath\NativeMath.dll 복사한 \Redist\Debug\x86\ 폴더에 붙여 넣습니다.  
  
     DebugNativeMathWRTNativeMathWRT.dll 복사한 RedistDebugx86 폴더에 붙여 넣습니다.  
  
     DebugNativeMathWRTNativeMathWRT.winmd 복사한 ReferencesCommonConfigurationNeutral 폴더에 붙여 넣습니다.  
  
     DebugNativeMathWRTNativeMathWRT.pri 복사한 ReferencesCommonConfigurationNeutral 폴더에 붙여 넣습니다.  
  
12. \DesignTime\Debug\x86\ 폴더에서 NativeMathSDK.props, 라는 텍스트 파일을 만들고 다음 내용을 붙여넣습니다.  
  
    [!code-xml[CreatingAnSDKUsingCpp#7](../../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-cpp_7.xml)]  
  
13. 메뉴 모음에서 **보기**, **다른 Windows**하십시오 **속성 창** (키보드: F4 키 선택).  
  
14. **솔루션 탐색기**를 선택 합니다 **NativeMathWRT.winmd** 파일입니다. 에 **속성** 창에서를 **빌드 작업** 속성을 **콘텐츠**, 변경한 후를 **VSIX에 포함** 속성 **True**합니다.  
  
     이 프로세스를 반복 합니다 **SimpleMath.pri** 파일입니다.  
  
     이 프로세스를 반복 합니다 **NativeMath.Lib** 파일입니다.  
  
     이 프로세스를 반복 합니다 **NativeMathSDK.props** 파일입니다.  
  
15. **솔루션 탐색기**를 선택 합니다 **NativeMath.h** 파일입니다. 에 **속성** 창에서 변경 합니다 **VSIX에 포함** 속성을 **True**합니다.  
  
     이 프로세스를 반복 합니다 **NativeMath.dll** 파일입니다.  
  
     이 프로세스를 반복 합니다 **NativeMathWRT.dll** 파일입니다.  
  
     이 프로세스를 반복 합니다 **SDKManifest.xml** 파일입니다.  
  
16. 메뉴 모음에서 **빌드**, **솔루션 빌드**를 선택합니다.  
  
17. **솔루션 탐색기**에 대 한 바로 가기 메뉴를 열고 합니다 **NativeMathVSIX** 프로젝트를 선택한 후 **파일 탐색기에서 폴더 열기**합니다.  
  
18. **파일 탐색기**\bin\Debug\ 폴더를 탐색 하 고 다음 설치를 시작 하는 NativeMathVSIX.vsix를 실행 합니다.  
  
19. 선택 된 **설치** 단추, 설치가 완료 되기를 기다린 후 다음 Visual Studio를 다시 시작 합니다.  
  
## <a name="createSample"></a> 클래스 라이브러리를 사용 하는 샘플 앱을 만들려면  
  
1. 메뉴 모음에서 **파일**, **새로 만들기**, **프로젝트**를 차례로 선택합니다.  
  
2. 템플릿 목록에서 확장 **Visual C++** 를 **Windows Store**를 선택한 후 **비어 있는 앱**. 에 **이름** 상자에서 지정 **NativeMathSDKSample**를 선택한 후는 **확인** 단추입니다.  
  
3. **솔루션 탐색기**에 대 한 바로 가기 메뉴를 열고 합니다 **NativeMathSDKSample** 프로젝트를 선택한 후 **추가**를 **참조**합니다.  
  
4. 에 **공용 속성**를 **프레임 워크 및 참조** 속성 페이지 참조 형식 목록에서 확장 **Windows**를 선택한 후 **확장** . 세부 정보 창에서 선택 합니다 **네이티브 수학 SDK** 확장을 선택한 후는 **새 참조 추가** 단추입니다.  
  
5. **참조 추가** 대화 상자를 선택 합니다 **네이티브 수학 SDK** 확인란을 선택한 후는 **확인** 단추.  
  
6. NativeMathSDKSample에 대 한 프로젝트 속성을 표시 합니다.  
  
    NativeMathSDK.props에 정의 된 속성 참조를 추가한 경우에 적용 되었습니다. 검사 하 여이 확인할 수 있습니다 합니다 **VC + + 디렉터리** 프로젝트의 속성 **구성 속성**합니다.  
  
7. **솔루션 탐색기**MainPage.xaml을 열고 다음 XAML을 사용 하 여 해당 콘텐츠를 대체 합니다.  
  
    [!code-xml[CreatingAnSDKUsingCppDemoApp#1](../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcppdemoapp/cpp/mainpage.xaml#1)]  
  
8. Mainpage.xaml.h이이 코드와 일치 하도록 업데이트 합니다.  
  
    [!code-cpp[CreatingAnSDKUsingCppDemoApp#2](../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcppdemoapp/cpp/mainpage.xaml.h#2)]  
  
9. MainPage.xaml.cpp이이 코드와 일치 하도록 업데이트 합니다.  
  
     [!code-cpp[CreatingAnSDKUsingCppDemoApp#3](../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcppdemoapp/cpp/mainpage.xaml.cpp#3)]  
  
10. 앱을 실행 하려면 F5 키를 선택 합니다.  
  
11. 앱에서 임의의 두 숫자로 입력 작업을 선택한 다음 선택 합니다 **=** 단추입니다.  
  
     올바른 결과 표시 합니다.  
  
    이 연습에서는 만들고를 호출 하는 확장 SDK를 사용 하는 방법을 보여 주었습니다.는 [!INCLUDE[wrt](../includes/wrt-md.md)] 라이브러리 및 비-[!INCLUDE[wrt](../includes/wrt-md.md)] 라이브러리입니다.  
  
## <a name="next-steps"></a>다음 단계  
  
## <a name="see-also"></a>참고 항목  
 [연습: 사용 하 여 SDK 만들기 C# 또는 Visual Basic](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md)   
 [소프트웨어 개발 키트 만들기](../extensibility/creating-a-software-development-kit.md)
