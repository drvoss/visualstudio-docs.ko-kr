---
title: '연습: SharePoint를 위한 웹 파트 만들기 | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Web Parts [SharePoint development in Visual Studio], developing
- Web Parts [SharePoint development in Visual Studio], creating
- Web Parts [SharePoint development in Visual Studio], designing
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 622dfafbe16efee1e953fbc42bfa3b94cfa3cc58
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62965273"
---
# <a name="walkthrough-create-a-web-part-for-sharepoint"></a>연습: SharePoint 용 웹 파트 만들기

웹 파트를 사용 하면 직접 브라우저를 사용 하 여 콘텐츠, 모양 및 SharePoint 사이트 페이지의 동작을 수정할 수 있도록 합니다. 이 연습에서는 사용 하 여 웹 파트를 만드는 방법을 보여 줍니다.는 **웹 파트** Visual Studio 2010의 항목 템플릿.

웹 파트 데이터 표에서 직원을 표시합니다. 사용자는 직원 데이터를 포함 하는 파일의 위치를 지정 합니다. 사용자는 직원은 관리자만 목록에 표시 되도록 데이터 표를 필터링 수도 있습니다.

이 연습에서는 다음 작업을 수행합니다.

- Visual Studio를 사용 하 여 웹 파트를 만드는 **웹 파트** 항목 템플릿.

- 웹 파트의 사용자가 있는 속성 만들기를 설정할 수 있습니다. 이 속성은 직원 데이터 파일의 위치를 지정합니다.

- 웹 파트 컨트롤을 추가 하 여 웹 파트의 콘텐츠를 렌더링 하는 컨트롤 컬렉션입니다.

- 새 메뉴 항목을 만들기는 *동사* 렌더링된 된 웹 파트의 동사 메뉴에 표시 됩니다. 웹 파트에 표시 되는 데이터를 수정 하려면 사용자는 동사를 사용 합니다.

- Sharepoint에서 웹 파트를 테스트 합니다.

    > [!NOTE]
    > 일부 Visual Studio 사용자 인터페이스 요소의 경우 다음 지침에 설명된 것과 다른 이름 또는 위치가 시스템에 표시될 수 있습니다. 이러한 요소는 사용하는 Visual Studio 버전 및 설정에 따라 결정됩니다. 자세한 내용은 [Visual Studio IDE 개인 설정](../ide/personalizing-the-visual-studio-ide.md)을 참조하세요.

## <a name="prerequisites"></a>전제 조건

- 지원되는 Microsoft Windows 및 SharePoint 버전.

- Visual Studio 2017 또는 Azure DevOps 서비스입니다.

## <a name="create-an-empty-sharepoint-project"></a>빈 SharePoint 프로젝트 만들기

먼저 빈 SharePoint 프로젝트를 만듭니다. 사용 하 여 프로젝트에 웹 파트를 추가 합니다는 나중에 **웹 파트** 항목 템플릿.

1. 시작 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 를 사용 하 여 합니다 **관리자 권한으로 실행** 옵션입니다.

2. 메뉴 모음에서 선택 **파일** > **새로 만들기** > **프로젝트**합니다.

3. 에 **새 프로젝트** 대화 상자에서 합니다 **SharePoint** 언어를 사용 하 고 선택 하려는 아래의 노드를 **2010** 노드.

4. 에 **템플릿** 창 선택 **SharePoint 2010 프로젝트**를 선택한 후는 **확인** 단추입니다.

     합니다 **SharePoint 사용자 지정 마법사** 나타납니다. 이 마법사를 사용 하면 프로젝트 및 솔루션의 신뢰 수준을 디버그 하는 데 사용할 사이트를 선택할 수 있습니다.

5. 선택 합니다 **팜 솔루션으로 배포** 옵션 단추를 선택한 후는 **마침** 기본 로컬 SharePoint 사이트를 적용 하는 단추입니다.

## <a name="add-a-web-part-to-the-project"></a>웹 파트를 프로젝트에 추가

추가 된 **웹 파트** 프로젝트 항목입니다. 합니다 **웹 파트** 항목 웹 파트 코드 파일을 추가 합니다. 나중에 웹 파트의 콘텐츠를 렌더링 하는 웹 파트 코드 파일에 코드를 추가 합니다.

1. 메뉴 모음에서 **프로젝트** > **새 항목 추가**를 선택합니다.

2. 에 **새 항목 추가** 대화 상자의 합니다 **설치 된 템플릿** 창 확장를 **SharePoint** 노드를 선택한 후는 **2010** 노드.

3. SharePoint 템플릿 목록에서 선택 합니다 **웹 파트** 템플릿을 선택한 후 합니다 **추가** 단추입니다.

     합니다 **웹 파트** 항목에 표시 됩니다 **솔루션 탐색기**합니다.

## <a name="rendering-content-in-the-web-part"></a>웹 파트에서 콘텐츠를 렌더링합니다.

웹 파트 클래스의 controls 컬렉션에 추가 하 여 웹 파트에 표시 하려는 컨트롤을 지정할 수 있습니다.

1. **솔루션 탐색기**오픈 *WebPart1.vb* (Visual Basic)에서는 또는 *WebPart1.cs* (C#에서).

     웹 파트 코드 파일이 코드 편집기에서 열립니다.

2. 웹 파트 코드 파일의 맨 위에 다음 문을 추가 합니다.

     [!code-csharp[SP_WebPart#1](../sharepoint/codesnippet/CSharp/spext_webpart/webpart1/webpart1.cs#1)]
     [!code-vb[SP_WebPart#1](../sharepoint/codesnippet/VisualBasic/spext_webpart/webpart1/webpart1.vb#1)]

3. `WebPart1` 클래스에 다음 코드를 추가합니다. 이 코드는 다음 필드를 선언합니다.

   - 직원 웹 파트에 표시할 데이터 표입니다.

   - 데이터 표를 필터링 하는 데 사용 되는 컨트롤에 나타나는 텍스트입니다.

   - 데이터 표에 데이터를 표시할 수 없는 경우 오류를 표시 하는 레이블.

   - 직원 데이터 파일의 경로 포함 하는 문자열입니다.

     [!code-csharp[SP_WebPart#2](../sharepoint/codesnippet/CSharp/spext_webpart/webpart1/webpart1.cs#2)]
     [!code-vb[SP_WebPart#2](../sharepoint/codesnippet/VisualBasic/spext_webpart/webpart1/webpart1.vb#2)]

4. `WebPart1` 클래스에 다음 코드를 추가합니다. 이 코드 라는 사용자 지정 속성을 추가 `DataFilePath` 웹 파트입니다. 사용자 지정 속성은 사용자가 SharePoint에서 설정할 수 있는 속성입니다. 이 속성을 가져옵니다 및 데이터 그리드를 채우는 데 사용 되는 XML 데이터 파일의 위치를 설정 합니다.

     [!code-csharp[SP_WebPart#3](../sharepoint/codesnippet/CSharp/spext_webpart/webpart1/webpart1.cs#3)]
     [!code-vb[SP_WebPart#3](../sharepoint/codesnippet/VisualBasic/spext_webpart/webpart1/webpart1.vb#3)]

5. `CreateChildControls` 메서드를 다음 코드로 바꿉니다. 이 코드는 다음 작업을 수행합니다.

   - 이전 단계에서 선언한 레이블을 확인 하 고 데이터 표를 추가 합니다.

   - 데이터 표에서 직원 데이터를 포함 하는 XML 파일에 바인딩합니다.

     [!code-csharp[SP_WebPart#4](../sharepoint/codesnippet/CSharp/spext_webpart/webpart1/webpart1.cs#4)]
     [!code-vb[SP_WebPart#4](../sharepoint/codesnippet/VisualBasic/spext_webpart/webpart1/webpart1.vb#4)]

6. 다음 메서드를 `WebPart1` 클래스에 추가합니다. 이 코드는 다음 작업을 수행합니다.

   - 렌더링된 된 웹 파트의 웹 파트 동사 메뉴에 표시 되는 동사를 만듭니다.

   - 사용자가 동사 메뉴에서 동사를 선택할 때 발생하는 이벤트를 처리합니다. 이 코드는 데이터 표에 표시 되는 직원 목록을 필터링 합니다.

     [!code-csharp[SP_WebPart#5](../sharepoint/codesnippet/CSharp/spext_webpart/webpart1/webpart1.cs#5)]
     [!code-vb[SP_WebPart#5](../sharepoint/codesnippet/VisualBasic/spext_webpart/webpart1/webpart1.vb#5)]

## <a name="test-the-web-part"></a>웹 파트 테스트

프로젝트를 실행 하면 SharePoint 사이트가 열립니다. 웹 파트는 sharepoint에서 웹 파트 갤러리에 자동으로 추가 됩니다. 모든 웹 파트 페이지로 웹 파트를 추가할 수 있습니다.

1. 메모장 파일에 다음 XML을 붙여 넣습니다. 이 XML 파일에는 웹 파트에 표시 되는 샘플 데이터를 포함 합니다.

    ```xml
    <?xml version="1.0" encoding="utf-8" ?>
        <employees xmlns="http://schemas.microsoft.com/vsto/samples">
           <employee>
               <name>David Hamilton</name>
               <hireDate>2001-05-11</hireDate>
               <title>Sales Associate</title>
           </employee>
           <employee>
               <name>Karina Leal</name>
               <hireDate>1999-04-01</hireDate>
               <title>Manager</title>
           </employee>
           <employee>
               <name>Nancy Davolio</name>
               <hireDate>1992-05-01</hireDate>
               <title>Sales Associate</title>
           </employee>
           <employee>
               <name>Steven Buchanan</name>
               <hireDate>1955-03-04</hireDate>
               <title>Manager</title>
           </employee>
           <employee>
               <name>Suyama Michael</name>
               <hireDate>1963-07-02</hireDate>
               <title>Sales Associate</title>
           </employee>
        </employees>
    ```

2. 메모장의 메뉴 모음에서 선택 **파일** > **이름으로 저장**합니다.

3. 에 **다른 이름으로 저장** 대화 상자의 합니다 **형식으로 저장** 목록에서 선택 **모든 파일**합니다.

4. 에 **파일 이름** 상자에 입력 합니다 **data.xml**합니다.

5. 사용 하 여 폴더를 선택 합니다 **폴더 찾아보기** 단추를 선택한 후 합니다 **저장** 단추입니다.

6. Visual Studio에서 선택 합니다 **F5** 키입니다.

     SharePoint 사이트가 열립니다.

7. 에 **사이트 작업** 메뉴 선택 **기타 옵션**합니다.

8. **만들기** 페이지를 선택 합니다 **웹 파트 페이지** 형식을 선택한 다음 선택 합니다 **만들기** 단추.

9. 에 **새 웹 파트 페이지** 페이지에서 페이지의 이름을 **SampleWebPartPage.aspx**를 선택한 후는 **만들기** 단추입니다.

     웹 파트 페이지가 표시 됩니다.

10. 웹 파트 페이지의 모든 영역을 선택 합니다.

11. 페이지의 맨 위에 있는 선택 합니다 **삽입** 탭을 선택한 다음는 **웹 파트** 단추입니다.

12. **범주** 창 선택는 **사용자 지정** 폴더를 선택 합니다 **WebPart1** 웹 파트 선택한 후는 **추가** 단추.

     웹 파트 페이지에 나타납니다.

## <a name="test-the-custom-property"></a>사용자 지정 속성을 테스트 합니다.

웹 파트에 나타나는 데이터 그리드를 채우기 위해 각 직원에 대 한 데이터가 포함 된 XML 파일의 경로 지정 합니다.

1. 웹 파트의 오른쪽에 표시 되는 화살표를 선택 하 고 선택한 **웹 파트 편집** 나타나는 메뉴에서.

     웹 파트에 대 한 속성을 포함 하는 창 페이지의 오른쪽에 나타납니다.

2. 창에서 확장을 **기타** 노드를 이전에 만든 XML 파일의 경로 입력을 선택 합니다 **적용** 단추를 선택한 후는 **확인** 단추.

     웹 파트에서 직원의 목록이 표시 되는지 확인 합니다.

## <a name="test-the-web-part-verb"></a>웹 파트 동사를 테스트 합니다.

표시 하 고 웹 파트 동사 메뉴에 표시 되는 항목을 클릭 하 여 관리자가 아닌 직원을 숨깁니다.

1. 웹 파트의 오른쪽에 표시 되는 화살표를 선택 하 고 선택한 **관리자만 표시** 나타나는 메뉴에서.

     관리자가 직원만 웹 파트에 표시 됩니다.

2. 화살표를 다시 선택 하 고 선택한 **모든 직원 표시** 나타나는 메뉴에서.

     모든 직원에 게 웹 파트에 표시 됩니다.

## <a name="see-also"></a>참고자료

[SharePoint 용 웹 파트를 만들](../sharepoint/creating-web-parts-for-sharepoint.md)
[방법: SharePoint 웹 파트를 만듭니다](../sharepoint/how-to-create-a-sharepoint-web-part.md)
[방법: 디자이너를 사용 하 여 SharePoint 웹 파트를 만듭니다](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md)
[연습: 디자이너를 사용 하 여 SharePoint 용 웹 파트 만들기](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint-by-using-a-designer.md)
