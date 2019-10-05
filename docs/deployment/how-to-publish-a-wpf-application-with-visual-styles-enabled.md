---
title: '방법: 사용 하도록 설정 하는 비주얼 스타일을 사용 하 여 WPF 응용 프로그램 게시 | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 73b22b02-fc75-42aa-82d3-51fdcaf8e5c8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4ed9a9a349f2496343a9a9828cd436d8d4015aa9
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62898349"
---
# <a name="how-to-publish-a-wpf-application-with-visual-styles-enabled"></a>방법: 비주얼 스타일을 사용하여 WPF 애플리케이션 게시

비주얼 스타일을 사용자가 선택한 테마에 따라 변경 되는 공용 컨트롤의 모양을 사용 하도록 설정 합니다. 기본적으로 비주얼 스타일을 수동으로 활성화 해야 하므로 Windows Presentation Foundation (WPF) 응용 프로그램에 대 한 사용 되지 않습니다. 그러나 WPF 응용 프로그램에 대 한 비주얼 스타일을 사용 하도록 설정 하 고 다음 솔루션을 게시 하면 오류가 발생 합니다. 이 항목에서는이 오류 및 사용 하도록 설정 하는 비주얼 스타일을 사용 하 여 WPF 응용 프로그램을 게시 하기 위한 프로세스를 해결 하는 방법을 설명 합니다. 비주얼 스타일에 대 한 자세한 내용은 참조 하세요. [비주얼 스타일이 개요](/windows/desktop/Controls/visual-styles-overview)합니다. 오류 메시지에 대 한 자세한 내용은 참조 하세요. [ClickOnce 배포 관련 오류 문제 해결](../deployment/troubleshooting-specific-errors-in-clickonce-deployments.md)합니다.

 오류를 해결 하 고 솔루션을 게시 하려면 다음 작업을 수행 해야 합니다.

- [비주얼 스타일을 사용 하지 않고 솔루션을 게시할](#publish-the-solution-without-visual-styles-enabled)합니다.

- [매니페스트 파일을 만듭니다](#create-a-manifest-file)합니다.

- [게시 된 솔루션의 실행 파일에 매니페스트 파일을 포함](#embed-the-manifest-file-into-the-executable-file-of-the-published-solution)합니다.

- [응용 프로그램 및 배포 매니페스트에 서명](#sign-the-application-and-deployment-manifests)합니다.

  그런 다음 최종 사용자가 응용 프로그램을 설치 하려는 위치에 게시 된 파일을 이동할 수 있습니다.

## <a name="publish-the-solution-without-visual-styles-enabled"></a>비주얼 스타일을 사용 하지 않고 솔루션을 게시 합니다.

1. 프로젝트가 비주얼 스타일을 사용 하지 않았는지 확인 합니다. 먼저, 다음 XML에 대 한 프로젝트의 매니페스트 파일을 확인 합니다. 그런 다음 XML가 있는 경우에 XML을 주석 태그를 사용 하 여 묶습니다.

     기본적으로 시각적 스타일 사용 되지 않습니다.

    ```xml
    <dependency>
        <dependentAssembly>
            <assemblyIdentity type="win32" name="Microsoft.Windows.Common-Controls" version="6.0.0.0" processorArchitecture="*" publicKeyToken="6595b64144ccf1df" language="*" />
        </dependentAssembly>
    </dependency>
    ```

     다음 절차에는 프로젝트와 연결 된 매니페스트 파일을 열려고 하는 방법을 보여 줍니다.

    **Visual Basic 프로젝트에서 매니페스트 파일을 열려면**

    1. 메뉴 모음에서 **프로젝트**하십시오 *ProjectName* **속성**여기서 *ProjectName* WPF 프로젝트의 이름입니다.

         WPF 프로젝트에 대 한 속성 페이지가 나타납니다.

    2. 에 **응용 프로그램** 탭에서 **Windows 설정 보기**합니다.

         app.manifest 파일이 열립니다는 **코드 편집기**합니다.

    **C# 프로젝트에서 매니페스트 파일을 열려면**

    1. 메뉴 모음에서 **프로젝트**하십시오 *ProjectName* **속성**여기서 *ProjectName* WPF 프로젝트의 이름입니다.

         WPF 프로젝트에 대 한 속성 페이지가 나타납니다.

    2. 에 **응용 프로그램** 탭, 매니페스트 필드에 표시 되는 이름을 기록해 둡니다. 이 프로젝트와 연결 된 매니페스트의 이름입니다.

        > [!NOTE]
        > 하는 경우 **기본 설정 사용 하 여 매니페스트 포함** 또는 **매니페스트 없이 응용 프로그램 만들기** 비주얼 스타일을 사용 하지 매니페스트 필드에 표시 합니다. 매니페스트 파일의 이름에에서 나타나는 경우 매니페스트 필드,이 절차에서는 다음 단계를 진행 합니다.

    3. **솔루션 탐색기**에서 **모든 파일 표시**를 선택합니다.

         이 단추 등 제외 되는 일반적으로 숨겨져 있는 모든 프로젝트 항목을 보여 줍니다. 매니페스트 파일을 프로젝트 항목으로 표시 됩니다.

2. 빌드하고 솔루션을 게시 합니다. 솔루션을 게시 하는 방법에 대 한 자세한 내용은 참조 하세요. [방법: 게시 마법사를 사용하여 ClickOnce 애플리케이션 게시](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)를 참조하세요.

## <a name="create-a-manifest-file"></a>매니페스트 파일 만들기

1. 메모장 파일에 다음 XML을 붙여 넣습니다.

     이 XML 비주얼 스타일을 지 원하는 컨트롤을 포함 하는 어셈블리를 설명 합니다.

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <asmv1:assembly manifestVersion="1.0"
        xmlns="urn:schemas-microsoft-com:asm.v1"
        xmlns:asmv1="urn:schemas-microsoft-com:asm.v1"
        xmlns:asmv2="urn:schemas-microsoft-com:asm.v2"
        xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
        <dependency>
            <dependentAssembly>
                <assemblyIdentity type="win32" name="Microsoft.Windows.Common-Controls" version="6.0.0.0" processorArchitecture="*" publicKeyToken="6595b64144ccf1df" language="*" />
            </dependentAssembly>
        </dependency>
    </asmv1:assembly>
    ```

2. 메모장에서 클릭 **파일**를 클릭 하 고 **다른 이름으로 저장**합니다.

3. 에 **다른 이름으로 저장** 대화 상자의 합니다 **형식으로 저장** 드롭 다운 목록에서 **모든 파일**합니다.

4. 에 **파일 이름** 상자, 파일 이름을 지정 하 고 추가 *.manifest* 파일 이름의 끝에 있습니다. 예를 들어: *themes.manifest*합니다.

5. 선택 된 **폴더 찾아보기** 단추, 모든 폴더를 선택 하 고, 클릭 **저장**합니다.

    > [!NOTE]
    > 나머지 절차에서는이 파일 이름은 가정 *themes.manifest* 파일에 저장 되는 및를 *C:\temp* 컴퓨터에 디렉터리입니다.

## <a name="embed-the-manifest-file-into-the-executable-file-of-the-published-solution"></a>게시 된 솔루션의 실행 파일에 매니페스트 파일을 포함

1. 엽니다는 **Visual Studio 명령 프롬프트**합니다.

    여는 방법에 대 한 자세한를 **Visual Studio 명령 프롬프트**를 참조 하세요 [명령 프롬프트](/dotnet/framework/tools/developer-command-prompt-for-vs)합니다.

   > [!NOTE]
   > 나머지 단계를 솔루션에 대 한 다음과 같은 가정을 확인합니다.
   >
   > - 솔루션의 이름은 **MyWPFProject**합니다.
   > - 솔루션은 다음 디렉터리에 있는: `%UserProfile%\Documents\Visual Studio 2010\Projects\`합니다.
   >
   > - 솔루션은 다음 디렉터리에 게시: `%UserProfile%\Documents\Visual Studio 2010\Projects\publish`합니다.
   > - 게시 된 응용 프로그램 파일의 최신 버전은 다음 디렉터리에 있습니다. `%UserProfile%\Documents\Visual Studio 2010\Projects\publish\Application Files\WPFApp_1_0_0_0`
   >
   > 이름이 나 위에서 설명한 디렉터리 위치를 사용할 필요가 없습니다. 이름 및 위치를 위에서 설명한 솔루션을 게시 하는 데 필요한 단계를 설명 하기 위해 사용 됩니다.

2. 명령 프롬프트에서 게시 된 응용 프로그램 파일의 최신 버전이 포함 된 디렉터리 경로 변경 합니다. 다음 예제에서는이 단계를 보여 줍니다.

   ```cmd
   cd "%UserProfile%\Documents\Visual Studio 2010\Projects\MyWPFProject\publish\Application Files\WPFApp_1_0_0_0"
   ```

3. 명령 프롬프트에서 응용 프로그램의 실행 파일에 매니페스트 파일을 포함 하려면 다음 명령을 실행 합니다.

   ```cmd
   mt -manifest c:\temp\themes.manifest -outputresource:MyWPFApp.exe.deploy
   ```

## <a name="sign-the-application-and-deployment-manifests"></a>응용 프로그램 및 배포 매니페스트 서명

1. 명령 프롬프트에서 제거 하려면 다음 명령을 실행 합니다 *.deploy* 현재 디렉터리에서 실행 파일에서 확장 합니다.

   ```cmd
   ren MyWPFApp.exe.deploy MyWPFApp.exe
   ```

   > [!NOTE]
   > 이 예제에서는 하나의 파일에 있다고 가정 합니다 *.deploy* 파일 확장명입니다. 이 디렉터리에 있는 모든 파일 이름을 바꿔야 하는 *.deploy* 파일 확장명입니다.

2. 명령 프롬프트에서 응용 프로그램 매니페스트에 서명 하려면 다음 명령을 실행 합니다.

   ```cmd
   mage -u MyWPFApp.exe.manifest -cf ..\..\..\MyWPFApp_TemporaryKey.pfx
   ```

   > [!NOTE]
   > 이 예제를 사용 하 여 매니페스트에 서명 하는 것으로 가정 합니다 *.pfx* 프로젝트의 파일입니다. 매니페스트를 서명 하지 않는 경우는 생략할 수 있습니다는 `-cf` 이 예제에 사용 되는 매개 변수입니다. 암호에 필요한 인증서를 사용 하 여 매니페스트에 서명 하는 경우 지정 된 `-password` 옵션 (`For example: mage -u MyWPFApp.exe.manifest -cf ..\..\..\MyWPFApp_TemporaryKey.pfx - password Password`).

3. 명령 프롬프트에서 다음 명령을 추가 하는 *.deploy* 이 절차의 이전 단계에서 이름을 바꾼 파일의 이름으로 확장 합니다.

   ```
   ren MyWPFApp.exe MyWPFApp.exe.deploy
   ```

   > [!NOTE]
   > 이 예에서는 하나의 파일만 가정 했습니다를 *.deploy* 파일 확장명입니다. 이전에이 디렉터리의 모든 파일 이름을 바꿔야 하는 *.deploy* 파일 이름 확장명입니다.

4. 명령 프롬프트에서 배포 매니페스트에 서명 하려면 다음 명령을 실행 합니다.

   ```
   mage -u ..\..\MyWPFApp.application -appm MyWPFApp.exe.manifest -cf ..\..\..\MyWPFApp_TemporaryKey.pfx
   ```

   > [!NOTE]
   > 이 예제를 사용 하 여 매니페스트에 서명 하는 것으로 가정 합니다 *.pfx* 프로젝트의 파일입니다. 매니페스트를 서명 하지 않는 경우는 생략할 수 있습니다는 `-cf` 이 예제에 사용 되는 매개 변수입니다. 암호에 필요한 인증서를 사용 하 여 매니페스트에 서명 하는 경우 지정 된 `-password` 이 예제와 같이 옵션을:`For example: mage -u MyWPFApp.exe.manifest -cf ..\..\..\MyWPFApp_TemporaryKey.pfx - password Password`합니다.

   다음이 단계를 수행한 후에 최종 사용자가 응용 프로그램을 설치 하려는 위치에 게시 된 파일을 이동할 수 있습니다. 솔루션을 종종 업데이트 하려는 경우 이러한 명령을 스크립트에 이동할 수 있으며 새 버전을 게시할 때마다 스크립트를 실행 수 있습니다.

## <a name="see-also"></a>참고자료

-[ClickOnce 배포 관련 오류 문제 해결](../deployment/troubleshooting-specific-errors-in-clickonce-deployments.md)
- [비주얼 스타일 개요](/windows/desktop/Controls/visual-styles-overview)
- [시각적 개체 스타일 사용](/windows/desktop/Controls/cookbook-overview)
- [명령 프롬프트](/dotnet/framework/tools/developer-command-prompt-for-vs)
