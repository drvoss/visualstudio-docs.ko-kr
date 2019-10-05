---
title: SharePoint 솔루션 지역화 | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.Project.GlobalAndFeatureResource
- VS.SharePoint.Project.AddResourceDialog
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- globalizing [SharePoint development in Visual Studio]
- localizing [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, localizing
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 90da60cb904ba6e3db2be3805256fcf4eb9122ee
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63444355"
---
# <a name="localize-sharepoint-solutions"></a>SharePoint 솔루션 지역화

  전 세계적으로 사용할 수 있도록 응용 프로그램을 준비 하는 프로세스를 지역화 라고 합니다. 지역화 리소스를 특정 문화권으로 변환 됩니다. 자세한 내용은 [Globalizing and Localizing Applications](../ide/globalizing-and-localizing-applications.md)합니다. 이 항목에서는 SharePoint 솔루션을 지역화 하는 방법에 대 한 개요를 제공 합니다.

 솔루션을 지역화 하려면 코드에서 하드 코드 된 문자열을 제거 하 고 리소스 파일에 추상화 합니다. 리소스 파일은는 [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)]-파일 기반을 *.resx* 확장 합니다. 리소스 파일에는 솔루션에서 사용 되는 문자열의 번역된 된 버전이 포함 되어 있습니다. 자세한 내용은 [응용 프로그램의 리소스](http://go.microsoft.com/fwlink/?LinkID=155844)합니다.

> [!NOTE]
> SharePoint 솔루션 리소스 파일에 문자열 리소스만 추가 합니다. 리소스 편집기를 사용 하면 문자열이 아닌 리소스를 추가할 수 있습니다, 있지만 문자열이 아닌 리소스는 SharePoint에 배포 하지 않습니다.

## <a name="resource-files"></a>리소스 파일
 리소스 파일의 세 가지 종류가 있습니다: 기본적으로 언어 중립적인 및 언어별 합니다.

|리소스 파일 형식|설명|
|------------------------|-----------------|
|기본|라고도 대체 (fallback) 리소스에 기본 리소스 파일 영어와 같은 기본 문화권에 대 한 지역화 된 문자열을 포함 합니다. 지정된 된 언어에 대 한 지역화 된 리소스 파일을 찾을 수 있는 경우 사용 됩니다. 기본 리소스에 별도 파일이 없는, 기본 응용 프로그램 어셈블리에 저장 됩니다.|
|언어 중립|특정 문화권이 아니라 언어에 지역화 된 문자열을 포함 하는 리소스 파일입니다. 예를 들어 프랑스어 "fr"입니다.|
|언어별|언어 및 문화권에 대 한 지역화 된 문자열을 포함 하는 리소스 파일입니다. 예를 들어에 "FR-CA" 프랑스어 (캐나다)입니다.|

 자세한 내용은 [리소스 지역화를 위한의 계층적 구성](http://go.microsoft.com/fwlink/?LinkId=178360)합니다.

 개발 하는 SharePoint 프로젝트에 기본 리소스 파일을 지정 하려면 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], 선택 **고정 언어 (고정 국가)** 문화권 목록에는 **리소스 추가** 대화 상자 있습니다 리소스 파일을 추가 합니다.

## <a name="localize-visual-studio-sharepoint-solutions"></a>Visual Studio SharePoint 솔루션 지역화
 솔루션을 지역화 하는 경우 솔루션이 사용자에 게 표시 하는 텍스트 정보를 모두 고려해 야 합니다. 정보 메시지, 오류 메시지 및 [!INCLUDE[TLA2#tla_ui](../sharepoint/includes/tla2sharptla-ui-md.md)] 문자열 변환 해야 하 고 이러한 번역을 리소스 파일에 포함 합니다.

 리소스 파일에서 모든 문자열에는 고유 식별자입니다. 각 리소스 파일의 번역된 된 문자열에 동일한 식별자를 사용 합니다. 예를 들어, "문자열 1"이 기본 리소스 파일의 첫 번째 문자열에 대 한 식별자 인 경우 언어별 리소스 파일의 첫 번째 문자열에 동일한 식별자를 사용 합니다.

 다음 세 가지 영역에서 일반적으로 지역화 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint 응용 프로그램: 기능, ASPX 페이지 태그 및 코드입니다. 이해 하기 쉽도록 다음 단원에서는 독일어와 일본어로 지역화 하려면 SharePoint 솔루션을 있다고 가정 합니다. 기본 언어는 영어입니다.

### <a name="localize-features"></a>기능 지역화
 기능을 지역화 하려면 하드 코드 된 제목 및 기능 설명의 번역 된 제목 및 문자열 지역화 된 리소스 파일에서 참조 하는 식으로 대체 해야 합니다. 이 변경에 **기능 디자이너** 에서 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]합니다. 자세한 내용은 [방법: 기능 지역화](../sharepoint/how-to-localize-a-feature.md)합니다.

 세 개의 리소스 파일 프로젝트 항목이 프로젝트에 추가 하면 영어 기능을 독일어와 일본어로 지역화 하려면: 영어, 독일어 및 일본어입니다. ASPX 태그 또는 코드를 지역화 하려면 기능 리소스 파일을 사용할 수 없습니다. 별도 리소스 파일이 필요 합니다.

 기능 리소스 파일을 만든 후에 번역 된 문자열을 추가 합니다. 다음 형식의 식 사용 하 여 지역화 된 문자열을 액세스 합니다.

```aspx-csharp
$Resources:String ID
```

 기능 리소스의 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 항상 리소스 라고 합니다. 고정 언어, 문화권 이외의 다른 언어를 선택 하는 경우 [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)] 리소스 파일 이름에 추가 됩니다. 예를 들어, invariant 언어 (기본값) 기능 리소스 파일을 추가 하는 경우 라고 *Resources.resx*합니다. 일본어 (일본) 문화권을 선택 하 여 언어별 기능 리소스를 추가 하는 경우 파일 이라고 *Resources.ja 됩니다*합니다. 기능 리소스 파일 이름은 자동으로 할당 됩니다 하 고 변경할 수 없습니다.

 기능 리소스의 범위에 추가 된 기능에 로컬입니다. 솔루션의 모든 기능 또는 요소 파일에서 사용할 수 있는 리소스를 만들려면 추가 된 **전역 리소스 파일** 기능 리소스 파일 대신 프로젝트 항목입니다. **전역 리소스 파일** 프로젝트 항목에는 **2010** 아래에 폴더 **SharePoint** 에 **새 항목 추가** 대화 상자. 전역 리소스 파일은 SharePoint 루트 폴더의 \Resources 폴더에 배포합니다.

### <a name="localize-aspx-page-markup"></a>ASPX 페이지 태그 지역화
 지역화할 [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] 페이지, 세 개의 리소스 파일 프로젝트 항목이 프로젝트에 추가할: 영어, 독일어 및 일본어입니다. 태그 외에 코드도 지역화 해야 하는 경우 대신 전역 리소스 파일을 추가할 수 있습니다.

 기본 언어 리소스 파일의 이름을 제공 합니다. 지역화 된 리소스 파일에 언어별 문화권 추가 된 동일한 이름을 제공 [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)]합니다. 예를 들어 *의 경우 MyAppResources.de-DE.resx* 독일어와 *일본어의 경우 됩니다* 일본어에 대 한 합니다.

 설정 된 **배포 유형** 각 리소스 파일의 속성 **AppGlobalResource**합니다. 이렇게 하면 리소스 파일은 솔루션의 모든 컨트롤과 ASPX 페이지에서 사용할 수 있는 App_GlobalResources 폴더에 배포 합니다. App_GlobalResources 폴더 C:\inetpub\wwwroot\wss\VirtualDirectories에 위치한\\< 포트 번호\>\App_GlobalResources 합니다.

> [!NOTE]
> 비 전역 리소스 파일을 사용 하는 경우 배포 형식 속성과 기타 SharePoint 관련 속성을 사용 하도록 설정 하려면 프로젝트 항목 폴더로 이동 합니다.

 ASPX 태그 리소스 파일은 코드를 지역화 하려면 데도 사용할 수 있습니다. 리소스 ASPX 태그 외에 코드도 지역화를 사용 하는 경우 빌드 작업 속성 설정을 그대로 각 파일의 리소스가 포함 된 리소스로 위성 어셈블리로 컴파일합니다. 그러나 리소스 파일을 사용 하 여 태그만 지역화 하는, 기본 응용 프로그램 어셈블리로 컴파일할에서 파일을 방지 하기 위해 콘텐츠 빌드 작업 필요에 따라 변경할 수 있습니다.

 다음 형식의 식을 사용 하 여 ASPX 페이지 및 컨트롤 태그에 이미 있는 모든 하드 코드 된 속성 문자열을 바꿉니다.

```aspx-csharp
<asp:<class> runat="server" Text="<%$Resources:<Resource File Name>, <String ID>%>" />
```

 예를 들어:

```aspx-csharp
<asp:Button ID="btn1" runat="server" onclick="btn1_Click" Text="<%$Resources:Resource1,String7%>"></asp:Button>
```

 텍스트인 ASPX 다음 형식의 식을 사용 합니다.

```aspx-csharp
<asp:literal ID="<ID>" runat="server" Text="<%$Resources:<Resource File Name>, <String ID>%>" />
```

 예를 들어:

```aspx-csharp
<asp:literal ID="Literal1" runat="server" Text="<%$Resources:Resource1, String9%>" />
```

 자세한 내용은 [방법: ASPX 태그 지역화](../sharepoint/how-to-localize-aspx-markup.md)합니다.

### <a name="localize-code"></a>코드 지역화
 기능 문자열을 지역화 하는 것 외에도 및 [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] 태그 해야 메시지 문자열 및 솔루션 코드에 표시 되는 오류 문자열을 지역화 합니다. 지역화 된 정보 및 오류 메시지는 위성 어셈블리에 포함 됩니다. 위성 어셈블리와 같은 사용자에 게 표시 되는 문자열을 포함할 [!INCLUDE[TLA2#tla_ui](../sharepoint/includes/tla2sharptla-ui-md.md)] 텍스트와 출력 메시지에 예외와 같은 합니다.

 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 표준.NET Framework 허브 및 스포크 모델을 사용합니다. 허브, 즉 주 프로그램 어셈블리에는 기본 언어 리소스가 포함 되어 있습니다. 스포크, 즉 위성 어셈블리 언어 관련 리소스를 포함 합니다. 자세한 내용은 [리소스 패키지 및 배포](http://go.microsoft.com/fwlink/?LinkId=179280)를 참조하세요. 리소스에서 위성 어셈블리는 컴파일됩니다 (*.resx*) 파일입니다. 언어별 리소스 파일을 프로젝트와 솔루션 패키지에 추가 하면 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 이라는 위성 어셈블리로 리소스 파일을 컴파일하고 *{프로젝트 이름}.resources.dll*합니다.

 ASPX 태그를 사용 하 여 별도 리소스 파일 프로젝트 항목을 프로젝트에 추가 하 여 SharePoint 응용 프로그램 코드를 지역화 하는 대로 기본 언어 및 각각에 대 한 언어 키를 누릅니다. 그러나 이전에 설명한 대로, ASPX 태그 지역화를 위한 리소스 파일이 이미 있는 경우 다시 사용할 수 있습니다 하 코드 지역화를 위해. 리소스 파일을 만들어야 하는 경우 기본 언어 리소스 파일에 이름을 사용 하 여 추가 사용자가 선택한를 *.resx* 확장 합니다. 지역화 된 리소스 파일에 언어별 문화권 추가 된 동일한 이름의 이름을 [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)]입니다. 포함 리소스를 위성 리소스 어셈블리를 생성할 수 있도록 하려면 각 리소스 파일의 빌드 작업 속성을 설정 합니다.

 위성 어셈블리를 만들려면 프로젝트를 빌드하고 다음 파일을 통해 추가 어셈블리로 추가 합니다 **고급** 탭의 **패키지 디자이너**합니다. 어셈블리를 추가할 때 추가 문화권 [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)] 폴더를 위치 경로 같은 *DE-DE\\{0} 프로젝트 항목 이름}.resources.dll*합니다. 이렇게 하면 패키지에 동일한 이름을 가진 파일을 포함 합니다.

 코드에서 호출 하 여 하드 코드 된 문자열을 대체 합니다 <xref:System.Web.HttpContext.GetGlobalResourceObject%2A> 메서드 구문을 사용 하 여:

```aspx-csharp
HttpContext.GetGlobalResourceObject("<Resource File Name>", "<String ID>")
```

 자세한 내용은 [방법: 코드 지역화](../sharepoint/how-to-localize-code.md)합니다.

#### <a name="web-part-code-localization"></a>웹 파트 코드 지역화
 웹 파트에는 WebDisplayName, Category 및 WebDescription 같은 하드 코드 된 문자열을 사용 하는 코드 특성을 포함 하는 사용자 지정 속성 편집기 기능이 포함 됩니다. 이러한 특성에 대 한 문자열 값을 대체 하려면 특성의 클래스에서 파생 되는 별도 클래스를 만듭니다. 해당 클래스에 특성의 속성을 설정 합니다. 특성 속성을 기본 클래스에 따라 달라 집니다. 예를 들어, WebDisplayName 특성 속성이 displaynamevalue이 고 WebDescription 특성 속성이 descriptionvalue입니다.

 파생된 클래스에서 리소스 파일 및 문자열 ID에 대 한 지역화 된 값을 가져오려고 ResourceManager 개체에서 문자열 ID 참조 속성 편집기 특성에이 값을 반환 합니다.

## <a name="see-also"></a>참고자료
- [방법: 기능 지역화](../sharepoint/how-to-localize-a-feature.md)
- [방법: ASPX 태그 지역화](../sharepoint/how-to-localize-aspx-markup.md)
- [방법: 코드 지역화](../sharepoint/how-to-localize-code.md)
- [방법: 리소스 파일 추가](../sharepoint/how-to-add-a-resource-file.md)
- [방법: 리소스 파일을 사용 하 여 지역화 된 이름, 속성 및 사용 권한을 지정 합니다.](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)
