---
title: '연습: 사용 하 여 SDK 만들기 C++ | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 36ea793b-3832-41a1-b906-69e680ad5e1d
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a60194c6512b67e1e3e90389b0221b6cdb8a5226
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66312694"
---
# <a name="walkthrough-create-an-sdk-using-c"></a>연습: 사용 하 여 SDK 만들기C++
이 연습에는 네이티브를 만드는 방법을 보여 줍니다 C++ 수학 라이브러리 SDK, SDK로는 VSIX Visual Studio Extension (), 패키지 및를 사용 하 여 앱을 만듭니다. 이 연습에서는 이러한 단계로 구분 됩니다.

- [네이티브 및 Windows 런타임 라이브러리를 만들려면](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createClassLibrary)

- [NativeMathVSIX 확장 프로젝트를 만들려면](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createVSIX)

- [클래스 라이브러리를 사용 하는 샘플 앱을 만들려면](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createSample)

## <a name="prerequisites"></a>전제 조건
 이 연습을 수행하려면 Visual Studio SDK를 설치해야 합니다. 자세한 내용은 [Visual Studio SDK](../extensibility/visual-studio-sdk.md)합니다.

## <a name="createClassLibrary"></a> 네이티브 및 Windows 런타임 라이브러리를 만들려면

1. 메뉴 모음에서 **파일** > **새로 만들기** > **프로젝트**를 선택합니다.

2. 템플릿 목록에서 확장 **Visual C++**   >  **Windows 유니버설**를 선택한 후의 **DLL (유니버설 Windows 앱)** 템플릿. 에 **이름** 상자에서 지정 `NativeMath`를 선택한 후는 **확인** 단추입니다.

3. 업데이트 *NativeMath.h* 다음 코드와 일치 하도록 합니다.

     [!code-cpp[CreatingAnSDKUsingCpp#1](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_1.h)]

4. 업데이트 *NativeMath.cpp* 이 코드와 일치 하도록 합니다.

     [!code-cpp[CreatingAnSDKUsingCpp#2](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_2.cpp)]

5. **솔루션 탐색기**에 대 한 바로 가기 메뉴를 열고 **솔루션 'NativeMath'** 를 선택한 후 **추가** > **새 프로젝트**.

6. 템플릿 목록에서 확장 **Visual C++** 를 선택한 후 합니다 **Windows 런타임 구성 요소** 템플릿. 에 **이름** 상자에서 지정 `NativeMathWRT`를 선택한 후는 **확인** 단추입니다.

7. 업데이트 *Class1.h* 이 코드와 일치 하도록 합니다.

     [!code-cpp[CreatingAnSDKUsingCpp#3](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_3.h)]

8. 업데이트 *Class1.cpp* 이 코드와 일치 하도록 합니다.

     [!code-cpp[CreatingAnSDKUsingCpp#4](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_4.cpp)]

9. 메뉴 모음에서 **빌드** > **솔루션 빌드**를 선택합니다.

## <a name="createVSIX"></a> NativeMathVSIX 확장 프로젝트를 만들려면

1. **솔루션 탐색기**에 대 한 바로 가기 메뉴를 열고 **솔루션 'NativeMath'** 를 선택한 후 **추가** > **새 프로젝트**.

2. 템플릿 목록에서 확장 **Visual C#**  > **확장성**를 선택한 후 **VSIX 프로젝트**합니다. 에 **이름** 상자에서 지정 **NativeMathVSIX**를 선택한 후는 **확인** 단추입니다.

3. **솔루션 탐색기**에 대 한 바로 가기 메뉴를 열고 **source.extension.vsixmanifest**를 선택한 후 **코드 보기**합니다.

4. 기존 XML를 바꾸려면 다음 XML을 사용 합니다.

    [!code-xml[CreatingAnSDKUsingCpp#6](../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-cpp_6.xml)]

5. **솔루션 탐색기**에 대 한 바로 가기 메뉴를 열고 합니다 **NativeMathVSIX** 프로젝트를 선택한 후 **추가** > **새 항목**.

6. 목록에서 **Visual C# 항목**를 확장 하 고 **데이터**를 선택한 후 **XML 파일**합니다. 에 **이름** 상자에서 지정 `SDKManifest.xml`를 선택한 후는 **확인** 단추입니다.

7. 이 XML을 사용 하 여 파일의 내용을 바꿉니다.

     [!code-xml[CreatingAnSDKUsingCpp#5](../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-cpp_5.xml)]

8. **솔루션 탐색기**아래에 있는 합니다 **NativeMathVSIX** 프로젝트에서이 폴더 구조를 만듭니다.

    ```xml
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

9. **솔루션 탐색기**에 대 한 바로 가기 메뉴를 열고 **솔루션 'NativeMath'** 를 선택한 후 **파일 탐색기에서 폴더 열기**합니다.

10. **파일 탐색기**를 복사 *$SolutionRoot$\NativeMath\NativeMath.h*를 선택한 다음 **솔루션 탐색기**아래에 있는 **NativeMathVSIX**프로젝트를 붙여 넣습니다 합니다 *$SolutionRoot$ \NativeMathVSIX\DesignTime\CommonConfiguration\Neutral\Include\\*  폴더입니다.

     복사본 *$SolutionRoot$\Debug\NativeMath\NativeMath.lib*를 붙여 넣습니다 합니다 *$SolutionRoot$ \NativeMathVSIX\DesignTime\Debug\x86\\*  폴더입니다.

     복사본 *$SolutionRoot$\Debug\NativeMath\NativeMath.dll* 에 붙여 넣습니다 합니다 *$SolutionRoot$ \NativeMathVSIX\Redist\Debug\x86\\*  폴더입니다.

     복사본 *$SolutionRoot$\Debug\NativeMathWRT\NativeMathWRT.dll* 에 붙여 넣습니다 합니다 *$SolutionRoot$ \NativeMathVSIX\Redist\Debug\x86* 폴더입니다.
     복사본 *$SolutionRoot$\Debug\NativeMathWRT\NativeMathWRT.winmd* 에 붙여 넣습니다 합니다 *$SolutionRoot$ \NativeMathVSIX\References\CommonConfiguration\Neutral* 폴더입니다.

     복사본 *$SolutionRoot$\Debug\NativeMathWRT\NativeMathWRT.pri* 에 붙여 넣습니다 합니다 *$SolutionRoot$ \NativeMathVSIX\References\CommonConfiguration\Neutral* 폴더입니다.

11. 에 *$SolutionRoot$ \NativeMathVSIX\DesignTime\Debug\x86\\*  폴더를 라는 텍스트 파일을 만듭니다 *NativeMathSDK.props*, 그 안에 다음 콘텐츠를 붙여:

    [!code-xml[CreatingAnSDKUsingCpp#7](../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-cpp_7.xml)]

12. 메뉴 모음에서 선택 **뷰** > **기타 Windows** > **속성 창** (키보드: 선택 된 **F4** 키).

13. **솔루션 탐색기**를 선택 합니다 **NativeMathWRT.winmd** 파일입니다. 에 **속성** 창에서를 **빌드 작업** 속성을 **콘텐츠**, 변경한 후를 **VSIX에 포함** 속성 **True**합니다.

     이 프로세스를 반복 합니다 **NativeMath.h** 파일입니다.

     이 프로세스를 반복 합니다 **NativeMathWRT.pri** 파일입니다.

     이 프로세스를 반복 합니다 **NativeMath.Lib** 파일입니다.

     이 프로세스를 반복 합니다 **NativeMathSDK.props** 파일입니다.

14. **솔루션 탐색기**를 선택 합니다 **NativeMath.h** 파일입니다. 에 **속성** 창에서 변경 합니다 **VSIX에 포함** 속성을 **True**합니다.

     이 프로세스를 반복 합니다 **NativeMath.dll** 파일입니다.

     이 프로세스를 반복 합니다 **NativeMathWRT.dll** 파일입니다.

     이 프로세스를 반복 합니다 **SDKManifest.xml** 파일입니다.

15. 메뉴 모음에서 **빌드** > **솔루션 빌드**를 선택합니다.

16. **솔루션 탐색기**에 대 한 바로 가기 메뉴를 열고 합니다 **NativeMathVSIX** 프로젝트를 선택한 후 **파일 탐색기에서 폴더 열기**합니다.

17. **파일 탐색기**로 이동 합니다 *$SolutionRoot$ \NativeMathVSIX\bin\Debug* 폴더 및 다음 실행 *NativeMathVSIX.vsix* 설치를 시작 하 합니다.

18. 선택 된 **설치** 단추, 설치 완료를 위해 기다린 후 다음 Visual Studio를 엽니다.

## <a name="createSample"></a> 클래스 라이브러리를 사용 하는 샘플 앱을 만들려면

1. 메뉴 모음에서 **파일** > **새로 만들기** > **프로젝트**를 선택합니다.

2. 템플릿 목록에서 확장 **시각적 C++**   >  **Windows 유니버설** 선택한 후 **비어 있는 앱**. 에 **이름** 상자에서 지정 **NativeMathSDKSample**를 선택한 후는 **확인** 단추입니다.

3. **솔루션 탐색기**에 대 한 바로 가기 메뉴를 열고 합니다 **NativeMathSDKSample** 프로젝트를 선택한 후 **추가** > **참조**.

4. 에 **참조 추가** 대화 상자에서 참조 형식의 목록 **유니버설 Windows**를 선택한 후 **확장**합니다. 마지막으로 선택 합니다 **네이티브 수학 SDK** 확인란을 선택한 후 합니다 **확인** 단추입니다.

5. NativeMathSDKSample에 대 한 프로젝트 속성을 표시 합니다.

    에 정의 된 속성 *NativeMathSDK.props* 참조를 추가 했을 때 적용 됩니다. 속성을 검사 하 여 적용 된 것을 확인할 수 있습니다 합니다 **VC + + 디렉터리** 프로젝트의 속성 **구성 속성**합니다.

6. **솔루션 탐색기**오픈 **MainPage.xaml**, 다음 다음 XAML을 사용 하 여 해당 콘텐츠를 바꾸려면:

    [!code-xml[CreatingAnSDKUsingCppDemoApp#1](../extensibility/codesnippet/Xaml/walkthrough-creating-an-sdk-using-cpp_8.xaml)]

7. 업데이트 *Mainpage.xaml.h* 이 코드와 일치 하도록 합니다.

    [!code-cpp[CreatingAnSDKUsingCppDemoApp#2](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_9.h)]

8. 업데이트 *MainPage.xaml.cpp* 이 코드와 일치 하도록 합니다.

     [!code-cpp[CreatingAnSDKUsingCppDemoApp#3](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_10.cpp)]

9. 선택 된 **F5** 키를 눌러 앱을 실행 합니다.

10. 앱에서 임의의 두 숫자로 입력 작업을 선택한 다음 선택 합니다 **=** 단추입니다.

     올바른 결과 표시 합니다.

    이 연습에서는 만들고를 호출 하는 확장 SDK를 사용 하는 방법을 보여 주었습니다.는 [!INCLUDE[wrt](../extensibility/includes/wrt_md.md)] 라이브러리 및 비-[!INCLUDE[wrt](../extensibility/includes/wrt_md.md)] 라이브러리입니다.

## <a name="next-steps"></a>다음 단계

## <a name="see-also"></a>참고자료
- [연습: 사용 하 여 SDK 만들기 C# 또는 Visual Basic](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md)
- [소프트웨어 개발 키트 만들기](../extensibility/creating-a-software-development-kit.md)
