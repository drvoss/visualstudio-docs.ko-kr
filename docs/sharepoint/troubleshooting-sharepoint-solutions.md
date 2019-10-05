---
title: SharePoint 솔루션 문제 해결 | Microsoft Docs
ms.date: 02/22/2017
ms.topic: conceptual
f1_keywords:
- Microsoft.VisualStudio.Tools.SharePoint.Errors.Debugging
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, troubleshooting
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: bab7f45824def7a4b5a385381a4789b7adc276d0
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63008089"
---
# <a name="troubleshoot-sharepoint-solutions"></a>SharePoint 솔루션 문제 해결
  다음 문제 또는 경고를 사용 하 여 SharePoint 솔루션을 디버깅할 때 발생할 수 있습니다는 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 디버거. 자세한 내용은 [SharePoint 2007 워크플로 솔루션 디버깅](https://msdn.microsoft.com/3a5392f3-66f3-48be-956e-02de23fa6247)합니다.

## <a name="token-restrictions-in-sandboxed-visual-web-parts"></a>샌드박스 비주얼 웹 파트의 토큰 제한 사항
 샌드박스 솔루션의 비주얼 웹 파트는 SharePoint 런타임이 지원하는 $SPUrl과 같은 표준 토큰을 처리할 수 없습니다. 이에 따라 URL은 확인되지 않으며, 다음 예제와 같이 스크립트 요소에서 URL을 직접 참조하는 경우 비주얼 웹 파트 디자이너의 디자인 뷰에서 내용을 미리 볼 수 없습니다.

```xml
<script src="<% $SPUrl:~site/SiteAssets/ListOperations.js %>"></script>
```

 이 제한 사항을 해결하고 토큰을 확인하려면 리터럴을 사용하여 URL을 참조하십시오.

```xml
<asp:literal ID="Literal1" runat="server" Text="<script src='" />
<asp:literal ID="Literal2" runat="server" Text="<% $SPUrl:~site/SiteAssets/ListOperations.js %>" />
<asp:literal ID="Literal3" runat="server" Text="' type='text/javascript' ></script>" />
```

## <a name="character-restrictions-in-names-of-projects-and-project-items"></a>프로젝트 및 프로젝트 항목 이름의 문자 제한
 프로젝트와 프로젝트 항목의 이름에는 SharePoint 2010의 배포 경로에서 유효한 문자만 포함될 수 있습니다. 다른 문자가 허용 됩니다.

### <a name="error-message"></a>오류 메시지
 "잘못 된 문자" 오류 메시지입니다.

### <a name="resolution"></a>해결
 SharePoint 프로젝트 및 프로젝트 항목 이름의 경우 다음 문자만 사용합니다.

- 영숫자 ASCII 문자

- 공백

- 마침표 (입니다.)

- 쉼표 ()

- 밑줄 (_)

- 대시 (-)

- 백슬래시(\\)

  프로젝트가 패키지될 때 유효성 검사 규칙은 배포 중인 각 파일의 배포 경로 속성에 이러한 유효한 문자만 포함되어 있는지 확인합니다.

## <a name="errors-when-creating-custom-fields"></a>사용자 지정 필드를 만들 때 오류 발생
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]에서 사용자 지정 필드는 XML로 정의됩니다. 필드가 정의되어 있지 않거나 특정 형식을 사용하여 참조되는 경우 오류가 발생할 수 있습니다.

### <a name="error-message"></a>오류 메시지
 "잘못 된 문자" 패키징 시 오류 메시지입니다.

### <a name="resolution"></a>해결
 필드 정의의 ID는 다음 예제와 같이 중괄호로 묶은 GUID여야 합니다.

```xml
<Field ID="{5744d18c-305e-4632-8bd1-09d134f4830d}"
    Type="Note"
    Name="PatientName"
    DisplayName="Patient Name"
    Group="A Custom Group">
</Field>.
```

 다음 예제와 같이 콘텐츠 형식의 필드 참조를 빈 요소 형식을 사용 하 여 정의 해야 합니다 (\<FieldRef / >)를 시작/끝 요소를 사용 하 여 (\<FieldRef >\</FieldRef >):

```xml
<FieldRef ID="{5744d18c-305e-4632-8bd1-09d134f4830d}"
    Name="PatientName"
    DisplayName="Patient Name"
    Required="TRUE"/>
```

 필드의 소스 XML에 잘못된 형식이나 유효하지 않은 XML 파일과 같은 문제가 있는 경우 "파일을 구문 분석할 수 없음" 오류가 발생합니다.

## <a name="new-non-english-site-definitions-do-not-appear-in-site-creation-page-after-deployment"></a>배포 후 영어가 아닌 사이트 정의 새 사이트 만들기 페이지에 표시 되지 않습니다.
 만들고 영어가 아닌 버전을 사용 하 여 사이트 정의 배포 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] (로캘로 버전, 즉 [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)] 1033 이외의), **SharePoint 사용자 지정** 탭 는나타나지않습니다**서식 파일 선택** 상자와 새 사이트 템플릿이 나타나지 않습니다는 **새 SharePoint 사이트** 페이지입니다.

### <a name="error-message"></a>오류 메시지
 없음

### <a name="resolution"></a>해결
 에 잘못 된 값으로 인해이 문제가 발생 합니다 **경로** webtemp 사이트 정의 구성에 대 한 속성 파일을 같은 *webtemp_SiteDefinitionProject1.xml*합니다. 에 **경로** 아래에 있는 webtemp 파일의 속성을 **배포 위치**, 1033 적절 한 로캘을 변경 [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)]. 예를 들어, 사용 하려면 일본어 로캘을 변경 값 1041 하 합니다. 자세한 내용은 참조 [Microsoft에 의해 할당되는 로캘 ID](http://go.microsoft.com/fwlink/?LinkID=165561)를 참조하세요.

## <a name="error-appears-when-a-workflow-project-is-deployed-on-a-clean-system"></a>클린 시스템에는 워크플로 프로젝트를 배포할 때 오류가 표시 됩니다.
 이 문제는 클린 시스템의 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]에서 워크플로 프로젝트를 배포하는 경우 발생합니다. 클린 시스템은 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 및 SharePoint를 새로 설치했지만 워크플로 프로젝트를 배포하지 않은 컴퓨터입니다.

### <a name="error-message"></a>오류 메시지
 SharePoint 목록을 찾을 수 없습니다. 워크플로 기록 합니다.

### <a name="resolution"></a>해결
 누락 된 워크플로 기록 목록으로 인해이 오류가 발생합니다. 개발 환경을 클린 시스템 이기 때문에 워크플로가 배포 되지 및 워크플로 기록 목록 아직 존재 하지 않습니다. 이 문제를 해결 하려면를 사용 하면 만들려는 워크플로 기록 목록 워크플로 마법사에 다시 엽니다.

##### <a name="to-reenter-the-workflow-wizard"></a>워크플로 마법사를 다시 입력

1. **솔루션 탐색기**에서 워크플로 노드를 선택 합니다.

2. 에 **속성** 창의 줄임표 단추가 있는 임의의 속성에서 줄임표 (...) 단추를 선택 합니다.

## <a name="user-must-refresh-application-page-in-browser-while-debugging-to-view-updated-image"></a>사용자는 브라우저에서 응용 프로그램 페이지를 새로 고침 해야 업데이트 된 이미지를 보려면 디버그 하는 동안
 와 같은 이미지를 표시 하는 컨트롤을 사용 하 여 응용 프로그램 페이지를 포함 하는 SharePoint 솔루션 디버깅 하는 경우는 [!INCLUDE[TLA2#tla_html](../sharepoint/includes/tla2sharptla-html-md.md)] 이미지 컨트롤을 이미지에 대 한 모든 변경 사항을 표시 하려면 브라우저에서 페이지를 새로 고침 해야 합니다.

## <a name="error-the-site-location-is-not-valid"></a>오류: 사이트 위치가 올바르지 않습니다.
 이 문제가 발생할 수 있습니다 [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)] 설치 되어 있지 않습니다. 에 지정 된 SharePoint 웹 사이트에 대 한 관리자 권한이 없습니다 경우에 발생할 수 있습니다 하는 **SharePoint 사용자 지정 마법사**합니다.

### <a name="error-message"></a>오류 메시지

- SharePoint 사이트 위치가 올바르지 않습니다.

### <a name="resolution"></a>해결

- [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)]을 설치합니다.

- SharePoint 웹 사이트에 관리자 액세스할 수 있는지 확인 합니다. 자세한 내용은 참조는 [!INCLUDE[TLA2#tla_office](../sharepoint/includes/tla2sharptla-office-md.md)] 온라인 문서 [할당 하거나 SharePoint Server의 서비스 응용 프로그램의 관리자가 제거](https://docs.microsoft.com/sharepoint/administration/assign-or-remove-administrators-of-service-applications)합니다.

## <a name="site-deletion-web-event-does-not-occur-in-event-receiver-project"></a>이벤트 수신기가 프로젝트의 사이트 삭제 웹 이벤트가 발생 하지 않습니다.
 이벤트 수신기 프로젝트를 만들고 "사이트 삭제 되 고"와 같은 특정 웹 이벤트를 선택 하면 이벤트가 발생 하지 않습니다.

### <a name="error-message"></a>오류 메시지
 없음

### <a name="resolution"></a>해결
 이 문제는 기능 범위가 사이트 수준 이벤트를 처리 하는 "사이트" 해야 합니다. 하지만 이벤트 수신기가 프로젝트에 대 한 기본 기능 범위는 "Web" 때문에 발생 합니다. 영향을 받는 웹 이벤트 다음과 같습니다.

- 사이트를 삭제 (WebDeleting)

- 사이트 삭제 됨 (WebDeleted)

- 사이트를 이동 (WebMoving)

- 사이트 이동 됨 (WebMoved)

  이 문제를 해결 하려면 이벤트 수신기의 기능 범위를 다음과 같이 변경 합니다.

##### <a name="to-change-the-feature-scope-of-the-event-receiver"></a>이벤트 수신기의 기능 범위를 변경 하려면

1. **솔루션 탐색기**, 이벤트 수신기를 열고 *.feature* 파일을 **기능 디자이너** 파일을 두 번 클릭 하거나 바로 가기 메뉴를 열고 하 여 차례로 선택 **열려**합니다.

2. 옆의 화살표를 선택 **범위**를 선택한 후 **사이트** 나타나는 목록에서.

## <a name="deployment-error-appears-after-the-name-of-an-identifier-in-a-business-data-connectivity-model-project-is-changed"></a>비즈니스 데이터 연결 모델 프로젝트에 있는 식별자의 이름 변경 된 후 배포 오류가 나타남
 비즈니스 데이터 연결 (BDC) 모델의 엔터티 식별자 이름을 변경 하 고 솔루션을 배포 하려고 하는 경우이 문제가 발생 합니다.

### <a name="error-messages"></a>오류 메시지

- \<*모델 이름*>에 다음 외부 콘텐츠 형식 활성화 오류가 발생 했습니다...

- 이름의 IMetadataObject '\<*모델 이름*>'에 'name' 필드가 중복 된 값이 포함 하는 중...

### <a name="resolution"></a>해결
 이 문제를 해결 하려면 모델을 수동으로 삭제 하 고 솔루션을 다시 배포 합니다.  다음 도구 중 하나를 사용 하 여 모델을 삭제할 수 있습니다.

- SharePoint 2010 중앙 관리 합니다. 자세한 내용은 [BDC 모델 관리](http://go.microsoft.com/fwlink/?LinkID=181472) Microsoft TechNet 웹 사이트입니다.

- Windows PowerShell. 명령 프롬프트에서이 명령을 입력 하 여 모델을 삭제할 수 있습니다. **Remove-SPBusinessDataCatalogModel**. 자세한 내용은 [일반 cmdlet (SharePoint Server 2010)](http://go.microsoft.com/fwlink/?LinkID=182375) Microsoft TechNet 웹 사이트입니다.

## <a name="an-error-appears-when-you-try-to-view-a-visual-web-part-in-sharepoint"></a>Sharepoint에서 비주얼 웹 파트를 보려고 할 때 오류가 표시 됩니다.
 이 문제가 발생 하면를 **경로** 사용자 정의 컨트롤의 속성 문자열을 사용 하 여 시작 하지 않습니다 "CONTROLTEMPLATES\\" 합니다.

### <a name="error-messages"></a>오류 메시지

- 파일 ' /_CONTROLTEMPLATES/ *\<프로젝트 이름 >* / *\<웹 파트 이름 >* / *\<사용자 정의 컨트롤 이름 >* .ascx'가 없습니다.

- '/' 응용 프로그램에 서버 오류가 발생 했습니다.

### <a name="resolution"></a>해결

##### <a name="to-resolve-this-issue"></a>이 문제를 해결 하려면

1. **솔루션 탐색기**, 해당 파일 이름 확장명은 사용자 컨트롤 파일을 *.ascx*합니다.

2. 메뉴 모음에서 선택 **뷰** > **속성 창**합니다.

3. 에 **속성** 창에서 확장을 **배포 위치** 노드.

4. 값을 확인 합니다 **경로** 된 문자열로 시작 하는 속성 "CONTROLTEMPLATES\\"입니다.

## <a name="error-appears-when-an-imported-reusable-workflow-that-contains-a-task-form-field-is-run"></a>작업 양식 필드를 포함 하는 가져온된 재사용 가능한 워크플로 실행할 때 오류가 표시 됩니다.
 필드에 있는 태스크 폼을 포함 하는 워크플로 가져오고 다음 가져온 원본 동일한 시스템에서 새 워크플로 실행 하는 경우이 문제가 발생 합니다.

### <a name="error-message"></a>오류 메시지
 배포 단계 ' 활성화 기능 '에서 오류가 발생 했습니다. Id 사용 하 여 필드 [*Guid*] 기능에 정의 된 [*Guid*] 또는 하위 사이트에 현재 사이트 컬렉션에서 발견 되었습니다.

### <a name="resolution"></a>해결
 이 오류는 재사용 가능한 워크플로 가져오기 프로젝트 때문에 발생 하는 필드 ID 충돌 결과 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 작업 양식 필드 Id를 변경 하지 않습니다. 원래 워크플로 포함 하는 동일한 서버에서 가져온된 워크플로 배포 하는 경우에 필드 ID 충돌이 발생 합니다.

 이 문제를 해결 하려면 모든 가져온된 워크플로 파일에 필드 ID 특성의 값을 변경 하려면 찾기 및 바꾸기 기능을 사용 합니다.

## <a name="error-appears-when-a-renamed-imported-list-instance-is-run"></a>오류 표시 되는 이름이 바뀐 가져올 때 목록 인스턴스가 실행 될
 가져온된 목록 인스턴스에 이름을 바꾼 후에서 실행 하는 경우이 문제가 발생 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]합니다.

### <a name="error-message"></a>오류 메시지
 빌드 오류: 배포 단계 ' 활성화 기능 '에서 오류가 발생 했습니다. 파일 Template\Features\\[*프로젝트를 가져와서*<em>기능</em>*이름*] \Files\Lists\\[*이전* <em>목록 이름</em>] \Schema.xml 존재 하지 않습니다.

### <a name="resolution"></a>해결
 목록 인스턴스를 가져올 때 CustomSchema 이라는 특성 목록 인스턴스의 Elements.xml 파일에 추가 됩니다. Elements.xml 목록 인스턴스에 대 한 사용자 지정 schema.xml의 경로 포함 합니다. 목록 인스턴스 이름을 바꾸면 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], 사용자 지정 schema.xml에 대 한 배포 경로 변경 하지만 CustomSchema 특성의 경로 값이 업데이트 되지 않습니다. 결과적으로 목록 인스턴스를 찾을 수 없습니다는 *schema.xml* 기능이 활성화 되 면 CustomSchema 특성으로 지정 된 이전 경로에 파일입니다.

 이 문제를 해결 하려면 배포 위치의 경로 업데이트 합니다 *schema.xml* CustomSchema 특성에는 파일입니다.

## <a name="sharepoint-debugging-session-terminated-by-iis"></a>IIS에서를 종료 하는 세션을 디버깅 하는 SharePoint
 에 중단점을 설정 하는 경우이 문제가 발생을 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint 솔루션을 선택 합니다 **F5** 실행 한 다음 90 초 넘게 중단점에 머무르는 키.

### <a name="error-message"></a>오류 메시지
 웹 서버 프로세스를 디버깅 하 고 있는 인터넷 정보 서비스 (IIS)에서 종료 되었습니다. IIS에서 애플리케이션 풀 ping 설정을 구성하여 이 문제를 방지할 수 있습니다. 참조 추가 세부 정보에 대 한 도움말입니다.

### <a name="resolution"></a>해결
 기본적으로 IIS 응용 프로그램 풀에는 응용 프로그램 닫기 전에 응답 응용 프로그램에 대 한 90 초 동안 기다립니다. 이 프로세스는 응용 프로그램을 "ping" 이라고 합니다. 이 문제를 해결 하려면 대기 시간을 늘리려면 또는 ping을 완전히 응용 프로그램을 사용 하지 않도록 설정 합니다.

##### <a name="to-access-the-iis-app-pool-settings"></a>IIS 앱 풀 설정에 액세스 하려면

1. IIS 관리자를 엽니다.

2. 에 **연결** 창, SharePoint 서버 노드를 확장 한 다음 선택 합니다 **응용 프로그램 풀** 노드.

3. 에 **응용 프로그램 풀** 페이지에서 SharePoint 응용 프로그램 풀 (대개 "SharePoint-80")를 선택를 선택한 후를 **작업** 창 선택 합니다 **고급 설정** 링크입니다.

4. IIS 시간 제한 전에 대기 시간을 늘리려면 값을 변경 **Ping 최대 응답 시간 (초)** 90 초 보다 큰 값으로.

5. Ping을 실행 하는 IIS를 사용 하지 않으려면 설정할 **Ping 사용** 하 **False**합니다.

## <a name="auto-retract-leaves-orphaned-list-instance-in-sharepoint"></a>SharePoint에서 분리 된 목록 인스턴스를 떠날 자동 취소
 다음 단계를 수행 하는 경우이 문제가 발생 합니다.

1. 있는 목록 인스턴스와 목록 정의 만들기 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]합니다.

2. 선택 된 **F5** 키를 눌러 솔루션을 실행 합니다.

3. 디버깅을 중지 하거나 SharePoint 사이트를 닫습니다.

4. SharePoint 사이트를 다시 열 및 목록 인스턴스를 엽니다.

### <a name="error-message"></a>오류 메시지
 '/' 응용 프로그램에 서버 오류가 발생 했습니다.

### <a name="resolution"></a>해결
 SharePoint 솔루션의 디버그 세션을 닫은 후 하기 때문에 발생 하는이 자동 취소 기능 솔루션을 제거 합니다. 취소는 SharePoint에서 목록 정의 삭제 하지만 list의 인스턴스를 삭제 하지 않습니다. 기본 목록 정의 목록 인스턴스가 필요 합니다.

 이 문제를 해결 하려면 메뉴 모음에서 솔루션을 배포 **빌드합니다** > **배포**합니다. (선택 하 여 솔루션을 디버그 하지 합니다 **F5** 키입니다.) 그런 다음 SharePoint에서 목록 인스턴스를 삭제 합니다.

## <a name="original-sharepoint-solution-is-replaced-by-an-exported-version"></a>원래 SharePoint 솔루션 내보낸된 버전으로 바뀝니다.
 SharePoint 솔루션을 내보내면 솔루션을 가져올 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], 다음에 배포 하는 솔루션 내보낸 된 동일한 사이트에 다시 원래 SharePoint 솔루션을 대체 됩니다. 원래 솔루션에 활성화 되지 않은 서버에 솔루션을 배포 하는 경우에이 문제가 발생 하지 않습니다.

### <a name="error-message"></a>오류 메시지
 없음

### <a name="resolution"></a>해결
 내보낸 된 사이트에서 솔루션을 덮어쓰지 않으려면,는 solutionid 특성이 있으며,의 Guid 및 가져온된의 모든 기능에 대 한 기능 Id를 변경 합니다 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 프로젝트입니다.

## <a name="error-appears-when-debugging-starts"></a>디버깅을 시작할 때 오류가 나타남
 Visual Studio에서 SharePoint 솔루션의 디버깅을 시작할 때 지정한 키가 사전에 없기 때문에 Visual Studio에서 Web.config 파일을 로드할 수 없다는 오류가 발생합니다.

### <a name="error-message"></a>오류 메시지
 Web.config 구성 파일을 로드 하지 못했습니다. 잘못 된 형식의 XML 요소에 대 한 파일을 확인 하 고 다시 시도 합니다. 다음 오류가 발생했습니다. 지정 된 키가 사전에 없는 합니다.

### <a name="resolution"></a>해결
 이 문제를 해결하려면 Visual Studio에서 SharePoint 프로젝트의 사이트 URL 속성 값이 웹 애플리케이션의 대체 액세스 매핑에 대한 기본 영역에 할당된 URL과 일치하는지 확인합니다. 인트라넷 등의 다른 영역을 URL에 사용하여 오류를 해결할 수 없습니다. 프로젝트의 사이트 URL과 기본 영역의 URL은 일치해야 합니다. 대체 액세스 매핑에 액세스 하려면 SharePoint 2010 중앙 관리 유틸리티를 열어를 선택 합니다 **응용 프로그램 관리** 링크를 차례로 **웹 응용 프로그램**, 선택는  **대체 액세스 매핑 구성** 링크 합니다. 자세한 내용은 [웹 응용 프로그램에 대 한 영역을 만들](http://go.microsoft.com/fwlink/?LinkId=192274)합니다.

## <a name="see-also"></a>참고자료

- [SharePoint 패키징 및 배포 문제 해결](../sharepoint/troubleshooting-sharepoint-packaging-and-deployment.md)
- [SharePoint 솔루션 빌드 및 디버그](../sharepoint/building-and-debugging-sharepoint-solutions.md)
- [Visual Studio의 디버깅](../debugger/debugging-in-visual-studio.md)