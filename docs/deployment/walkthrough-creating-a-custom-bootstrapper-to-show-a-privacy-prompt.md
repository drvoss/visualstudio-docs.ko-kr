---
title: '연습: 개인정보 처리 방침 프롬프트를 사용 하 여 사용자 지정 부트스트래퍼 만들기 | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, prerequisites
- dependencies [.NET Framework], custom bootstrapper package
- deploying applications [Visual Studio], custom prerequisites
- Windows Installer deployment, prerequisites
- prerequisites [.NET Framework], custom bootstrapper package
ms.assetid: 2f3edd6a-84d1-4864-a1ae-6a13c5732aae
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 00c5266d57ae5633313465796c718d989f783ea6
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63406856"
---
# <a name="walkthrough-create-a-custom-bootstrapper-with-a-privacy-prompt"></a>연습: 개인정보처리방침 프롬프트가 포함된 사용자 지정 부트스트래퍼 만들기
최신 파일 버전 및 어셈블리 버전을 사용 하 여 어셈블리를 사용할 수 있게 되 면 자동으로 업데이트 하도록 ClickOnce 응용 프로그램을 구성할 수 있습니다. 되도록 고객에 게이 동작에 동의 하는, 개인정보 처리 방침 프롬프트를 표시할 수 있습니다. 그런 다음 응용 프로그램이 자동으로 업데이트 하는 권한을 부여할 것인지를 선택할 수 있습니다. 응용 프로그램에 자동으로 업데이트 하도록 허용 되지 않습니다 설치 하지 않습니다.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="prerequisites"></a>전제 조건
 이 연습을 완료하려면 다음 구성 요소가 필요합니다.

- Visual Studio 2010

## <a name="create-an-update-consent-dialog-box"></a>업데이트 승인 대화 상자를 만들려면
 개인정보 처리 방침 프롬프트를 표시 하려면 응용 프로그램에 대 한 자동 업데이트에 동의 하는지 묻는 하는 응용 프로그램을 만듭니다.

#### <a name="to-create-a-consent-dialog-box"></a>동의 대화 상자를 만들려면

1. **파일** 메뉴에서 **새로 만들기**를 가리킨 다음 **프로젝트**를 클릭합니다.

2. 에 **새 프로젝트** 대화 상자, 클릭 **Windows**를 클릭 하 고 **WindowsFormsApplication**합니다.

3. 에 대 한 합니다 **이름**, 형식 **ConsentDialog**를 클릭 하 고 **확인**합니다.

4. 디자이너에서 폼을 클릭 합니다.

5. 에 **속성** 창에서 변경 합니다 **텍스트** 속성을 **업데이트 승인 대화 상자**합니다.

6. 에 **도구 상자**, 확장 **모든 Windows Forms**를 끌어서를 **레이블** 컨트롤을 폼입니다.

7. 디자이너에서 레이블 컨트롤을 클릭 합니다.

8. 에 **속성** 창에서 변경 합니다 **텍스트** 속성 **모양을** 다음과:

    응용 프로그램을 설치 하려고 합니다. 웹에서 최신 업데이트를 확인 합니다. "동의 안 함"을 클릭 하 여 응용 프로그램을 확인 하 고 인터넷에서 업데이트를 자동으로 설치 권한을 부여 합니다.

9. 에 **도구 상자**, 끌어를 **확인란을** 중간 폼에 컨트롤입니다.

10. 에 **속성** 창에서를 **텍스트** 아래의 속성 **레이아웃** 를 **동의**합니다.

11. 에 **도구 상자**를 끌어를 **단추** 컨트롤을 폼의 왼쪽 아래.

12. 에 **속성** 창에서를 **텍스트** 아래의 속성 **레이아웃** 를 **계속**합니다.

13. 에 **속성** 창에서를 **(이름)** 아래의 속성 **디자인** 를 **ProceedButton**합니다.

14. 에 **도구 상자**를 끌어를 **단추** 컨트롤을 폼의 오른쪽 아래.

15. 에 **속성** 창에서를 **텍스트** 아래의 속성 **레이아웃** 를 **취소**합니다.

16. 에 **속성** 창에서를 **(이름)** 아래의 속성 **디자인** 를 **CancelButton**합니다.

17. 디자이너에서 두 번 클릭 합니다 **동의 함** CheckedChanged 이벤트 처리기를 생성 하려면 확인란을 선택 합니다.

18. Form1 코드 파일에서 CheckedChanged 이벤트 처리기에 다음 코드를 추가 합니다.

     [!code-csharp[ConsentDialog#1](../deployment/codesnippet/CSharp/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_1.cs)]
     [!code-vb[ConsentDialog#1](../deployment/codesnippet/VisualBasic/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_1.vb)]

19. 사용 하지 않으려면 클래스 생성자를 업데이트 합니다 **계속** 기본 단추입니다.

     [!code-csharp[ConsentDialog#6](../deployment/codesnippet/CSharp/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_2.cs)]
     [!code-vb[ConsentDialog#6](../deployment/codesnippet/VisualBasic/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_2.vb)]

20. Form1 코드 파일에서 최종 사용자가 온라인 업데이트에 동의 하는 경우에 관리 하는 부울 변수는 다음 코드를 추가 합니다.

     [!code-csharp[ConsentDialog#3](../deployment/codesnippet/CSharp/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_3.cs)]
     [!code-vb[ConsentDialog#3](../deployment/codesnippet/VisualBasic/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_3.vb)]

21. 디자이너에서 두 번 클릭 합니다 **계속** 단추 클릭 이벤트 처리기를 생성 합니다.

22. Form1 코드 파일에 대 한 클릭 이벤트 처리기에 다음 코드를 추가 합니다 **계속** 단추입니다.

     [!code-csharp[ConsentDialog#2](../deployment/codesnippet/CSharp/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_4.cs)]
     [!code-vb[ConsentDialog#2](../deployment/codesnippet/VisualBasic/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_4.vb)]

23. 디자이너에서 두 번 클릭 합니다 **취소** 단추 클릭 이벤트 처리기를 생성 합니다.

24. Form1 코드 파일에 대 한 Click 이벤트 처리기에 다음 코드를 추가 합니다 **취소** 단추입니다.

     [!code-csharp[ConsentDialog#4](../deployment/codesnippet/CSharp/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_5.cs)]
     [!code-vb[ConsentDialog#4](../deployment/codesnippet/VisualBasic/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_5.vb)]

25. 최종 사용자는 온라인 업데이트에 동의 하지 않을 경우 오류를 반환 하도록 응용 프로그램을 업데이트 합니다.

     Visual Basic 개발자에 해당:

    1. **솔루션 탐색기**, 클릭 **ConsentDialog**합니다.

    2. 에 **프로젝트** 메뉴에서 클릭 **모듈 추가**를 클릭 하 고 **추가**합니다.

    3. 에 *Module1.vb* 코드 파일에서 다음 코드를 추가 합니다.

        [!code-vb[ConsentDialog#7](../deployment/codesnippet/VisualBasic/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_6.vb)]

    4. 에 **프로젝트** 메뉴에서 클릭 **ConsentDialog 속성**를 클릭 하 고는 **응용 프로그램** 탭 합니다.

    5. 선택 취소 **응용 프로그램 프레임 워크 사용**합니다.

    6. 에 **시작 개체** 드롭 다운 메뉴에서 **Module1**합니다.

       > [!NOTE]
       > Windows XP 비주얼 스타일, 응용 프로그램 이벤트, 시작 화면, 단일 인스턴스 응용 프로그램 등과 같은 기능을 비활성화 응용 프로그램 프레임 워크를 사용 하지 않도록 설정 합니다. 자세한 내용은 [Application Page, Project Designer (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md)을 참조하세요.

       Visual C# 개발자에 해당:

       엽니다는 *Program.cs* 코드, 파일을 열고 다음 코드를 추가 합니다.

       [!code-csharp[ConsentDialog#5](../deployment/codesnippet/CSharp/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_7.cs)]

26. 에 **빌드** 메뉴에서 클릭 **BuildSolution**합니다.

## <a name="create-the-custom-bootstrapper-package"></a>사용자 지정 부트스트래퍼 패키지 만들기
 업데이트 승인 대화 상자 응용 프로그램에 대 한 사용자 지정 부트스트래퍼 패키지 만들기를 ClickOnce 응용 프로그램의 모든 필수 구성 요소로 포함 최종 사용자에 게 개인정보 처리 방침 프롬프트를 표시 합니다.

 이 절차에는 다음 문서를 만들어 사용자 지정 부트스트래퍼 패키지를 만드는 방법을 보여 줍니다.

- A *product.xml* 매니페스트 파일을 부트스트래퍼의 내용을 설명 합니다.

- A *package.xml* 매니페스트 파일에서 지역화 관련 부분 문자열 등 소프트웨어 사용 조건에 따라 패키지를 나열 합니다.

- 소프트웨어 사용 조건에 대 한 문서입니다.

#### <a name="step-1-to-create-the-bootstrapper-directory"></a>1단계: 부트스트래퍼 디렉터리를 만들려면

1. 라는 디렉터리를 만듭니다 **UpdateConsentDialog** 에 *%PROGRAMFILES%\Microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages*합니다.

    > [!NOTE]
    > 이 폴더를 만들려면 관리자 권한 해야 할 수 있습니다.

2. 에 *UpdateConsentDialog* 디렉터리를 라는 하위 디렉터리를 만듭니다 *en*합니다.

    > [!NOTE]
    > 각 로캘에 대 한 새 디렉터리를 만듭니다. 예를 들어 fr 및 독일 로캘에 대 한 하위 디렉터리를 추가할 수 있습니다. 필요한 경우 이러한 디렉터리는 프랑스어 및 독일어 문자열 및 언어 팩에 포함 됩니다.

#### <a name="step-2-to-create-the-productxml-manifest-file"></a>2단계: Product.xml 매니페스트 파일을 만들려면

1. 라는 텍스트 파일을 만듭니다 *product.xml*합니다.

2. 에 *product.xml* 파일에서 다음 XML 코드를 추가 합니다. 기존 XML 코드를 덮어쓰지 않도록 해야 합니다.

    ```xml
    <Product
      xmlns="http://schemas.microsoft.com/developer/2004/01/bootstrapper"
      ProductCode="Microsoft.Sample.EULA">
      <!-- Defines the list of files to be copied on build. -->
      <PackageFiles CopyAllPackageFiles="false">
        <PackageFile Name="ConsentDialog.exe"/>
      </PackageFiles>

      <!-- Defines how to run the Setup package.-->
      <Commands >
        <Command PackageFile = "ConsentDialog.exe" Arguments=''>
          <ExitCodes>
            <ExitCode Value="0" Result="Success" />
            <ExitCode Value="-1" Result="Fail" String="AU_Unaccepted" />
            <DefaultExitCode Result="Fail"
              FormatMessageFromSystem="true" String="GeneralFailure" />
          </ExitCodes>
        </Command>
      </Commands>

    </Product>
    ```

3. UpdateConsentDialog 부트스트래퍼 디렉터리에 파일을 저장 합니다.

#### <a name="step-3-to-create-the-packagexml-manifest-file-and-the-software-license-terms"></a>3단계: 매니페스트 package.xml 파일을 만들고 소프트웨어 사용 조건

1. 라는 텍스트 파일을 만듭니다 *package.xml*합니다.

2. 에 *package.xml* 파일 로케일을 정의 하 고 소프트웨어 사용 조건에 포함 하려면 다음 XML 코드를 추가 합니다. 기존 XML 코드를 덮어쓰지 않도록 해야 합니다.

    ```xml
    <Package
      xmlns="http://schemas.microsoft.com/developer/2004/01/bootstrapper"
      Name="DisplayName"
      Culture="Culture"
      LicenseAgreement="eula.rtf">
      <PackageFiles>
        <PackageFile Name="eula.rtf"/>
      </PackageFiles>

      <!-- Defines a localizable string table for error messages. -->
      <Strings>
        <String Name="DisplayName">Update Consent Dialog</String>
        <String Name="Culture">en</String>
        <String Name="AU_Unaccepted">The automatic update agreement is not accepted.</String>
        <String Name="GeneralFailure">A failure occurred attempting to launch the setup.</String>
      </Strings>
    </Package>
    ```

3. UpdateConsentDialog 부트스트래퍼 디렉터리에 en 하위 디렉터리에 파일을 저장 합니다.

4. 이라는 문서를 만듭니다 *eula.rtf* 소프트웨어 사용 조건에 대 한 합니다.

    > [!NOTE]
    > 소프트웨어 사용 조건에는 라이선스, 보증, 부채 및 현지 법률에 대 한 정보를 포함 해야 합니다. 이러한 파일 로캘에, MBCS 또는 유니코드 문자를 지 원하는 형식으로 파일 저장 되는 있는지 확인 해야 합니다. 소프트웨어 사용 조건의 콘텐츠에 대 한 법률 부서를 참조 하세요.

5. 문서에서 en 하위 디렉터리를 저장 합니다 *UpdateConsentDialog* 부트스트래퍼 디렉터리입니다.

6. 필요한 경우 새로 만듭니다 *package.xml* 매니페스트 파일 및 새 *eula.rtf* 각 로캘에 대 한 소프트웨어 사용 조건에 대 한 문서. 예를 들어 fr 및 독일 로캘에 대 한 하위 디렉터리를 만든 경우 package.xml 별도 매니페스트 파일을 만들고 소프트웨어 사용 조건 및 de 및 fr 하위 디렉터리에 저장 합니다.

## <a name="set-the-update-consent-application-as-a-prerequisite"></a>필수 구성 요소로 응용 프로그램을 동의 업데이트 설정
 Visual Studio에서 필수 구성 요소로 업데이트 동의 응용 프로그램을 설정할 수 있습니다.

#### <a name="to-set-the-update-consent-application-as-a-prerequisite"></a>필수 구성 요소로 응용 프로그램을 동의 업데이트를 설정 하려면

1. **솔루션 탐색기**를 배포 하려는 응용 프로그램의 이름을 클릭 합니다.

2. **프로젝트** 메뉴에서 *ProjectName* **속성**을 클릭합니다.

3. 클릭 합니다 **게시** 페이지를 선택한 다음 클릭 **필수 구성 요소**합니다.

4. 선택 **업데이트 승인 대화 상자**합니다.

    > [!NOTE]
    > 업데이트 승인 대화 상자가 필수 조건 대화 상자를 보려면 Visual Studio를 닫고 다시 여 해야 합니다.

5. **확인**을 클릭합니다.

## <a name="create-and-test-the-setup-program"></a>만들기 및 설치 프로그램을 테스트 합니다.
 필수 구성 요소로 업데이트 동의 응용 프로그램을 설정한 후 응용 프로그램에 대 한 설치 관리자 및 부트스트래퍼를 생성할 수 있습니다.

#### <a name="to-create-and-test-the-setup-program-by-not-clicking-i-agree"></a>동의 만들고 클릭 하지 않는 경우 설치 프로그램을 테스트 하려면

1. **솔루션 탐색기**를 배포 하려는 응용 프로그램의 이름을 클릭 합니다.

2. **프로젝트** 메뉴에서 *ProjectName* **속성**을 클릭합니다.

3. 클릭 합니다 **게시** 페이지를 선택한 다음 클릭 **지금 게시**합니다.

4. 게시 출력을 자동으로 열리지 않는 경우 게시 출력으로 이동 합니다.

5. 실행 합니다 *Setup.exe* 프로그램입니다.

     설치 프로그램 업데이트 승인 대화 상자 소프트웨어 사용권 계약을 보여 줍니다.

6. 소프트웨어 사용권 계약을 읽고 클릭 **Accept**합니다.

     업데이트 승인 대화 상자 응용 프로그램 표시 하 고 다음 텍스트를 보여 줍니다. 응용 프로그램을 설치 하려고 합니다. 웹에서 최신 업데이트를 확인 합니다. 동의 클릭 하 여 인터넷에 자동 업데이트를 확인 하려면 응용 프로그램을 인증 합니다.

7. 응용 프로그램을 닫거나 취소 클릭 합니다.

     응용 프로그램 오류를 표시 합니다. 에 대 한 시스템 구성 요소를 설치 하는 동안 오류가 발생 했습니다 *ApplicationName*합니다. 모든 시스템 구성 요소가 성공적으로 설치 될 때까지 계속할 수 없습니다.

8. 세부 정보에서 다음 오류 메시지가 표시를 클릭 합니다. 구성 요소 업데이트 승인 대화 상자는 다음 오류 메시지와 함께 설치에 실패 했습니다. "자동 업데이트 동의 허용 되지 않습니다." 다음 구성 요소를 설치 하지 못했습니다.-업데이트 승인 대화 상자

9. **닫기**를 클릭합니다.

#### <a name="to-create-and-test-the-setup-program-by-clicking-i-agree"></a>동의를 만들고 설치 프로그램을 클릭 하 여 테스트

1. **솔루션 탐색기**를 배포 하려는 응용 프로그램의 이름을 클릭 합니다.

2. **프로젝트** 메뉴에서 *ProjectName* **속성**을 클릭합니다.

3. 클릭 합니다 **게시** 페이지를 선택한 다음 클릭 **지금 게시**합니다.

4. 게시 출력을 자동으로 열리지 않는 경우 게시 출력으로 이동 합니다.

5. 실행 합니다 *Setup.exe* 프로그램입니다.

     설치 프로그램 업데이트 승인 대화 상자 소프트웨어 사용권 계약을 보여 줍니다.

6. 소프트웨어 사용권 계약을 읽고 클릭 **Accept**합니다.

     업데이트 승인 대화 상자 응용 프로그램 표시 하 고 다음 텍스트를 보여 줍니다. 응용 프로그램을 설치 하려고 합니다. 웹에서 최신 업데이트를 확인 합니다. 동의 클릭 하 여 인터넷에 자동 업데이트를 확인 하려면 응용 프로그램을 인증 합니다.

7. 클릭 **동의 함**를 클릭 하 고 **계속**합니다.

     응용 프로그램 설치를 시작 합니다.

8. 응용 프로그램 설치 대화 상자가 나타나면 클릭 **설치**합니다.

## <a name="see-also"></a>참고자료
- [애플리케이션 배포 필수 구성 요소](../deployment/application-deployment-prerequisites.md)
- [부트스트래퍼 패키지 만들기](../deployment/creating-bootstrapper-packages.md)
- [방법: 제품 매니페스트 만들기](../deployment/how-to-create-a-product-manifest.md)
- [방법: 패키지 매니페스트 만들기](../deployment/how-to-create-a-package-manifest.md)
- [제품 및 패키지 스키마 참조](../deployment/product-and-package-schema-reference.md)