---
title: 매개 변수가 있는 TableAdapter 쿼리 만들기
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
helpviewer_keywords:
- data [Visual Studio], TableAdapters
- TableAdapters, parameterized queries
- data [Visual Studio], searching data
- queries [Visual Studio], creating
- TableAdapters, searching data
- queries [Visual Studio], TableAdapters
ms.assetid: 104d1d19-b5a9-4071-b81e-1b3af08e9c7b
caps.latest.revision: 24
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 1da058cbbdda71758e9a158cfd6778a044797093
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65703822"
---
# <a name="create-parameterized-tableadapter-queries"></a>매개 변수가 있는 TableAdapter 쿼리 만들기
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

매개 변수가 있는 쿼리는 쿼리의 WHERE 절 조건을 충족하는 데이터를 반환합니다. 예를 들어 고객 목록을 반환하는 SQL 문 끝에 `WHERE City = @City`를 추가하여 특정 구/군/시의 고객만 표시하도록 고객 목록을 매개 변수화할 수 있습니다.  
  
데이터 집합 디자이너에서 매개 변수가 있는 TableAdapter 쿼리를 만듭니다. 사용 하 여 Windows 응용 프로그램에서 만들 수 있습니다는 **데이터 소스 매개 변수화** 명령 합니다 **데이터** 메뉴. 합니다 **데이터 소스 매개 변수화** 명령 매개 변수 값을 입력 하 고 쿼리를 실행할 수 있는 폼의 컨트롤을 만듭니다.  
  
> [!NOTE]
> 매개 변수가 있는 쿼리를 생성 하는 경우에 대 한 코딩 하는 데이터베이스에 관련 된 매개 변수 표기법을 사용 합니다. 예를 들어 Access 및 OleDb 데이터 소스는 물음표 '?'를 사용하여 매개 변수를 표기하므로 WHERE 절은 `WHERE City = ?`와 같습니다.  
  
> [!NOTE]
> 대화 상자와 메뉴 명령은 활성 설정 또는 사용 중인 버전에 따라 도움말에 설명 된 다 수 있습니다. 로 이동 설정을 변경 합니다 **도구** 선택한 메뉴 **설정 가져오기 및 내보내기**합니다. 자세한 내용은 [Visual Studio에서 개발 설정 사용자 지정](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3)을 참조하세요.  
  
## <a name="create-a-parameterized-tableadapter-query"></a>매개 변수가 있는 TableAdapter 쿼리 만들기 
  
- 원하는 매개 변수가 포함된 WHERE 절을 SQL 문에 추가하여 새 TableAdapter를 만듭니다. 자세한 내용은 [만들기 및 Tableadapter 구성](../data-tools/create-and-configure-tableadapters.md)합니다.  
  
     또는  
  
- 원하는 매개 변수가 포함된 WHERE 절을 SQL 문에 추가하여 기존 TableAdapter에 쿼리를 추가합니다.
  
### <a name="create-a-parameterized-query-while-designing-a-data-bound-form"></a>데이터 바인딩된 폼을 디자인 하는 동안 매개 변수가 있는 쿼리 만들기  
  
1. 데이터 세트에 이미 바인딩되어 있는 폼의 컨트롤을 선택합니다. 자세한 내용은 [Visual Studio에서 데이터 바인딩 Windows Forms 컨트롤](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)합니다.  
  
2. 에 **데이터** 메뉴에서**쿼리 추가**합니다.  
  
3. 원하는 매개 변수가 포함된 WHERE 절을 SQL 문에 추가하여 **검색 조건 작성기** 대화 상자에서 필요한 작업을 완료합니다.  
  
### <a name="add-a-query-to-an-existing-data-bound-form"></a>쿼리를 기존 데이터 바인딩된 폼에 추가  
  
1. **Windows Forms 디자이너**에서 폼을 엽니다.  
  
2. 에 **데이터** 메뉴에서 **쿼리 추가** 또는 **데이터 스마트 태그**합니다.  
  
   > [!NOTE]
   > **데이터** 메뉴에서 **쿼리 추가**를 사용할 수 없는 경우 매개 변수화를 추가할 데이터 소스가 표시되어 있는 폼의 컨트롤을 선택합니다. 예를 들어 폼의 <xref:System.Windows.Forms.DataGridView> 컨트롤에 데이터가 표시되는 경우 해당 컨트롤을 선택합니다. 폼의 개별 컨트롤에 데이터가 표시되는 경우에는 데이터 바인딩된 컨트롤을 선택합니다.  
  
3. 에 **선택한 데이터 원본 테이블** 영역에서 선택 하려는 tablethat 매개 변수화를 추가 합니다.  
  
4. 새 쿼리를 만드는 경우 **새 쿼리 이름** 상자에 이름을 입력합니다.  
  
    또는  
  
    **기존 쿼리 이름** 상자에서 쿼리를 선택합니다.  
  
5. 에 **쿼리 텍스트** 상자, 매개 변수를 사용 하는 쿼리를 입력 합니다.  
  
6. **확인**을 선택합니다.  
  
    매개 변수를 입력하기 위한 컨트롤과 **로드** 단추가 <xref:System.Windows.Forms.ToolStrip> 컨트롤의 폼에 추가됩니다.  
  
   TableAdapter 매개 변수가 현재 값이 없는 레코드를 쿼리 하려는 경우 null 값 할당할 수 있습니다. 예를 들어 포함 된 다음 쿼리에 `ShippedDate` 매개 변수에서 해당 `WHERE` 절:  
  
   ```sql
   SELECT CustomerID, OrderDate, ShippedDate  
   FROM Orders  
   WHERE (ShippedDate = @ShippedDate) OR  
   (ShippedDate IS NULL)  
   ```

TableAdapter에 대 한 쿼리 인 경우 다음 코드를 사용 하 여 운송 하지 않았다고 하는 모든 주문에 대해 쿼리할 수 있습니다.  
  
   [!code-csharp[VbRaddataTableAdapters#8](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataTableAdapters/CS/Form2.cs#8)]
   [!code-vb[VbRaddataTableAdapters#8](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataTableAdapters/VB/Form2.vb#8)]  
  
### <a name="enable-a-query-to-accept-null-values"></a>Null 값을 허용 하도록 쿼리를 사용 하도록 설정  
  
1. 에 **데이터 집합 디자이너**, null 매개 변수 값을 허용 해야 하는 TableAdapter 쿼리를 선택 합니다.  
  
2. 에 **속성** 창에서 **매개 변수**합니다. 줄임표를 누릅니다 ( **...** ) 버튼을 클릭 하 여 **매개 변수 컬렉션 편집기**합니다.  
  
3. Null 값을 허용 하는 매개 변수를 선택 하 고 설정 합니다 **AllowDbNull** 속성을 `true`입니다.  
  
## <a name="see-also"></a>참고자료

- [TableAdapter를 사용하여 데이터 집합 채우기](../data-tools/fill-datasets-by-using-tableadapters.md)