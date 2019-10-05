---
title: ClickOnce를 사용 하 여 Office 솔루션 배포
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, deploying solutions
- ClickOnce deployment [Office development in Visual Studio], deploying solutions
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 9e5c6282c446fbc9ef24433e40452cca2b1b905a
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63441851"
---
# <a name="deploy-an-office-solution-by-using-clickonce"></a>ClickOnce를 사용 하 여 Office 솔루션 배포
  ClickOnce를 사용하면 Office 솔루션을 더 적은 단계로 배포할 수 있습니다. 업데이트를 게시하는 경우 솔루션에서 자동으로 이를 감지하여 설치합니다. 그러나 ClickOnce에서는 컴퓨터의 각 사용자에 대해 별도로 솔루션을 설치하도록 합니다. Windows Installer를 사용 하 여 고려해 야 하므로 ( *.msi*) 둘 이상의 사용자를 동일한 컴퓨터에 솔루션을 실행 합니다.

## <a name="in-this-topic"></a>항목 내용

- [솔루션 게시](#Publish)

- [솔루션에 신뢰를 부여 하는 방법 결정](#Trust)

- [솔루션을 설치할 수 있도록](#Helping)

- [최종 사용자의 컴퓨터 (문서 수준 사용자 지정에만 해당)에 솔루션 문서 저장](#Put)

- [(문서 수준 사용자 지정에만 해당) SharePoint를 실행 하는 서버에 솔루션 문서 저장](#SharePoint)

- [사용자 지정 설치 관리자 만들기](#Custom)

- [업데이트 게시](#Update)

- [솔루션의 설치 위치 변경](#Location)

- [이전 버전으로 솔루션 롤백](#Roll)

  Windows Installer 파일을 만들어 Office 솔루션을 배포 하는 방법에 대 한 자세한 내용은 참조 하세요. [Windows Installer를 사용 하 여 Office 솔루션 배포](../vsto/deploying-an-office-solution-by-using-windows-installer.md)합니다.

## <a name="Publish"></a> 솔루션 게시
 사용 하 여 솔루션을 게시할 수는 **게시 마법사** 또는 **프로젝트 디자이너**합니다. 이 절차에서는 합니다 **프로젝트 디자이너** 게시 옵션의 전체 집합을 제공 하기 때문입니다. 참조 [게시 마법사 &#40;Visual Studio에서 Office 개발&#41;](../vsto/publish-wizard-office-development-in-visual-studio.md)합니다.

#### <a name="to-publish-the-solution"></a>솔루션을 게시하려면

1. **솔루션 탐색기**, 프로젝트에 대 한 명명 된 노드를 선택 합니다.

2. 메뉴 모음에서 선택 **프로젝트**하십시오 *ProjectName* **속성**합니다.

3. 에 **프로젝트 디자이너**, 선택 합니다 **게시** 다음 그림에 표시 된 탭 합니다.

    ![프로젝트 디자이너의 게시 탭](../vsto/media/vsto-publishtab.png "프로젝트 디자이너의 게시 탭")

4. 에 **폴더 위치 게시 (ftp 서버 또는 파일 경로)** 상자에 넣을 폴더의 경로 입력 합니다는 **프로젝트 디자이너** 솔루션 파일을 복사 합니다.

    다음과 같은 형식의 경로를 입력할 수 있습니다.

   - 로컬 경로 (예를 들어 *C:\FolderName\FolderName*).

   - 네트워크의 폴더에 범용 명명 규칙 (UNC) 경로 (예를 들어  *\\\ServerName\FolderName*).

   - 상대 경로 (예를 들어 *PublishFolder\\* , 프로젝트가 기본적으로 게시 되는 폴더인).

5. 에 **설치 폴더 URL** 상자 최종 사용자가 솔루션을 찾을 위치의 정규화 된 경로 입력 합니다.

    위치를 알 수 없는 아직 경우,이 필드에 아무것도 입력 하지 마십시오. 기본적으로 ClickOnce에서는 사용자가 솔루션을 설치한 폴더에서 업데이트를 찾습니다.

6. **필수 구성 요소** 단추를 선택합니다.

7. 에 **필수 구성 요소** 대화 상자에서 **필수 구성 요소를 설치 하려면 설치 프로그램 만들기** 확인란을 선택 합니다.

8. 에 **설치 필수 구성 요소 선택** 목록에 대 한 확인란을 선택 합니다 **Windows Installer 4.5** 및 적절 한.NET Framework 패키지 합니다.

    예를 들어 경우 솔루션이 대상으로 합니다 [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]에 대 한 확인란을 선택 **Windows Installer 4.5** 하 고 **Microsoft.NET Framework 4.5 Full**.

9. 솔루션이.NET Framework 4.5를 대상으로 하는 경우 선택 합니다 **Visual Studio 2010 Tools for Office Runtime** 확인란 합니다.

    > [!NOTE]
    > 이 확인란은 기본적으로 표시 되지 않습니다. 이 확인란을 표시하려면 부트스트래퍼 패키지를 만들어야 합니다. 참조 [부트스트래퍼 패키지는 Office 2013 VSTO 추가 기능에 대 한 Visual Studio 2012를 사용 하 여 만들기](create-vsto-add-ins-for-office-by-using-visual-studio.md)합니다.

10. 아래 **필수 구성 요소에 대 한 설치 위치를 지정**, 표시 및 선택한 옵션 중 하나를 선택 합니다 **확인** 단추입니다.

     다음 표는 각 옵션에 대해 설명합니다.

    |옵션|설명|
    |------------|-----------------|
    |**구성 요소 공급업체의 웹 사이트에서 필수 구성 요소 다운로드**|사용자에게 공급업체로부터 이러한 필수 구성 요소를 다운로드하여 설치하라는 메시지가 나타납니다.|
    |**내 응용 프로그램과 동일한 위치에서 필수 구성 요소 다운로드**|필수 구성 요소 소프트웨어가 솔루션과 함께 설치되어 있습니다. 이 옵션을 선택하면 자동으로 모든 필수 구성 요소 패키지가 게시 위치에 복사됩니다. 이 옵션이 작동하려면 필수 구성 요소 패키지가 개발 컴퓨터에 있어야 합니다.|
    |**다음 위치에서 필수 구성 요소 다운로드**|모든 필수 구성 요소 패키지가 지정한 위치에 복사되고 솔루션을 사용하여 설치됩니다.|

     참조 [필수 조건 대화 상자](../ide/reference/prerequisites-dialog-box.md)합니다.

11. 선택 된 **업데이트** 단추, 빈도 또는 사용 하려는 각 최종 사용자의 VSTO 추가 기능에서 사용자 지정 업데이트를 확인 한 다음에 지정 합니다 **확인** 단추.

    > [!NOTE]
    > CD 또는 이동식 드라이브를 사용 하 여 배포 하는 경우 선택 합니다 **업데이트 확인 안 함** 옵션 단추입니다.

     업데이트를 게시 하는 방법에 대 한 정보를 참조 하세요 [업데이트를 게시](#Update)합니다.

12. 선택 합니다 **옵션** 단추, 옵션을 검토 합니다 **옵션** 대화 상자를 선택한 후는 **확인** 단추.

13. 선택 된 **지금 게시** 단추입니다.

     이 절차의 앞부분에서 지정한 게시 폴더에 다음과 같은 폴더 및 파일이 추가됩니다.

    - 합니다 **응용 프로그램 파일** 폴더입니다.

    - 설치 프로그램

    - 최신 버전의 배포 매니페스트를 가리키는 배포 매니페스트

      합니다 **응용 프로그램 파일** 게시 하는 각 버전에 대 한 하위 폴더 포함 합니다. 각 버전별 하위 폴더에는 다음 파일이 들어 있습니다.

    - 애플리케이션 매니페스트

    - 배포 매니페스트

    - 사용자 지정 어셈블리

      다음 그림에서는 Outlook VSTO 추가 기능용 게시 폴더의 구조를 보여 줍니다.

      ![게시 폴더 구조](../vsto/media/publishfolderstructure.png "게시 폴더 구조")

    > [!NOTE]
    > ClickOnce 추가 합니다 *.deploy* 어셈블리에는 확장 보안된 설치 인터넷 정보 서비스 (IIS)의 안전 하지 않은 확장명 때문에 파일을 차단 하지 않도록 합니다. ClickOnce는 사용자가 솔루션을 설치 하는 경우 제거 합니다 *.deploy* 확장 합니다.

14. 이 절차의 앞부분에서 지정한 설치 위치에 솔루션 파일을 복사합니다.

## <a name="Trust"></a> 솔루션에 신뢰를 부여 하는 방법 결정
 사용자 컴퓨터에서 솔루션을 실행하려면 먼저 관리자가 신뢰를 부여하거나 사용자가 솔루션을 설치할 때 신뢰 프롬프트에 응답해야 합니다. 솔루션에 신뢰를 부여하려면 신뢰할 수 있고 확인된 게시자를 식별하는 인증서를 사용하여 매니페스트에 서명합니다. 참조 [응용 프로그램 및 배포 매니페스트에 서명 하 여 솔루션을 신뢰](../vsto/granting-trust-to-office-solutions.md#Signing)합니다.

 문서 수준 사용자 지정을 배포 하는 사용자의 컴퓨터에서 폴더에 문서를 저장 하거나 SharePoint 사이트에서 문서를 사용할 수 있도록 하려는 경우 Office 문서 위치 신뢰 한다고 확인 합니다. 참조 [문서에 신뢰 부여](../vsto/granting-trust-to-documents.md)합니다.

## <a name="Helping"></a> 솔루션을 설치할 수 있도록
 사용자가 솔루션을 설치할 수 배포 매니페스트를 열어 설치 프로그램을 실행 하 여 또는 문서 수준 사용자 지정 하는 동안 문서를 직접 열어 합니다. 가장 좋은 방법은 사용자가 설치 프로그램을 사용하여 솔루션을 설치하는 것입니다. 나머지 두 방식의 없는 필수 구성 요소 소프트웨어가 설치 되어 있는지 확인 합니다. 사용자가 설치 위치에서 문서를 열려는 경우, Office 애플리케이션의 보안 센터에서 신뢰할 수 있는 위치 목록에 이 문서를 추가해야 합니다.

### <a name="opening-the-document-of-a-document-level-customization"></a>문서 수준 사용자 지정의 문서 열기
 사용자는 문서 수준 사용자 지정의 문서를 설치 위치에서 바로 열거나 문서를 자신의 로컬 컴퓨터로 복사한 다음 이 복사본을 열 수 있습니다.

 가장 좋은 방법은 여러 사용자가 동시에 동일한 복사본을 열려고 시도하지 않도록 사용자가 자신의 컴퓨터에서 문서의 복사본을 여는 것입니다. 이 방법을 적용하려면 사용자 컴퓨터에 문서를 복사하도록 설치 프로그램을 구성하면 됩니다. 참조 [최종 사용자의 컴퓨터 (문서 수준 사용자 지정에만 해당)에 솔루션 문서 저장](#Put)합니다.

### <a name="install-the-solution-by-opening-the-deployment-manifest-from-an-iis-website"></a>IIS 웹 사이트에서 배포 매니페스트를 열어 솔루션을 설치 합니다.
 사용자는 웹에서 배포 매니페스트를 열어 Office 솔루션을 설치할 수 있습니다. 그러나 인터넷 정보 서비스 (IIS)의 보안된 설치 파일을 차단 합니다 *.vsto* 확장 합니다. 따라서 IIS를 사용하여 Office 솔루션을 배포하려면 먼저 IIS에서 MIME 형식을 정의해야 합니다.

##### <a name="to-add-the-vsto-mime-type-to-iis-60"></a>IIS 6.0에 .vsto MIME 형식을 추가하려면

1. IIS 6.0을 실행 하는 서버에서 선택 **시작** > **프로그램도** > **관리 도구**  >   **인터넷 정보 서비스 (IIS) 관리자**합니다.

2. 컴퓨터 이름을 선택 합니다 **웹 사이트** 폴더 또는 웹 사이트를 구성 하는 합니다.

3. 메뉴 모음에서 선택 **동작** > **속성**합니다.

4. 에 **HTTP 헤더** 탭을 선택 합니다 **MIME 형식** 단추입니다.

5. 에 **MIME 형식** 창 선택 합니다 **새로 만들기** 단추입니다.

6. 에 **MIME 형식을** 창 입력 **.vsto** 확장명으로 입력 **application/x-ms-vsto** MIME로 입력 한 다음 새 설정을 적용 합니다.

    > [!NOTE]
    > 변경 내용이 적용되려면 World Wide Web Publishing 서비스를 다시 시작하거나 작업자 프로세스가 재생될 때까지 기다려야 합니다. 열을 추가한 후 다음 브라우저의 디스크 캐시를 플러시할 해야 합니다 *.vsto* 파일을 다시 합니다.

##### <a name="to-add-the-vsto-mime-type-to-iis-70"></a>IIS 7.0에 .vsto MIME 형식을 추가하려면

1. IIS 7.0을 실행 하는 서버에서 선택 **시작** > **프로그램도** > **Accessories**합니다.

2. 바로 가기 메뉴를 열고 **명령 프롬프트**를 선택한 후 **관리자 권한으로 실행 합니다.**

3. 에 **열기** 상자에 다음 경로 입력 한 다음를 선택 합니다 **확인** 단추입니다.

    ```cmd
    %windir%\system32\inetsrv
    ```

4. 다음 명령을 입력한 다음 새로운 설정을 적용합니다.

    ```cmd
    set config /section:staticContent /+[fileExtension='.vsto',mimeType='application/x-ms-vsto']
    ```

    > [!NOTE]
    > 변경 내용이 적용되려면 World Wide Web Publishing 서비스를 다시 시작하거나 작업자 프로세스가 재생될 때까지 기다려야 합니다. 열을 추가한 후 다음 브라우저의 디스크 캐시를 플러시할 해야 합니다 *.vsto* 파일을 다시 합니다.

## <a name="Put"></a> 최종 사용자의 컴퓨터 (문서 수준 사용자 지정에만 해당)에 솔루션 문서 저장
 배포 후 작업을 만들어 최종 사용자의 컴퓨터에 솔루션의 문서에 복사할 수 있습니다. 따라서 사용자는 수동으로 문서를 복사 하도록 설치 위치에서 해당 컴퓨터에 솔루션을 설치한 후 없습니다. 배포 후 작업을 정의 하는 클래스를 만들기, 빌드 및 솔루션을 게시, 응용 프로그램 매니페스트를 수정 및 응용 프로그램 및 배포 매니페스트에 다시 서명 해야 합니다.

 다음 절차에서는 프로젝트 이름 인지 가정 **ExcelWorkbook** 이라는 만든된 폴더에 솔루션을 게시 하 고 **C:\publish** 컴퓨터에 있습니다.

### <a name="create-a-class-that-defines-the-post-deployment-action"></a>배포 후 작업을 정의하는 클래스를 만듭니다.

1. 메뉴 모음에서 선택 **파일** > **추가** > **새 프로젝트**합니다.

2. 에 **새 프로젝트 추가** 대화 상자의 **설치 된 템플릿** 창 선택 합니다 **Windows** 폴더입니다.

3. 에 **템플릿을** 창 선택 합니다 **클래스 라이브러리** 템플릿.

4. 에 **이름** 필드를 입력 합니다 **FileCopyPDA**를 선택한 후는 **확인** 단추입니다.

5. **솔루션 탐색기**를 선택 합니다 **FileCopyPDA** 프로젝트입니다.

6. 메뉴 모음에서 **프로젝트** > **참조 추가**를 선택합니다.

7. 에 **.NET** 탭에 대 한 참조를 추가 합니다 `Microsoft.VisualStudio.Tools.Applications.Runtime` 고 `Microsoft.VisualStudio.Tools.Applications.ServerDocument`입니다.

8. 클래스 이름을 `FileCopyPDA`로 바꾼 다음 파일의 내용을 이 코드로 바꿉니다. 이 코드는 다음 작업을 수행합니다.

   - 사용자의 바탕 화면에 문서를 복사합니다.

   - 배포 매니페스트에 대 한 정규화 된 경로에 대 한 상대 경로에서 _AssemblyLocation 속성을 변경합니다.

   - 사용자가 솔루션을 제거한 경우 파일을 삭제합니다.

     [!code-vb[Trin_ExcelWorkbookPDA#7](../vsto/codesnippet/VisualBasic/trin_excelworkbookpda/filecopypda/class1.vb#7)]
     [!code-csharp[Trin_ExcelWorkbookPDA#7](../vsto/codesnippet/CSharp/trin_excelworkbookpda/filecopypda/class1.cs#7)]

### <a name="build-and-publish-the-solution"></a>솔루션을 빌드하고 게시합니다.

1. **솔루션 탐색기**에 대 한 바로 가기 메뉴를 열고 합니다 **FileCopyPDA** 프로젝트를 선택한 후 **빌드**합니다.

2. 바로 가기 메뉴를 열고 합니다 **ExcelWorkbook** 프로젝트를 선택한 후 **빌드**합니다.

3. 바로 가기 메뉴를 열고 합니다 **ExcelWorkbook** 프로젝트를 선택한 후 **참조 추가**합니다.

4. **참조 추가** 대화 상자를 선택 합니다 **프로젝트** 탭을 선택 **FileCopyPDA**를 선택한 후는 **확인** 단추.

5. **솔루션 탐색기**를 선택 합니다 **ExcelWorkbook** 프로젝트입니다.

6. 메뉴 모음에서 **프로젝트** > **새 폴더**합니다.

7. Enter **데이터**를 선택 합니다 **Enter** 키입니다.

8. **솔루션 탐색기**를 선택 합니다 **데이터** 폴더입니다.

9. 메뉴 모음에서 선택 **프로젝트** > **기존 항목 추가**합니다.

10. 에 **기존 항목 추가** 대화 상자에 대 한 출력 디렉터리를 찾습니다는 **ExcelWorkbook** 프로젝트를 선택 합니다 **ExcelWorkbook.xlsx** 파일을 열고 다음을  **추가** 단추입니다.

11. **솔루션 탐색기** 를 선택 합니다 **ExcelWorkbook.xlsx** 파일입니다.

12. 에 **속성** 창에서를 **빌드 작업** 속성을 **콘텐츠** 및 **출력 디렉터리로 복사** 속성 **변경 된 내용만 복사**합니다.

     다음이 단계를 완료 한 경우 프로젝트는 다음 그림에서는 것과 비슷합니다.

     ![배포 후 작업의 프로젝트 구조입니다. ](../vsto/media/vsto-postdeployment.png "배포 후 작업의 프로젝트 구조입니다.")

13. 게시 된 **ExcelWorkbook** 프로젝트입니다.

### <a name="modify-the-application-manifest"></a>애플리케이션 매니페스트 수정

1. 솔루션 디렉터리를 엽니다 **c:\publish**를 사용 하 여 **파일 탐색기**합니다.

2. 엽니다는 **응용 프로그램 파일** 솔루션의 버전을 게시 폴더 및 다음 가장 최근의에 해당 하는 폴더를 엽니다.

3. 엽니다는 **ExcelWorkbook.dll.manifest** 메모장과 같은 텍스트 편집기에서 파일입니다.

4. `</vstav3:update>` 요소 뒤에 다음 코드를 추가합니다. 클래스 특성에 대 한는 `<vstav3:entryPoint>` 요소 구문을 사용 합니다. *NamespaceName.ClassName*. 다음 예제에서는 네임스페이스 및 클래스 이름이 같기 때문에 결과 진입점 이름은 `FileCopyPDA.FileCopyPDA`입니다.

    ```xml
    <vstav3:postActions>
      <vstav3:postAction>
        <vstav3:entryPoint
          class="FileCopyPDA.FileCopyPDA">
          <assemblyIdentity
            name="FileCopyPDA"
            version="1.0.0.0"
            language="neutral"
            processorArchitecture="msil" />
        </vstav3:entryPoint>
        <vstav3:postActionData>
        </vstav3:postActionData>
      </vstav3:postAction>
    </vstav3:postActions>
    ```

### <a name="re-sign-the-application-and-deployment-manifests"></a>애플리케이션 및 배포 매니페스트 다시 서명

1. 에 **%USERPROFILE%\Documents\Visual Studio 2013\Projects\ExcelWorkbook\ExcelWorkbook** 폴더를 복사 합니다 **ExcelWorkbook_TemporaryKey.pfx** 인증서 파일을 다음에 붙여 넣습니다 합니다  *PublishFolder* **files\excelworkbook**\__MostRecentPublishedVersion_ 폴더입니다.

2. Visual Studio 명령 프롬프트를 열고 디렉터리를 변경 합니다 **c:\publish\Application Files\ExcelWorkbook**\__MostRecentPublishedVersion_ 폴더 (예를 들어 **c:\publish\Application Files\ExcelWorkbook_1_0_0_4**).

3. 다음 명령을 실행하여 수정된 애플리케이션 매니페스트에 서명합니다.

    ```cmd
    mage -sign ExcelWorkbook.dll.manifest -certfile ExcelWorkbook_TemporaryKey.pfx
    ```

     "ExcelWorkbook.dll.manifest에 서명했습니다"라는 메시지가 나타납니다.

4. 변경 된 **c:\publish** 다음 명령을 실행 하 여 폴더 및 다음 업데이트 및 로그인 배포 매니페스트:

    ```cmd
    mage -update ExcelWorkbook.vsto -appmanifest "Application Files\Ex
    celWorkbookMostRecentVersionNumber>\ExcelWorkbook.dll.manifest" -certfile "Application Files\ExcelWorkbookMostRecentVersionNumber>\ExcelWorkbook_TemporaryKey.pfx"
    ```

    > [!NOTE]
    > 이전 예제에서 MostRecentVersionNumber 솔루션의 가장 최근에 게시 된 버전의 버전 번호를 사용 하 여 바꿉니다 (예를 들어 **1_0_0_4**).

     "ExcelWorkbook.vsto에 서명했습니다."라는 메시지가 나타납니다.

5. 복사 합니다 *ExcelWorkbook.vsto* 파일을 합니다 **c:\publish\Application Files\ExcelWorkbook**\__MostRecentVersionNumber_ 디렉터리입니다.

## <a name="SharePoint"></a> (문서 수준 사용자 지정에만 해당) SharePoint를 실행 하는 서버에 솔루션 문서 저장
 SharePoint를 사용하여 최종 사용자에게 문서 수준 사용자 지정을 게시할 수 있습니다. 사용자가 SharePoint 사이트에서 문서를 열면 런타임에 자동으로 공유 네트워크 폴더의 솔루션을 사용자의 로컬 컴퓨터에 설치합니다. 솔루션이 로컬로 설치된 후, 문서가 바탕 화면과 같은 다른 위치에 복사되는 경우에도 사용자 지정은 계속 작동합니다.

#### <a name="to-put-the-document-on-a-server-thats-running-sharepoint"></a>SharePoint를 실행하는 서버에 문서를 저장하려면

1. SharePoint 사이트의 문서 라이브러리에 솔루션 문서를 추가합니다.

2. 다음 방법 중 하나에 해당하는 단계를 수행합니다.

    - Office 구성 도구를 사용하여 모든 사용자 컴퓨터에 있는 Word 또는 Excel의 보안 센터에 SharePoint 실행 서버를 추가합니다.

         참조 [Office 2010의 보안 정책 및 설정](http://go.microsoft.com/fwlink/?LinkId=99227)합니다.

    - 각 사용자는 다음 단계를 수행해야 합니다.

        1. Word 또는 Excel을 열고 로컬 컴퓨터를 선택 합니다 **파일** 탭을 선택한 다음는 **옵션** 단추입니다.

        2. 에 **보안 센터** 대화 상자를 선택 합니다 **신뢰할 수 있는 위치** 단추입니다.

        3. 선택 된 **(권장 하지 않음) 네트워크 상의 신뢰할 수 있는 위치 허용** 확인란을 선택한 후는 **새 위치 추가** 단추입니다.

        4. 에 **경로** 상자에 업로드 한 문서가 포함 된 SharePoint 문서 라이브러리의 URL을 입력 합니다 (예를 들어 *http://SharePointServerName/TeamName/ProjectName/DocumentLibraryName* ).

             와 같은 기본 웹 페이지의 이름을 추가 하지 마세요 *default.aspx* 하거나 *AllItems.aspx*합니다.

        5. 선택 합니다 **이 위치의 하위 폴더도 신뢰할 수 있는** 확인란을 선택한 다음를 선택 합니다 **확인** 단추.

             사용자가 SharePoint 사이트에서 문서를 열면 이 문서가 열리고 사용자 지정이 설치됩니다. 사용자는 바탕 화면에 이 문서를 복사할 수 있습니다. 문서의 속성에서 문서의 네트워크 위치를 가리키므로 사용자 지정은 계속 실행됩니다.

## <a name="Custom"></a> 사용자 지정 설치 관리자 만들기
 솔루션을 게시할 때를 생성 되는 설치 프로그램을 사용 하는 대신, Office 솔루션용 사용자 지정 설치 관리자를 만들 수 있습니다. 예를 들어, 설치를 시작 하려면 스크립트에서 로그인을 사용할 수 있습니다 또는 일괄 처리 파일을 사용 하 여 사용자 개입 없이 솔루션을 설치할 수 있습니다. 이러한 시나리오는 최종 사용자의 컴퓨터에 필수 구성 요소가 이미 설치된 경우에 가장 적합합니다.

 사용자 지정 설치 프로세스의 일부로 Office 솔루션용 설치 관리자 도구를 호출 (*VSTOInstaller.exe*)에 기본적으로 다음 위치에 설치 됩니다.

 *%commonprogramfiles%\microsoft shared\VSTO\10.0\VSTOInstaller.exe*

 도구 위치에 없는 경우 사용할 수 있습니다 합니다 **이 Runtime Setup\v4\InstallerPath** 또는 **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\VSTO Runtime Setup\v4 \InstallerPath** 레지스트리 키를 눌러 해당 도구 경로를 찾습니다.

 다음 매개 변수를 사용할 수 있습니다 *VSTOinstaller.exe*합니다.

| 매개 변수 | 정의 |
|------------------| - |
| /Install 또는 /I | 솔루션을 설치합니다. 이 옵션 뒤에는 배포 매니페스트의 경로가 와야 합니다. 로컬 컴퓨터, UNC(Universal Naming Convention) 파일 공유에 대한 경로를 지정할 수 있습니다. 로컬 경로 지정할 수 있습니다 (*C:\FolderName\PublishFolder*), 상대 경로 (*게시\\* ), 또는 정규화 된 위치 ( *\\\ServerName\ FolderName* 또는 http://<em>ServerName/FolderName</em>). |
| /Uninstall 또는 /U | 솔루션을 제거합니다. 이 옵션 뒤에는 배포 매니페스트의 경로가 와야 합니다. 경로를 로컬 컴퓨터의 UNC 파일 공유로 지정할 수 있습니다. 로컬 경로 지정할 수 있습니다 (*c:\FolderName\PublishFolder*), 상대 경로 (*게시\\* ), 또는 정규화 된 위치 ( *\\\ServerName\ FolderName* 또는 http://<em>ServerName/FolderName</em>). |
| /Silent 또는 /S | 입력에 대한 메시지나 그 밖의 메시지를 사용자에게 표시하지 않고 설치 또는 제거합니다. 신뢰 프롬프트가 필요한 경우 사용자 지정 설치 되거나 업데이트 되지 않습니다. |
| /Help 또는 /? | 도움말 정보를 표시합니다. |

 실행할 때 *VSTOinstaller.exe*, 다음과 같은 오류 코드가 표시 될 수 있습니다.

|오류 코드|정의|
|----------------|----------------|
|0|솔루션이 성공적으로 설치되었거나 제거되었습니다. 또는 VSTOInstaller 도움말이 표시되었습니다.|
|-100|하나 이상의 명령줄 옵션은 유효 하지 않거나 두 번 이상 설정 되었습니다. 입력에 대 한 자세한 내용은 "vstoinstaller /?" 참조 또는 [ClickOnce Office 솔루션에 대 한 사용자 지정 설치 관리자 만들기](https://msdn.microsoft.com/3e5887ed-155f-485d-b8f6-3c02c074085e)합니다.|
|-101|하나 이상의 명령줄 옵션이 유효 하지 않습니다. 자세한 내용을 보려면 "vstoinstaller /?"를 입력하십시오.|
|-200|배포 매니페스트 URI는 유효 하지 않습니다. 자세한 내용을 보려면 "vstoinstaller /?"를 입력하십시오.|
|-201|배포 매니페스트가 잘못 되었으므로 솔루션을 설치할 수 없습니다. 참조 [Deployment manifests for Office 솔루션](../vsto/deployment-manifests-for-office-solutions.md)합니다.|
|-202|Visual Studio Tools for Office 섹션이 응용 프로그램 매니페스트의 잘못 되었으므로 솔루션을 설치할 수 없습니다. 참조 [Office 솔루션에 대 한 응용 프로그램 매니페스트](../vsto/application-manifests-for-office-solutions.md)합니다.|
|-203|다운로드 오류가 발생 했기 때문에 솔루션을 설치할 수 없습니다. 배포 매니페스트의 URI 또는 네트워크 파일 위치를 확인한 다음 다시 시도하세요.|
|-300|보안 예외가 발생 했기 때문에 솔루션을 설치할 수 없습니다. 참조 [Secure Office 솔루션](../vsto/securing-office-solutions.md)합니다.|
|-400|솔루션을 설치할 수 없습니다.|
|-401|솔루션을 제거할 수 없습니다.|
|-500|솔루션을 설치 또는 제거할 수 없거나 배포 매니페스트를 다운로드할 수 없어 작업이 취소되었습니다.|

## <a name="Update"></a> 업데이트 게시
 솔루션을 업데이트 하려면 다시 게시를 사용 하 여 합니다 **프로젝트 디자이너** 또는 **게시 마법사**, 한 다음 업데이트 된 솔루션의 설치 위치로 복사 합니다. 설치 위치에 파일을 복사하면 이전 파일을 덮어쓰게 됩니다.

 다음에 솔루션을 확인 하는 업데이트에 대 한 찾기 하 고 새 버전을 자동으로 로드 합니다.

## <a name="Location"></a> 솔루션의 설치 위치 변경
 솔루션이 게시된 후 설치 경로를 추가하거나 변경할 수 있습니다. 다음 이유 중 하나 이상으로 인해 설치 경로를 변경하려 할 수 있습니다.

- 설치 경로가 알려지기 전에 설치 프로그램을 컴파일한 경우

- 솔루션 파일이 다른 위치에 복사된 경우

- 설치 파일이 호스팅된 서버에 새 이름 또는 위치가 있는 경우

  솔루션의 설치 경로를 변경하려면 설치 프로그램을 업데이트한 다음 사용자가 이를 실행해야 합니다. 문서 수준 사용자 지정의 경우, 사용자가 문서의 속성이 새 위치를 가리키도록 업데이트해야 합니다.

> [!NOTE]
> 해당 문서 속성을 업데이트 하도록 요청 하지 않으려는 경우 사용자가 설치 위치에서 업데이트 된 문서를 요청할 수 있습니다.

#### <a name="to-change-the-installation-path-in-the-setup-program"></a>설치 프로그램에서 설치 경로를 변경하려면

1. 엽니다는 **명령 프롬프트** 창 및 설치 폴더로 디렉터리를 변경 합니다.

2. 설치 프로그램을 실행하고 새 설치 경로를 문자열로 받아들이는 `/url` 매개 변수를 포함시킵니다.

    다음 예제에서는 Fabrikam 웹 사이트에 있는 위치로 설치 경로를 변경하는 방법을 보여 주지만, 해당 URL을 원하는 경로로 바꿀 수 있습니다.

   ```cmd
   setup.exe /url="http://www.fabrikam.com/newlocation"
   ```

   > [!NOTE]
   > 메시지가 표시되어 실행 파일의 시그니처가 무효가 되었음을 알리는 경우, 솔루션 서명에 사용된 인증서는 더 이상 유효하지 않으며 게시자는 알 수 없게 됩니다. 그 결과 사용자는 솔루션의 소스를 신뢰함을 확인한 뒤에야 이를 설치할 수 있게 됩니다.

   > [!NOTE]
   > 현재 URL 값을 표시하려면 `setup.exe /url`을 실행하십시오.

   문서 수준 사용자 지정 사용자 문서를 열고 해당 _AssemblyLocation 속성을 업데이트 합니다. 다음 단계에서는 사용자가 이 작업을 수행하는 방법을 설명합니다.

#### <a name="to-update-the-_assemblylocation-property-in-a-document"></a>문서에서 _AssemblyLocation 속성을 업데이트하려면

1. 에 **파일** 탭에서 **정보**, 다음 그림에 나와 있는 합니다.

     ![Excel의 정보 탭](../vsto/media/vsto-infotab.png "Excel의 정보 탭")

2. 에 **속성** 목록에서 선택 **고급 속성**, 다음 그림에 나와 있는 합니다.

     ![Excel의 고급 속성입니다. ](../vsto/media/vsto-advanceddocumentproperties.png "Excel에 고급 속성입니다.")

3. 에 **사용자 지정** 탭에서 합니다 **속성** 목록에서 다음 그림과 같이 _AssemblyLocation을 선택 합니다.

     ![AssemblyLocation 속성입니다. ](../vsto/media/vsto-assemblylocationproperty.png "The AssemblyLocation 속성입니다.")

     합니다 **값** 상자 배포 매니페스트 식별자를 포함 합니다.

4. 식별자, 전에 형태로 막대를 뒤에 문서의 정규화 된 경로 입력 *경로*|*식별자* (예를 들어 *File://ServerName/ FolderName/FileName | 74744e4b-e4d6-41eb-84f7-ad20346fe2d9*합니다.

     이 식별자의 형식을 지정 하는 방법에 대 한 자세한 내용은 참조 하세요. [사용자 지정 문서 속성 개요](../vsto/custom-document-properties-overview.md)합니다.

5. 선택 된 **확인** 단추 및 그런 다음 저장 하 고 문서를 닫습니다.

6. /url 매개 변수를 사용하지 않고 설치 프로그램을 실행하여 지정한 위치에 솔루션을 설치합니다.

## <a name="Roll"></a> 이전 버전으로 솔루션 롤백
 솔루션을 롤백하면 사용자의 해당 솔루션이 이전 버전으로 돌아갑니다.

#### <a name="to-roll-back-a-solution"></a>솔루션을 롤백하려면

1. 솔루션의 설치 위치를 엽니다.

2. 최상위 폴더를 게시, 배포 매니페스트는 삭제 (합니다 *.vsto* 파일).

3. 롤백할 버전의 하위 폴더를 찾습니다.

4. 해당 하위 폴더의 배포 매니페스트를 최상위 게시 폴더에 복사합니다.

     예를 들어, 호출 되는 솔루션을 롤백하려면 **OutlookAddIn1** 버전 1.0.0.0 버전 1.0.0.1에서에서 파일을 복사 합니다 **OutlookAddIn1.vsto** 에서 **OutlookAddIn1_1_0_0_0** 폴더입니다. 파일을 붙여 넣습니다 최상위 게시 폴더에 대 한 버전별 배포 매니페스트 **OutlookAddIn1_1_0_0_1** 있던 합니다.

     다음 그림에서는 이 예제의 게시 폴더 구조를 보여 줍니다.

     ![게시 폴더 구조](../vsto/media/publishfolderstructure.png "게시 폴더 구조")

     다음에 사용자가 애플리케이션 또는 사용자 지정 문서를 열면 배포 매니페스트 변경 사항이 검색됩니다. 이전 버전의 Office 솔루션은 ClickOnce 캐시에서 실행됩니다.

> [!NOTE]
> 로컬 데이터는 이전 버전의 솔루션 하나에 대해서만 저장됩니다. 두 버전을 롤백하는 경우 로컬 데이터는 보존 되지 않습니다. 로컬 데이터에 대 한 자세한 내용은 참조 하세요. [ClickOnce 응용 프로그램의 로컬 및 원격 데이터 액세스](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md)합니다.

## <a name="see-also"></a>참고자료

- [Office 솔루션 배포](../vsto/deploying-an-office-solution.md)
- [Office 솔루션 게시](../vsto/deploying-an-office-solution-by-using-clickonce.md)
- [방법: ClickOnce를 사용 하 여 Office 솔루션 게시](https://msdn.microsoft.com/2b6c247e-bc04-4ce4-bb64-c4e79bb3d5b8)
- [방법: ClickOnce Office 솔루션 설치](https://msdn.microsoft.com/14702f48-9161-4190-994c-78211fe18065)
- [방법: ClickOnce를 사용 하 여 SharePoint 서버에 문서 수준 Office 솔루션 게시](https://msdn.microsoft.com/2408e809-fb78-42a1-9152-00afa1522e58)
- [ClickOnce office 솔루션에 대 한 사용자 지정 설치 관리자 만들기](https://msdn.microsoft.com/3e5887ed-155f-485d-b8f6-3c02c074085e)