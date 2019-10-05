---
title: ClickOnce 사용 하 여 COM 구성 요소 배포 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- registration-free COM deployment
- ClickOnce deployment, COM components
- COM components, deploying
- deploying applications [ClickOnce], COM components
- components, deploying
ms.assetid: 1a4c7f4c-7a41-45f2-9af4-8b1666469b89
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7032ec5ae03febf6c54978020379769ac742a136
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63406630"
---
# <a name="deploy-com-components-with-clickonce"></a>ClickOnce를 사용하여 COM 구성 요소 배포
일반적으로 기존 COM 구성 요소의 배포는 어려운 작업 이었습니다. 구성 요소는 전역으로 등록 해야 하 고 따라서 겹치는 응용 프로그램 간에 원치 않는 부작용을 일으킬 수 있습니다. 이 이런 아니므로 일반적으로.NET Framework 응용 프로그램에서 문제가 구성 요소는 응용 프로그램에 완전히 격리 또는 side-by-side-호환 됩니다. Visual Studio를 사용 하면 Windows XP 또는 더 높은 운영 체제에서 격리 된 COM 구성 요소를 배포할 수 있습니다.

 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] .NET 응용 프로그램을 배포 하는 쉽고 안전한 메커니즘을 제공 합니다. 그러나 레거시 COM 구성 요소를 사용 하는 응용 프로그램을 배포 하는 것에 대 한 추가 단계를 수행 해야 합니다. 이 항목에서는 격리 된 COM 구성 요소를 배포 하 고 기본 구성 요소를 참조 하는 방법에 설명 합니다 (Visual Basic 6.0 또는 시각적 개체에서 예를 들어, C++).

 격리 된 COM 구성 요소를 배포 하는 방법에 대 한 자세한 내용은 참조 하세요. [Simplify App Deployment with ClickOnce 및 등록이 필요 없는 COM](https://web.archive.org/web/20050326005413/msdn.microsoft.com/msdnmag/issues/05/04/RegFreeCOM/default.aspx)합니다.

## <a name="registration-free-com"></a>등록이 필요 없는 COM
 등록이 필요 없는 COM 배포 및 격리 된 COM 구성 요소를 활성화를 위한 새로운 기술 됩니다. 일반적으로 매니페스트 라는 XML 파일로 시스템 레지스트리에 설치 되어 있는 등록 정보와 모든 구성 요소의 형식 라이브러리에 넣어 작동 하는지는 응용 프로그램과 동일한 폴더에 저장 합니다.

 COM 구성 요소를 격리 개발자의 컴퓨터에 등록 하는 것 이어야 하는데 최종 사용자의 컴퓨터에 등록 하지 않아도 됩니다. COM 구성 요소를 격리 하려면 해당 참조를 설정 되어 하기만 하면 **격리** 속성을 **True**합니다. 기본적으로이 속성 설정할지 **False**, 등록 된 COM 참조로 처리 되어야 함을 나타냅니다. 이 속성이 **True**, 빌드 시이 구성 요소에 대해 생성 될 매니페스트가 있습니다. 에 해당 파일을 설치 하는 동안 응용 프로그램 폴더로 복사 됩니다.

 매니페스트 생성기에서 격리 된 COM 참조를 발견 하는 경우 모든 열거는 `CoClass` 항목 생성 및 해당 등록 데이터를 사용 하 여 각 항목과 일치 하는 구성 요소의 형식 라이브러리의 모든 COM에 대 한 정의 매니페스트 형식 라이브러리 파일의 클래스를 제공 합니다.

## <a name="deploy-registration-free-com-components-using-clickonce"></a>COM 구성 요소 등록이 필요 없는 ClickOnce를 사용 하 여 배포
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 배포 기술 이므로 격리 된 COM 구성 요소를 배포 하는 데 적합 모두 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 등록이 필요 없는 COM 구성 요소를 배포 하기 위해 매니페스트 있는 필요 합니다.

 일반적으로 구성 요소의 작성자는 매니페스트를 제공 해야 합니다. 그렇지 않은 경우 Visual Studio는 자동으로 COM 구성 요소에 대 한 매니페스트를 생성할 수 있지만. 매니페스트 생성 하는 동안 수행 되는 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 게시 프로세스에 대 한 자세한 내용은 참조 하십시오 [ClickOnce 응용 프로그램 게시](../deployment/publishing-clickonce-applications.md)합니다. 또한이 기능을 통해 Visual Basic 6.0과 같은 이전 개발 환경에서 작성 하는 레거시 구성 요소를 활용할 수 있습니다.

 두 가지는 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] COM 구성 요소를 배포 합니다.

- 부트스트래퍼를 사용 하 여 COM 구성 요소; 배포 이 지원 되는 모든 플랫폼에서 작동합니다.

- 기본 구성 요소 격리 (라고도: 등록이 필요 없는 COM) 배포를 사용 합니다. 그러나 Windows XP 또는 더 높은 운영 체제에서이 작동 하는 것은 합니다.

### <a name="example-of-isolating-and-deploying-a-simple-com-component"></a>격리 및 간단한 COM 구성 요소 배포의 예
 등록이 필요 없는 COM 구성 요소 배포를 보여주려면이 예제에서는 격리 된 네이티브 COM 구성 요소를 Visual Basic 6.0을 사용 하 여 만든 참조 하는 Visual Basic에서 Windows 기반 응용 프로그램을 만들기를 사용 하 여 배포 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]합니다.

 먼저 기본 COM 구성 요소를 만드는 해야 합니다.

##### <a name="to-create-a-native-com-component"></a>네이티브 COM 구성 요소를 만들려면

1. Visual Basic 6.0을 사용 합니다 **파일** 메뉴에서 클릭 **새로 만들기**, 다음 **프로젝트**합니다.

2. 에 **새 프로젝트** 대화 상자에서를 **Visual Basic** 선택한 노드는 **ActiveX DLL** 프로젝트. **이름** 상자에 `VB6Hello`을 입력합니다.

    > [!NOTE]
    > 등록이 필요 없는 COM을 사용 하 여 ActiveX DLL 및 ActiveX 컨트롤 프로젝트 형식만 지원 됩니다. ActiveX EXE 프로젝트 형식과 ActiveX 문서 관리 지원 되지 않습니다.

3. **솔루션 탐색기**를 두 번 클릭 **Class1.vb** 텍스트 편집기를 엽니다.

4. Class1.vb에서 생성된 된 코드에 대 한 후 다음 코드를 추가 합니다 `New` 메서드:

    ```vb
    Public Sub SayHello()
       MsgBox "Message from the VB6Hello COM component"
    End Sub
    ```

5. 구성 요소를 빌드하십시오. **빌드할** 메뉴에서 클릭 **솔루션 빌드**합니다.

> [!NOTE]
> COM 제어 프로젝트 형식 및 등록이 필요 없는 COM Dll만 지원 합니다. 등록이 필요 없는 com Exe를 사용할 수 없습니다.

 이제 Windows 기반 응용 프로그램을 만들고 COM 구성 요소에 대 한 참조를 추가할 수 있습니다.

##### <a name="to-create-a-windows-based-application-using-a-com-component"></a>COM 구성 요소를 사용 하 여 Windows 기반 응용 프로그램을 만들려면

1. Visual Basic을 사용 합니다 **파일** 메뉴에서 클릭 **새로 만들기**, 한 다음 **프로젝트**.

2. 에 **새 프로젝트** 대화 상자를 선택 합니다 **Visual Basic** 노드를 선택 **Windows 응용 프로그램**. **이름** 상자에 `RegFreeComDemo`을 입력합니다.

3. **솔루션 탐색기**를 클릭 합니다 **모든 파일 표시** 프로젝트 참조를 표시 하는 단추입니다.

4. 마우스 오른쪽 단추로 클릭 합니다 **참조가** 노드를 선택 **참조 추가** 상황에 맞는 메뉴에서.

5. 에 **참조 추가** 대화 상자에서 클릭 합니다 **찾아보기** 탭 고 vb6hello.dll을 차례로 선택 합니다.

    A **VB6Hello** 참조가 참조 목록에 나타납니다.

6. 가리킨를 **도구 상자**를 선택는 **단추** 컨트롤에 끌어서 놓습니다를 **Form1** 폼입니다.

7. 에 **속성** 창에서 설정 단추 **텍스트** 속성을 **Hello**합니다.

8. 처리기 코드를 추가 하려면 단추를 두 번 클릭 하 고 처리기를 아래와 같이 있도록 코드 파일에서 코드를 추가 합니다.

   ```vb
   Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click
       Dim VbObj As New VB6Hello.Class1
       VbObj.SayHello()
   End Sub
   ```

9. 애플리케이션을 실행합니다. **디버그** 메뉴에서 클릭 **디버깅 시작**합니다.

   다음 컨트롤을 격리 해야 합니다. 응용 프로그램에서 사용 하는 각 COM 구성 요소는 프로젝트에서 COM 참조로 표시 됩니다. 이러한 참조는 아래에 표시 된 **참조** 에서 노드를 **솔루션 탐색기** 창. (직접 사용 하거나 추가할 수 있는 알림을 참조를 **참조 추가** 명령을 합니다 **프로젝트** 메뉴 또는 ActiveX 컨트롤을 폼으로 끌어서에서 직접.)

   다음 단계에는 COM 구성 요소를 격리 하 여 격리 된 컨트롤이 포함 된 업데이트 된 응용 프로그램을 게시 하는 방법을 보여 줍니다.

##### <a name="to-isolate-a-com-component"></a>COM 구성 요소 격리

1. **솔루션 탐색기**를 **참조** 노드를 선택 합니다 **VB6Hello** 참조 합니다.

2. 에 **속성** 창의 값을 변경 합니다 **격리** 속성을 **False** 에 **True**.

3. **빌드할** 메뉴에서 클릭 **솔루션 빌드**합니다.

   이제 f5 키를 예상 대로 응용 프로그램 작동 하지만 경우 등록-COM에서 이제 실행 중인 이 증명 하기 위해 고 VB6Hello.dll 구성 요소를 등록 취소를 RegFreeComDemo1.exe Visual Studio IDE 외부에서 실행 합니다. 이 이번에는 단추를 클릭할 때 계속 작동 합니다. 응용 프로그램 매니페스트를 일시적으로 바꾸면 다시 못합니다.

> [!NOTE]
> COM 구성 요소가 없는 경우 일시적으로 등록을 취소 하 여 시뮬레이션할 수 있습니다. 명령 프롬프트를 열고를 입력 하 여 시스템 폴더를 이동할 `cd /d %windir%\system32`를 입력 하 여 다음 구성 요소 등록을 취소 `regsvr32 /u VB6Hello.dll`합니다. 입력 하 여 다시 등록 하는 수 `regsvr32 VB6Hello.dll`입니다.

 마지막 단계를 사용 하 여 응용 프로그램 게시를 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]:

##### <a name="to-publish-an-application-update-with-an-isolated-com-component"></a>격리 된 COM 구성 요소를 사용 하 여 응용 프로그램 업데이트를 게시 하려면

1. **빌드** 메뉴에서 클릭 **RegFreeComDemo 게시**합니다.

    게시 마법사가 나타납니다.

2. 게시 마법사에서 로컬 컴퓨터의 디스크에 액세스 하 고 게시 된 파일을 검사할 수 있는 위치를 지정 합니다.

3. **마침**을 클릭하여 애플리케이션을 게시합니다.

   게시 된 파일을 검사 하면 sysmon.ocx 파일이 포함 된 기록해둔 메시지가 표시 됩니다. 컨트롤이 최종 사용자의 컴퓨터를 다른 버전의 컨트롤을 사용 하 여 다른 응용 프로그램에 있으면이 응용 프로그램을 사용 하 여 방해 없습니다 것 이므로이 응용 프로그램에 완전히 격리 됩니다.

## <a name="reference-native-assemblies"></a>네이티브 어셈블리 참조
 Visual Studio는 네이티브 Visual Basic 6.0에 대 한 참조를 지원 또는 C++ 어셈블리 이러한 참조를 네이티브 참조 라고 합니다. 참조를 확인 하 여 네이티브 인지 여부를 확인할 수 있습니다 해당 **파일 형식** 속성이 **네이티브** 또는 **ActiveX**합니다.

 네이티브 참조를 추가 하려면 사용 합니다 **참조 추가** 명령을 사용한 다음, 매니페스트를 찾습니다. 일부 구성 요소 DLL에 매니페스트를 배치합니다. 이 경우 자체 DLL을 선택 하기만 하면 및 Visual Studio는 참조로 추가 네이티브 구성 요소에 포함된 된 매니페스트를 검색 하는 경우. Visual Studio는 모든 종속 파일 또는 참조 된 구성 요소와 동일한 폴더에 있는 경우 매니페스트에 나열 된 어셈블리에도 자동으로 포함 됩니다.

 COM 제어 격리를 사용 하면 매니페스트를 이미 있지 않은 COM 구성 요소를 배포 하기 쉽습니다. 그러나 구성 요소 매니페스트를 사용 하 여 제공 되 면, 매니페스트를 직접 참조할 수 있습니다. 실제로 사용 하는 대신 가능한 구성 요소의 작성자가 제공 하는 매니페스트 항상 사용 해야 합니다 **격리** 속성입니다.

## <a name="limitations-of-registration-free-com-component-deployment"></a>등록이 필요 없는 COM 구성 요소 배포의 제한 사항
 등록이 필요 없는 COM 기존의 배포 기술에 비해 명확한 이점을 제공합니다. 그러나 지적도 해야 하는 제한 사항에 몇 가지 제한이 있습니다. 가장 큰 제한은 작동 한다는 것만 Windows XP 이상. 등록이 필요 없는 COM 구현의 핵심 운영 체제에서 구성 요소는 로드 하는 방식 변경 해야 합니다. 아쉽게도 계층이 없습니다 하위 수준 지원 등록이 필요 없는 com

 모든 구성 요소 등록이 필요 없는 com 적합 한 후보는 다음 중 하나라도 해당 하는 경우 구성 요소는 적합 하지 않습니다.

- 구성 요소는-out-of-process 서버입니다. EXE 서버가 지원 되지 않습니다. Dll만 지원 됩니다.

- 구성 요소가 운영 체제의 일부인 또는 XML, Internet Explorer 또는 Microsoft Data Access Components (MDAC)와 같은 시스템 구성 요소입니다. 구성 요소 작성자; 재배포 정책을 따라야 합니다. 공급 업체에 문의 하세요.

- 구성 요소에는 Microsoft Office와 같은 응용 프로그램의 일부입니다. Microsoft Excel 개체 모델을 격리 하지 않아야 예를 들어 있습니다. Office의 일부 이며만 사용할 수는 컴퓨터에 설치 된 전체 Office 제품을 사용 하 여 합니다.

- 구성 요소 추가 또는 스냅인에서 예를 들어 Office 추가 기능에서 또는 웹 브라우저 컨트롤을 사용 하 여 위한 것입니다. 이러한 구성 요소에는 일반적으로 일종의 매니페스트 자체의 범위를 벗어납니다는 호스팅 환경으로 정의 된 등록 구성표 필요 합니다.

- 구성 요소에는 장치 드라이버를 인쇄 스풀러를 예를 들어 시스템의 실제 또는 가상 장치를 관리합니다.

- 구성 요소는 재배포 가능 패키지는 데이터 액세스 합니다. 데이터 응용 프로그램 일반적으로 별도 데이터에 액세스 해야 재배포 가능 패키지를 실행 하기 전에 설치 해야 합니다. Microsoft ADO 데이터 컨트롤, Microsoft OLE DB 또는 Microsoft Data Access Components (MDAC)와 같은 구성 요소를 격리 하지 않아야 합니다. 대신, 응용 프로그램에서 MDAC 또는 SQL Server Express를 사용 하는 경우 설정 해야 해당 필수 구성 요소와 참조 [방법: ClickOnce 응용 프로그램을 사용 하 여 필수 구성 요소 설치](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md)합니다.

  경우에 따라 개발자는 구성 요소의 등록이 필요 없는 com 다시 디자인할 수 있습니다. 없는 경우 수 계속 빌드하고에 의존 하는 부트스트래퍼를 사용 하 여 표준 등록 체계를 통해 응용 프로그램을 게시 합니다. 자세한 내용은 [부트스트래퍼 패키지 만들기](../deployment/creating-bootstrapper-packages.md)합니다.

  COM 구성 요소는 응용 프로그램당 한 번 격리 수만 있습니다. 예를 들어, 서로 다른 두에서 동일한 COM 구성 요소를 격리할 수 없습니다 **클래스 라이브러리** 동일 응용 프로그램의 일부인 프로젝트입니다. 그렇게 하면 빌드 경고, 및 응용 프로그램 런타임 시 로드 되지 것입니다. 이 문제를 방지 하기 위해 단일 클래스 라이브러리에 COM 구성 요소를 캡슐화 하는 것이 좋습니다.

  일부의 시나리오는 com에서 등록 개발자의 컴퓨터에 필요 하지만 응용 프로그램의 배포 등록이 필요 하지 않습니다. `Isolated` 속성 자동으로 생성 된 매니페스트를 빌드하는 동안 COM 구성 요소 개발자의 컴퓨터에 등록 해야 해야 합니다. 빌드 중 자동 등록을 호출 하는 등록 캡처 기능이 없으며 있습니다. 또한 형식 라이브러리에 명시적으로 정의 된 모든 클래스 매니페스트에서 반영 되지 않습니다. 네이티브 참조와 같은 기존 매니페스트를 사용 하 여 COM 구성 요소를 사용 하는 경우에 구성 요소를 개발 시에 등록 하지 해야 합니다. 그러나 등록은 구성 요소는 ActiveX 컨트롤에 포함 하려는 경우 필요 합니다 **도구 상자** 및 Windows Forms 디자이너입니다.

## <a name="see-also"></a>참고자료
- [ClickOnce 보안 및 배포](../deployment/clickonce-security-and-deployment.md)