---
title: SharePoint 솔루션 디버깅 | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.Project.WebConfigModificationDialog
- VS.SharePointTools.Project.DebuggingNotEnabled
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, debugging
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 60aa38d5042625393132ffceb3cc226f44e67645
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63443493"
---
# <a name="debug-sharepoint-solutions"></a>SharePoint 솔루션 디버깅
  사용 하 여 SharePoint 솔루션을 디버깅할 수는 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 디버거. 디버깅을 시작할 때 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint 서버에 프로젝트 파일을 배포 하 고 다음 웹 브라우저에서 SharePoint 사이트의 인스턴스를 엽니다. 다음 섹션에서는 SharePoint 응용 프로그램에 디버그 하는 방법에 설명 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]합니다.

- [디버깅 사용](#enable-debugging)

- [F5 디버깅 및 배포 프로세스](#f5-debug-and-deployment-process)

- [SharePoint 프로젝트 기능이](#sharepoint-project-features)

- [워크플로 디버깅](#debug-workflows)

- [기능 이벤트 수신기를 디버그 합니다.](#debug-feature-event-receivers)

- [Ehanced 디버깅 정보를 사용 하도록 설정](#enable-enhanced-debugging-information)

## <a name="enable-debugging"></a>디버깅 사용
 먼저 SharePoint 솔루션에 디버그할 때 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], 대화 상자를 알려 줍니다 web.config 파일에 디버깅을 사용 하도록 하지 않습니다. (Web.config 파일을 SharePoint 서버를 설치할 때 생성 됩니다. 자세한 내용은 [Web.config 파일을 사용 하 여 작업](http://go.microsoft.com/fwlink/?LinkID=149266).) 대화 상자는 디버깅을 사용 하려면 디버깅 하거나 web.config 파일을 수정 하지 않고 프로젝트를 실행 하는의 옵션을 제공 합니다. 첫 번째 옵션을 선택하면 프로젝트가 정상적으로 실행됩니다. 두 번째 옵션을 선택하면 web.config 파일이 다음과 같이 구성됩니다.

- 호출 스택에 있는 설정 (`CallStack="true"`)

- 사용자 지정 오류가 비활성화 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] (`<customErrors mode="Off" />`)

- 컴파일 디버깅 사용 (`<compilation debug="true">`)

  결과 web.config 파일을 따릅니다.

```xml
<?xml version="1.0" encoding="UTF-8" standalone="yes"?>
    <configuration>
        ...
        <SharePoint>
            <SafeMode MaxControls="200"
                CallStack="true"
                DirectFileDependencies="10"
                TotalFileDependencies="50"
                AllowPageLevelTrace="false">
                ...
            </SafeMode>
        ...
        </SharePoint>
        <system.web>
            ...
            <customErrors mode="Off" />
            ...
            <compilation debug="true">
            ...
            </compilation>
            ...
        </system.web>
        ...
    </configuration>
```

 변경을 디버깅을 사용 하지 않도록 설정 하려면 다음을 변경할 [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] web.config 파일에서:

- 호출 스택 해제 (`CallStack="false"`)

- 사용자 지정 오류를 활성화 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] (`<customErrors mode="On" />`)

- 컴파일 디버깅 사용 안 함 (`<compilation debug="false">`)

## <a name="f5-debug-and-deployment-process"></a>F5 디버깅 및 배포 프로세스
 디버그 모드에서 SharePoint 프로젝트를 실행 하는 경우 SharePoint 배포 프로세스는 다음 작업을 수행 합니다.

1. 사용자 지정 가능한 배포 전 명령을 실행합니다.

2. 사용 하 여 웹 솔루션 패키지 (.wsp) 파일을 만듭니다 [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] 명령입니다. .Wsp 파일에 모든 필요한 파일 및 기능이 포함 됩니다. 자세한 내용은 [솔루션 개요](http://go.microsoft.com/fwlink/?LinkID=128154)합니다.

3. SharePoint 솔루션은 팜 솔루션 경우 재생 되는 [!INCLUDE[TLA2#tla_iis5](../sharepoint/includes/tla2sharptla-iis5-md.md)] 지정된 된 사이트에 대 한 응용 프로그램 풀 [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)]합니다. 이 단계에서 잠긴 파일을 해제 합니다 [!INCLUDE[TLA2#tla_iis5](../sharepoint/includes/tla2sharptla-iis5-md.md)] 작업자 프로세스입니다.

4. 패키지의 이전 버전이 이미 있는 경우 이전 버전의 기능 및.wsp 파일의 파일을 제거 합니다. 이 단계에서는 기능을 비활성화 솔루션 패키지를 제거한 후 SharePoint 서버에 솔루션 패키지를 삭제 합니다.

5. .Wsp 파일에서 기능 및 파일의 현재 버전을 설치합니다. 이 단계를 추가 하 고 SharePoint 서버에서 솔루션을 설치 합니다.

6. 워크플로의 경우 워크플로 어셈블리를 설치 합니다. 사용 하 여 해당 위치를 변경할 수는 *어셈블리 위치* 속성입니다.

7. 사이트 또는 웹 범위인 경우 SharePoint에서 프로젝트의 기능을 활성화 합니다. 팜 및 웹 응용 프로그램 범위에서 기능이 활성화 되지 않습니다.

8. 워크플로의 경우 SharePoint 라이브러리, 목록 또는에서 선택한 사이트를 사용 하 여 워크플로 연결 합니다 **SharePoint 사용자 지정 마법사**합니다.

   > [!NOTE]
   > 이 연결을 선택한 경우에 발생 **자동으로 연결 워크플로** 마법사에서.

9. 사용자 지정 가능한 배포 후 명령을 실행합니다.

10. 연결 된 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 디버거를 합니다 [!INCLUDE[sharepointShort](../sharepoint/includes/sharepointshort-md.md)] 프로세스 (*w3wp.exe*). 프로젝트 형식을 사용 하면 변경 하는 경우는 *샌드박스 솔루션* 속성 및 해당 값으로 설정 됩니다 **true**, 다른 프로세스에 디버거 연결 (*SPUCWorkerProcess.exe*). 자세한 내용은 [샌드박스 솔루션 고려 사항](../sharepoint/sandboxed-solution-considerations.md)합니다.

11. SharePoint 솔루션이 팜 솔루션 이라면 JavaScript 디버거를 시작 합니다.

12. 웹 브라우저에서 적절 한 라이브러리, 목록 또는 사이트 페이지를 표시합니다.

    [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 각 작업이 완료 된 후 출력 창에 상태 메시지를 표시 합니다. 작업을 완료할 수 없는 경우 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 오류 목록 창에서 오류 메시지를 표시 합니다.

## <a name="sharepoint-project-features"></a>SharePoint 프로젝트 기능이
 기능은 이식 가능한 모듈식 단위 사이트 정의 사용 하 여 사이트 수정을 간소화 하는 기능입니다. 패키지 이기도 [!INCLUDE[sharepointShort](../sharepoint/includes/sharepointshort-md.md)] 특정 범위에 대해 활성화 될 수 고 사용자가 특정 목표 또는 작업을 수행 하는 (WSS) 요소입니다. 템플릿 기능으로 배포 됩니다.

 디버그 모드에서 프로젝트를 실행할 때 배포 프로세스에 폴더를 만듭니다는 *기능* 에서 디렉터리 *%COMMONPROGRAMFILES%\Microsoft Shared\web server extensions\14\TEMPLATE\FEATURES*합니다. 기능 이름 형식이 *프로젝트 이름*_Feature*x*, testproject_feature1 합니다.

 기능 디렉터리에 솔루션 폴더를 포함 한 *정의 기능* 파일 및 *워크플로 정의* 파일입니다. 기능 정의 파일 (Feature.xml) 프로젝트의 하십시오 프로젝트 정의 파일에 있는 파일에 설명 합니다 (*Elements.xml*) 프로젝트 템플릿에 대해 설명 합니다. *Elements.xml* 에서 찾을 수 있습니다 **솔루션 탐색기**, 하지만 Feature.xml 솔루션 패키지를 만들 때 생성 됩니다. 이러한 파일에 대 한 자세한 내용은 참조 하세요. [SharePoint 프로젝트 및 프로젝트 항목 템플릿](../sharepoint/sharepoint-project-and-project-item-templates.md)합니다.

## <a name="debug-workflows"></a>워크플로 디버깅
 워크플로 프로젝트를 디버깅할 때 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 목록 또는 라이브러리 (해당 유형)에 따라 워크플로 템플릿을 추가 합니다. 그런 다음 수동으로 또는 추가 하거나 업데이트 하 여 항목 워크플로 서식 파일을 시작할 수 있습니다. 사용할 수 있습니다 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 워크플로 디버깅 합니다.

> [!NOTE]
> 다른 어셈블리에 대 한 참조를 추가 하는 경우 해당 어셈블리를 전역 어셈블리 캐시에 설치 되어 있는지 확인 하십시오 ( [!INCLUDE[TLA2#tla_gac](../sharepoint/includes/tla2sharptla-gac-md.md)]). 그렇지 않은 경우 워크플로 솔루션 실패 합니다. 어셈블리를 설치 하는 방법에 대 한 정보를 참조 하세요 [수동으로 문서 또는 항목에서 워크플로 시작](https://support.office.com/article/Manually-start-a-workflow-on-a-document-or-item-5C106E0E-6FF2-4A75-AF99-F01653BC7963)합니다.

 그러나 배포 프로세스는 워크플로 시작 하지 않습니다. SharePoint 웹 사이트에서 워크플로 시작 해야 합니다. 또한 Microsoft Office Word 2010 같은 클라이언트 응용 프로그램을 사용 하 여 또는 별도 서버 쪽 코드를 사용 하 여 워크플로 시작할 수 있습니다. 에 지정 된 방법 중 하나를 사용 합니다 **SharePoint 사용자 지정 마법사**합니다.

 예를 들어, 워크플로 수동으로 시작할 수 있습니다를 지정한 경우 라이브러리 또는 목록 항목에서 바로 워크플로 시작 합니다. 워크플로 수동으로 시작 하는 방법에 대 한 자세한 내용은 참조 하세요. [수동으로 문서 또는 항목에서 워크플로 시작](https://support.office.com/article/Manually-start-a-workflow-on-a-document-or-item-5C106E0E-6FF2-4A75-AF99-F01653BC7963)합니다.

## <a name="debug-feature-event-receivers"></a>기능 이벤트 수신기를 디버그 합니다.
 기본적으로 실행 하는 경우를 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint 응용 프로그램을 SharePoint 서버를 해당 기능은 자동으로 활성화. 그러나 되므로 문제가 발생 기능 이벤트 수신자를 디버깅할 때에서 기능을 활성화 하는 경우 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], 디버거에서 다른 프로세스에서 실행 됩니다. 즉, 중단점 등의 몇 가지 디버깅 기능을 제대로 작동 하지 않습니다.

 자동으로 SharePoint에서 기능 활성화를 사용 하지 않도록 설정 하 고 기능 이벤트 수신자의 적절 한 디버깅을 허용 하려면 프로젝트의 값을 설정 **활성 배포 구성을** 속성을 **활성화없음** 디버깅 하기 전에 합니다. 그런 다음 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]에서 SharePoint 애플리케이션의 디버깅을 시작한 후 SharePoint에서 수동으로 기능을 활성화합니다. 기능을 활성화 하려면 엽니다는 **사이트 작업** SharePoint에서 메뉴 **사이트 설정**를 선택 합니다 **사이트 기능 관리** 링크를 선택한 후의 **활성화** 계속 정상적으로 디버깅 하려면 기능 옆의 단추입니다.

## <a name="enable-enhanced-debugging-information"></a>향상 된 디버깅 정보를 사용 하도록 설정
 간의 복잡 한 상호 작용으로 인해 합니다 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 프로세스 (devenv.exe)는 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint 호스트 프로세스 (*vssphost4.exe*), SharePoint 및 WCF 계층에서 발생 하는 오류를 진단 하는 동안 빌드, 배포 및 등을 어려울 수 있습니다. 이러한 오류를 해결할 수 있도록, 향상 된 디버깅 정보를 사용할 수 있습니다. 이렇게 하려면 Windows 레지스트리에서 다음 레지스트리 키로 이동 합니다.

 **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\11.0\SharePointTools**

 하는 경우 "EnableDiagnostics" **REG_DWORD** 값은 아직 존재, 수동으로 만들어야 합니다. "EnableDiagnostics" 값 "1."로 설정

 에 표시할 정보를 추적 1 원인 스택에이 키 값을 설정 합니다 **출력** 창에서 실행 하는 동안 프로젝트 시스템 오류가 발생할 때마다 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]합니다. 고급 디버깅 정보를 사용하지 않도록 설정하려면 EnableDiagnostics를 다시 0으로 설정하거나 이 값을 삭제합니다.

 다른 SharePoint 레지스트리 키에 대 한 자세한 내용은 참조 하세요. [Visual Studio에서 SharePoint 도구의 확장을 디버그](../sharepoint/debugging-extensions-for-the-sharepoint-tools-in-visual-studio.md)합니다.

## <a name="see-also"></a>참고자료
- [SharePoint 솔루션 문제 해결](../sharepoint/troubleshooting-sharepoint-solutions.md)
