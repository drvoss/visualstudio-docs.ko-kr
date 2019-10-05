---
title: 비즈니스 데이터를 사용 하 여 SharePoint에서 외부 목록 만들기
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Business Data Connectivity service [SharePoint development in Visual Studio], business data in a Web Part
- BDC [SharePoint development in Visual Studio], external list
- Business Data Connectivity service [SharePoint development in Visual Studio], business data in a SharePoint list
- BDC [SharePoint development in Visual Studio], business data in a SharePoint list
- BDC [SharePoint development in Visual Studio], business data in a Web Part
- BDC [SharePoint development in Visual Studio], entity backed list
- Business Data Connectivity service [SharePoint development in Visual Studio], entity backed list
- Business Data Connectivity service [SharePoint development in Visual Studio], external list
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: cf9c7d13e6aaac85d3bac4254247a3c07b39b5c3
ms.sourcegitcommit: 25570fb5fb197318a96d45160eaf7def60d49b2b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/30/2019
ms.locfileid: "66401063"
---
# <a name="walkthrough-create-an-external-list-in-sharepoint-by-using-business-data"></a>연습: 비즈니스 데이터를 사용 하 여 SharePoint에 외부 목록 만들기

데이터 연결 (BDC (비즈니스) 서비스를 SharePoint을 백 엔드 서버 응용 프로그램, 웹 서비스 및 데이터베이스의 비즈니스 데이터를 표시할 수 있습니다.

이 연습에서는 샘플 데이터베이스의 연락처 정보를 반환 하는 BDC 서비스에 대 한 모델을 만드는 방법을 보여 줍니다. 그런 다음 만들려는 외부 목록 SharePoint에서이 모델을 사용 하 여 합니다.

이 연습에서는 다음 작업을 수행합니다.

- 프로젝트를 만듭니다.
- 모델에 엔터티를 추가 합니다.
- Finder 메서드를 추가 합니다.
- 특정 Finder 메서드를 추가 합니다.
- 프로젝트를 테스트 합니다.

## <a name="prerequisites"></a>전제 조건

이 연습을 완료하려면 다음 구성 요소가 필요합니다.

- Windows 및 SharePoint 버전을 지원 합니다.

- AdventureWorks 예제 데이터베이스에 액세스 합니다. AdventureWorks 데이터베이스를 설치 하는 방법에 대 한 자세한 내용은 참조 하세요. [SQL Server 예제 데이터베이스](http://go.microsoft.com/fwlink/?LinkID=117483)합니다.

## <a name="create-a-project-that-contains-a-bdc-model"></a>BDC 모델이 포함 된 프로젝트 만들기

1. Visual Studio의 메뉴 모음에서 선택 **파일** > **새로 만들기** > **프로젝트**합니다.

     **새 프로젝트** 대화 상자가 열립니다.

2. 준 **Visual C#** 또는 **Visual Basic**를 확장 합니다 **SharePoint** 노드를 선택한 후는 **2010** 항목입니다.

3. 에 **템플릿을** 창 선택 **SharePoint 2010 프로젝트**, 프로젝트 이름을 **AdventureWorksTest**를 선택한 후는 **확인** 단추 .

     합니다 **SharePoint 사용자 지정 마법사** 나타납니다. 이 마법사를 사용 하 여 프로젝트를 디버깅 하 고 솔루션의 신뢰 수준을 설정 하는 사이트를 지정할 수 있습니다.

4. 선택 된 **팜 솔루션으로 배포** 신뢰 수준을 설정 하려면 옵션 단추입니다.

5. 선택 된 **완료** 기본 로컬 SharePoint 사이트를 적용 하는 단추입니다.

6. **솔루션 탐색기**, SharePoint 프로젝트 노드를 선택 합니다.

7. 메뉴 모음에서 **프로젝트** > **새 항목 추가**를 선택합니다.

     **새 항목 추가** 대화 상자가 열립니다.

8. 에 **템플릿을** 창 선택 **비즈니스 데이터 연결 모델 (팜 솔루션만 해당)** , 프로젝트 이름을 **adventureworkscontacts로 지정한**를 선택한 다음 합니다 **추가** 단추입니다.

## <a name="add-data-access-classes-to-the-project"></a>데이터 액세스 클래스를 프로젝트에 추가

1. 메뉴 모음에서 선택 **도구가** > **데이터베이스에 연결**합니다.

     **연결 추가** 대화 상자가 열립니다.

2. SQL Server AdventureWorks 샘플 데이터베이스에 대 한 연결을 추가 합니다.

     자세한 내용은 [연결 추가/수정 (Microsoft SQL Server)](https://msdn.microsoft.com/fa400910-26c3-4df7-b9d1-115e688b4ea3)합니다.

3. **솔루션 탐색기**에서 프로젝트 노드를 선택합니다.

4. 메뉴 모음에서 **프로젝트** > **새 항목 추가**를 선택합니다.

5. 에 **설치 된 템플릿** 창 선택 합니다 **데이터** 노드.

6. 에 **템플릿을** 창 선택 **LINQ to SQL 클래스**합니다.

7. 에 **이름** 상자에서 지정 **AdventureWorks**를 선택한 후는 **추가** 단추입니다.

     .dbml 파일이 프로젝트에 추가되고 O/R 디자이너(개체 관계형 디자이너)가 열립니다.

8. 메뉴 모음에서 선택 **뷰** > **서버 탐색기**합니다.

9. **서버 탐색기**AdventureWorks 예제 데이터베이스를 나타내는 노드를 확장 한 다음 확장, 합니다 **테이블** 노드.

10. 추가 된 **Contact (Person)** O/R 디자이너에 끌어 테이블입니다.

     엔터티 클래스가 만들어져 디자인 화면에 표시됩니다. 엔터티 클래스에 Contact (Person) 테이블의 열에 매핑되는 속성이 있습니다.

## <a name="remove-the-default-entity-from-the-bdc-model"></a>BDC 모델에서 기본 엔터티를 제거 합니다.

합니다 **비즈니스 데이터 연결 모델** 프로젝트는 모델에 Entity1 이라는 기본 엔터티를 추가 합니다. 이 엔터티를 제거 합니다. 나중에 새 엔터티를 추가 합니다. 빈 모델을 사용 하 여 시작 연습을 완료 하는 데 필요한 단계 수가 줄어듭니다.

1. **솔루션 탐색기**를 확장 합니다 **BdcModel1** 노드를 연 다음 합니다 *BdcModel1.bdcm* 파일.

2. Business Data Connectivity 모델 파일이 BDC 디자이너에서 열립니다.

3. 디자이너에서 바로 가기 메뉴를 열고 **Entity1**를 선택한 후 **삭제**합니다.

4. **솔루션 탐색기**에 대 한 바로 가기 메뉴를 열고 *Entity1.vb* (Visual Basic)에서는 또는 *Entity1.cs* (에서 C#)를 선택한 후 **삭제** .

5. 바로 가기 메뉴를 열고 *Entity1Service.vb* (Visual Basic에서는) 또는 *Entity1Service.cs* (에서 C#)를 선택한 후 **삭제**.

## <a name="add-an-entity-to-the-model"></a>모델에 엔터티 추가

모델에 엔터티를 추가 합니다. Visual Studio에서 엔터티를 추가할 수 있습니다 **도구 상자** BDC 디자이너에 있습니다.

1. 메뉴 모음에서 **보기** > **도구 상자**를 선택합니다.

2. 에 **BusinessDataConnectivity** 탭의 **도구 상자**, 추가 **엔터티** BDC 디자이너에 합니다.

     새 엔터티 디자이너에 표시 됩니다. 라는 파일을 추가 하는 visual Studio *EntityService.vb* (Visual Basic에서는) 또는 *EntityService.cs* (C#의 경우)의 프로젝트에 있습니다.

3. 메뉴 모음에서 선택 **뷰** > **속성** > **창**합니다.

4. 에 **속성** 창에서 설정 합니다 **이름** 속성 값을 **연락처**.

5. 디자이너에서 엔터티에 대 한 바로 가기 메뉴를 열고 **추가**를 선택한 후 **식별자**합니다.

     엔터티에 대해 새 식별자를 표시 됩니다.

6. 에 **속성** 창에서 식별자의 이름을 변경할 **ContactID**합니다.

7. 에 **형식 이름이** 목록에서 선택 **System.Int32**합니다.

## <a name="add-a-specific-finder-method"></a>특정 Finder 메서드 추가

특정 연락처를 표시할 BDC 서비스를 사용 하려면 특정 Finder 메서드를 추가 해야 합니다. BDC 서비스 사용자 목록에 항목을 선택 하 고 다음 선택 하는 경우 특정 Finder 메서드를 호출 합니다 **보기 항목** 리본의 단추입니다.

Specificfinder 메서드를 사용 하 여 연락처 엔터티를 추가 합니다 **BDC 메서드 세부 정보** 창입니다. 특정 엔터티를 반환할 메서드에 코드를 추가 합니다.

1. BDC 디자이너에서 선택 합니다 **연락처** 엔터티.

2. 메뉴 모음에서 선택 **뷰** > **기타 Windows** > **BDC 메서드 세부 정보**합니다.

     BDC 메서드 세부 정보 창이 열립니다.

3. 에 **메서드를 추가** 목록에서 선택 **Specificfinder 메서드 만들기**합니다.

     Visual Studio 모델에는 다음 요소를 추가합니다. 이러한 요소에 표시 된 **BDC 메서드 세부 정보** 창입니다.

    - ReadItem 라는 메서드가 있습니다.

    - 메서드에 대 한 입력된 매개 변수입니다.

    - 메서드에 대 한 반환 매개 변수입니다.

    - 각 매개 변수의 형식 설명자입니다.

    - 메서드에 대 한 메서드 인스턴스입니다.

4. 에 **BDC 메서드 세부 정보** 창에 대해 표시 되는 목록을 연 합니다 **연락처** 형식 설명자를 선택한 후 **편집**합니다.

     합니다 **BDC 탐색기** 열리고 모델의 계층적 뷰를 제공 합니다.

5. **속성** 창 옆에 있는 목록을 연를 **TypeName** 속성을 선택 합니다 **현재 프로젝트** 탭을 선택한 후는 **연락처**속성입니다.

6. 에 **BDC 탐색기**의 바로 가기 메뉴를 열고는 **연락처**를 선택한 후 **형식 설명자 추가**합니다.

     이라는 새 형식 설명자 **TypeDescriptor1** 에 표시 되는 **BDC 탐색기**합니다.

7. 에 **속성** 창에서 설정 합니다 **이름** 속성 값을 **ContactID**.

8. 옆에 있는 목록을 연 합니다 **TypeName** 속성을 선택한 후 **Int32**합니다.

9. 옆에 있는 목록을 연 합니다 **식별자** 속성을 선택한 후 **ContactID**합니다.

10. 다음 필드의 각 형식 설명자를 만들려면 6 단계를 반복 합니다.

    |이름|형식 이름|
    |----------|---------------|
    |FirstName|System.String|
    |LastName|System.String|
    |전화 번호|System.String|
    |EmailAddress|System.String|
    |EmailPromotion|System.Int32|
    |NameStyle|System.Boolean|
    |PasswordHash|System.String|
    |PasswordSalt|System.String|

11. BDC 디자이너에서에 **연락처** 엔터티를 열고 합니다 **ReadItem** 메서드.

     연락처 서비스 코드 파일이 코드 편집기에서 열립니다.

12. 에 `ContactService` 클래스를 대체 합니다 `ReadItem` 메서드를 다음 코드로 합니다. 이 코드는 다음 작업을 수행합니다.

    - AdventureWorks 데이터베이스의 Contact 테이블에서 레코드를 검색합니다.

    - BDC 서비스에 연락처 엔터티를 반환합니다.

    > [!NOTE]
    > 값을 `ServerName` 필드 서버의 이름입니다.

     [!code-csharp[SP_BDC#3](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs#3)]
     [!code-vb[SP_BDC#3](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb#3)]

## <a name="add-a-finder-method"></a>Finder 메서드 추가

연락처 목록에 표시할 BDC 서비스를 사용 하려면 Finder 메서드를 추가 해야 합니다. Finder 메서드를 사용 하 여 연락처 엔터티를 추가 합니다 **BDC 메서드 세부 정보** 창입니다. BDC 서비스에 엔터티 컬렉션을 반환할 메서드에 코드를 추가 합니다.

1. BDC 디자이너에서 선택 합니다 **연락처** 엔터티.

2. 에 **BDC 메서드 세부 정보** 창, 축소 합니다 **ReadItem** 노드.

3. 에 **메서드를 추가** 목록에서 합니다 **ReadList** 메서드를 선택 **Finder 메서드 만들기**합니다.

     Visual Studio에는 메서드, 반환 매개 변수 및 형식 설명자를 추가합니다.

4. BDC 디자이너에서에 **연락처** 엔터티를 열고 합니다 **ReadList** 메서드.

     코드 편집기에서 Contact 서비스의 코드 파일이 열립니다.

5. 에 `ContactService` 클래스를 대체 합니다 `ReadList` 메서드를 다음 코드로 합니다. 이 코드는 다음 작업을 수행합니다.

   - AdventureWorks 데이터베이스의 Contacts 테이블에서 데이터를 검색합니다.

   - BDC 서비스에 연락처 엔터티 목록을 반환합니다.

     > [!NOTE]
     > 값을 `ServerName` 필드 서버의 이름입니다.

     [!code-csharp[SP_BDC#2](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs#2)]
     [!code-vb[SP_BDC#2](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb#2)]

## <a name="test-the-project"></a>프로젝트 테스트

프로젝트를 실행 하면 SharePoint 사이트가 열리고 Visual Studio을 Business Data Connectivity 서비스 모델을 추가 합니다. 연락처 엔터티를 참조 하는 SharePoint에서 외부 목록을 만듭니다. AdventureWorks 데이터베이스의 연락처에 대 한 데이터를 목록에 나타납니다.

> [!NOTE]
> 솔루션을 디버그할 수 있으려면 SharePoint의 보안 설정을 수정 해야 합니다. 자세한 내용은 [비즈니스 데이터 연결 모델 디자인](../sharepoint/designing-a-business-data-connectivity-model.md)합니다.

1. **F5** 키를 선택합니다.

     SharePoint 사이트가 열립니다.

2. 에 **사이트 작업** 메뉴에서 선택 합니다 **기타 옵션** 명령입니다.

3. 에 **만들기** 페이지를 선택 합니다 **외부 목록** 템플릿을 선택한 후는 **만들기** 단추.

4. 사용자 지정 목록 이름을 **연락처**합니다.

5. 옆에 있는 찾아보기 단추를 선택 합니다 **외부 콘텐츠 형식** 필드입니다.

6. 에 **외부 콘텐츠 형식 선택** 대화 상자를 선택 합니다 **AdventureWorksContacts.BdcModel1.Contact** 항목을 선택한 후는 **만들기** 단추.

     SharePoint에서 AdventureWorks 샘플 데이터베이스의 연락처를 포함하는 외부 목록을 만듭니다.

7. SpecificFinder 메서드를 테스트하려면 목록에서 연락처를 선택합니다.

8. 리본에서 선택 합니다 **항목** 탭을 선택한 다음는 **보기 항목** 명령입니다.

     선택한 연락처의 세부 정보가 폼에 나타납니다.

## <a name="next-steps"></a>다음 단계

다음이 항목에서는 sharepoint에서 BDC 서비스 모델을 설계 하는 방법에 알아볼 수 있습니다.

- [방법: Creator 메서드 추가](../sharepoint/how-to-add-a-creator-method.md)합니다.
- [방법: Updater 메서드 추가](../sharepoint/how-to-add-an-updater-method.md)합니다.
- [방법: Deleter 메서드 추가](../sharepoint/how-to-add-a-deleter-method.md)합니다.

## <a name="see-also"></a>참고자료

[비즈니스 데이터 연결 모델 디자인](../sharepoint/designing-a-business-data-connectivity-model.md)
[비즈니스 데이터 연결 모델 만들기](../sharepoint/creating-a-business-data-connectivity-model.md)
[BDC 모델 디자인 도구 개요](../sharepoint/bdc-model-design-tools-overview.md) 
 [ SharePoint 비즈니스 데이터 통합](../sharepoint/integrating-business-data-into-sharepoint.md)
