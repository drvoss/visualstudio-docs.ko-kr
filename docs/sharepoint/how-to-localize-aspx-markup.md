---
title: '방법: ASPX 태그 지역화 | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- localizing XML [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, localizing
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 4cd3c17a9e771ad9a1aee7526f24e3a8282f208d
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63443098"
---
# <a name="how-to-localize-aspx-markup"></a>방법: ASPX 태그 지역화
  [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] (.aspx) 페이지는 일반적으로 하드 코드 된 문자열 값을 사용합니다. 이러한 문자열을 지역화 하려면 지역화 된 리소스를 참조 하는 식으로 대체 합니다.

## <a name="localize-aspx-markup"></a>ASPX 태그 지역화

#### <a name="to-localize-aspx-markup"></a>ASPX 태그 지역화

1. 별도 리소스 파일 추가: 기본 언어 및 각각에 대 한 지역화 된 언어입니다.

     태그 및 코드가 아닌 지역화 하는 경우에 전역 리소스 파일 프로젝트 항목을 추가 합니다. 코드와 태그를 지역화 하는 경우에 리소스 파일 프로젝트 항목을 추가 합니다.

    1. 전역 리소스 파일을 추가할 **솔루션 탐색기**선택한을 SharePoint 프로젝트 항목에 대 한 바로 가기 메뉴를 열고 **추가** > **새 항목**합니다. SharePoint에서 **2010** 노드를 선택 합니다 **전역 리소스 파일** 템플릿.

    2. 리소스 파일에 추가할 **솔루션 탐색기**선택한을 SharePoint 프로젝트 항목에 대 한 바로 가기 메뉴를 열고 **추가** > **새 항목**합니다. 준 합니다 **Visual Basic** 또는 **Visual C#** 노드를 선택 합니다 **리소스 파일** 템플릿.

    > [!NOTE]
    > 배포 유형 속성을 사용 하도록 설정 하려면 SharePoint 프로젝트 항목에 리소스 파일을 추가 해야 합니다. 이 속성은이 절차의 뒷부분에서 필요 합니다. 솔루션에 SharePoint 프로젝트 항목을 찾을 수 없는 경우에 빈 SharePoint 프로젝트를 추가 및 해당 기본값을 제거할 수 있습니다 *Elements.xml* 파일입니다.

2. 기본 언어 리소스 파일에 추가 된 원하는 이름을 지정 합니다.는 *.resx* MyAppResources.resx 같은 확장 합니다. 지역화된 각 리소스 파일에 동일한 기본 이름을 사용하지만 문화권 [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)]를 추가합니다. 독일어 이름 리소스를 지역화 하는 예를 들어 *의 경우 MyAppResources.de-DE.resx*합니다.

3. 값을 변경 합니다 **배포 유형** 각 리소스 파일의 속성 **AppGlobalResource** 서버의 App_GlobalResources 폴더에 배포 하도록 합니다.

4. 리소스 ASPX 태그 외에 코드도 지역화를 사용 하는 경우의 값을 유지 합니다 **빌드 작업** 속성으로 각 파일의 **포함 리소스**합니다. 리소스 파일을 사용 하 여 태그만 지역화 하는, 하는 경우 파일의 속성 값을 선택적으로 변경할 수 있습니다 **콘텐츠**합니다. 자세한 내용은 [지역화 SharePoint 솔루션](../sharepoint/localizing-sharepoint-solutions.md)합니다.

5. 각 리소스 파일을 열고 각 파일에 동일한 문자열 Id를 사용 하 여 지역화 된 문자열을 추가 합니다.

6. 에 [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] ASPX 페이지나 컨트롤에 대 한 태그 다음 형식을 사용 하는 값으로 하드 코드 된 문자열을 대체 합니다.

    ```aspx-csharp
    <%$Resources:Resource File Name, String ID%>
    ```

     예를 들어, 응용 프로그램 페이지에서 레이블 컨트롤에 대 한 텍스트를 지역화 하려면 다음과 같이 변경

    ```aspx-csharp
    <asp:Content ID="Main" ContentPlaceHolderID="PlaceHolderMain" runat="server">
    <asp:Label ID="lbl" runat="server" Text="Label text"></asp:Label>
    </asp:Content>
    ```

     다음으로 변경:

    ```aspx-csharp
    <asp:Content ID="Main" ContentPlaceHolderID="PlaceHolderMain" runat="server">
    <asp:Label ID="lbl" runat="server" Text="<%$Resources:MyAppResources,String1%>"></asp:Label>
    </asp:Content>
    ```

7. 선택 된 **F5** 키를 빌드하고 응용 프로그램을 실행 합니다.

8. Sharepoint의 기본값과에서 표시 언어를 변경 합니다.

     응용 프로그램에서 지역화 된 문자열을 표시 합니다. 지역화 된 리소스를 표시 하려면 SharePoint 서버에 리소스 파일의 문화권과 일치 하는 언어 팩 설치 되어 있어야 합니다.

## <a name="see-also"></a>참고자료
- [SharePoint 솔루션 지역화](../sharepoint/localizing-sharepoint-solutions.md)
- [방법: 기능 지역화](../sharepoint/how-to-localize-a-feature.md)
- [방법: 리소스 파일 추가](../sharepoint/how-to-add-a-resource-file.md)
- [방법: 코드 지역화](../sharepoint/how-to-localize-code.md)
