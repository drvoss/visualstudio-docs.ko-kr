---
title: 동시성 예외 처리 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- concurrency control, exceptions
- datasets [Visual Basic], errors
- exception handling, concurrency issues
- data concurrency, walkthroughs
- updating datasets, errors
- concurrency control, walkthroughs
ms.assetid: 73ee9759-0a90-48a9-bf7b-9d6fc17bff93
caps.latest.revision: 27
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 5269ec74388fa9b09a4cceabad364d19409470df
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65699743"
---
# <a name="handle-a-concurrency-exception"></a>동시성 예외 처리
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

동시성 예외 (<xref:System.Data.DBConcurrencyException>)는 두 사용자가 동시에 데이터베이스에서 동일한 데이터를 변경 하려고 할 때 발생 합니다. 이 연습에서는 catch 하는 방법을 보여 주는 Windows 응용 프로그램을 만든를 <xref:System.Data.DBConcurrencyException>오류를 발생 시킨 행 찾아 처리 하는 방법에 대 한 전략에 알아봅니다.  
  
 이 연습에서는 다음 프로세스를 안내합니다.  
  
1. 새 **Windows 응용 프로그램** 프로젝트입니다.  
  
2. Northwind 기반으로 새 데이터 집합 만들기 `Customers` 테이블입니다.  
  
3. 양식 만들기는 <xref:System.Windows.Forms.DataGridView> 데이터를 표시 합니다.  
  
4. 데이터 집합의 데이터로 채우는 `Customers` Northwind 데이터베이스의 테이블입니다.  
  
5. 사용 된 [Visual Database Tools](https://msdn.microsoft.com/6b145922-2f00-47db-befc-bf351b4809a1) 에 직접 액세스 하려면 Visual Studio에서를 `Customers` 데이터 테이블 및 레코드를 변경 합니다.  
  
6. 다른 값으로 동일한 레코드를 변경, 데이터 집합을 업데이트 하 고 동시성 오류가 발생 하는 데이터베이스에 변경 내용 쓰기 시도 합니다.  
  
7. 오류를 catch 한 다음 계속 해 서 데이터베이스를 업데이트 또는 업데이트 작업을 취소 여부를 결정 하는 레코드의 다른 버전을 표시 합니다.  
  
## <a name="prerequisites"></a>전제 조건  
 이 연습을 완료하려면 다음 사항이 필요합니다.  
  
- 업데이트를 수행할 수 있는 권한 가진 Northwind 샘플 데이터베이스에 액세스 합니다.
  
> [!NOTE]
> 대화 상자와 메뉴 명령은 활성 설정 또는 사용 중인 버전에 따라 도움말에서 설명 하는 것에서 다 수 있습니다. 설정을 변경하려면 **도구** 메뉴에서 **설정 가져오기 및 내보내기** 를 선택합니다. 자세한 내용은 [Visual Studio에서 개발 설정 사용자 지정](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3)을 참조하세요.  
  
## <a name="create-a-new-project"></a>새 프로젝트 만들기  
 새 Windows 응용 프로그램을 만들어 연습을 시작 합니다.  
  
#### <a name="to-create-a-new-windows-application-project"></a>새 Windows 응용 프로그램 프로젝트를 만들려면  
  
1. 에 **파일** 메뉴에서 새 프로젝트를 만듭니다.  
  
2. 에 **프로젝트 형식** 창, 프로그래밍 언어를 선택 합니다.  
  
3. **템플릿** 창에서 **Windows 응용 프로그램**을 선택합니다.  
  
4. 프로젝트 이름을 `ConcurrencyWalkthrough`를 선택한 후 **확인**합니다.  
  
     Visual Studio 프로젝트를 추가 합니다 **솔루션 탐색기** 디자이너에서 새 폼이 표시 됩니다.  
  
## <a name="create-the-northwind-dataset"></a>Northwind 데이터 집합을 만들려면  
 명명 된 데이터 집합을 만들면이 섹션에서는 `NorthwindDataSet`합니다.  
  
#### <a name="to-create-the-northwinddataset"></a>NorthwindDataSet를 만들려면  
  
1. 에 **데이터** 메뉴 선택 **새 데이터 소스 추가**합니다.  
  
     [데이터 원본 구성](https://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f) 마법사가 열립니다.  
  
2. 에 **데이터 소스 형식 선택**화면에서 **데이터베이스**합니다.  
  
3. 사용 가능한 연결 목록에서 Northwind 샘플 데이터베이스에 대 한 연결을 선택 합니다. 연결 된 연결 목록에서 사용할 수 없는 경우 선택**새 연결**  
  
    > [!NOTE]
    > 로컬 데이터베이스 파일에 연결 하는 경우 선택 **No** 프로젝트에 파일을 추가 하려는 설정 하려는 경우 메시지가 표시 되 면 합니다.  
  
4. 에 **응용 프로그램 구성 파일에 연결 문자열 저장**화면에서 **다음**합니다.  
  
5. 확장을 **테이블** 노드를 선택 합니다 `Customers` 테이블입니다. 데이터 집합에 대 한 기본 이름을 해야 `NorthwindDataSet`합니다.  
  
6. 선택 **완료** 데이터 집합 프로젝트에 추가 합니다.  
  
## <a name="create-a-data-bound-datagridview-control"></a>데이터 바인딩된 DataGridView 컨트롤 만들기  
 만든이 섹션에서는 <xref:System.Windows.Forms.DataGridView> 끌어서를 **고객** 에서 항목을 **데이터 원본** 창에서 Windows 폼으로 합니다.  
  
#### <a name="to-create-a-datagridview-control-that-is-bound-to-the-customers-table"></a>Customers 테이블에 바인딩되는 DataGridView 컨트롤을 만들려면  
  
1. 에 **데이터** 메뉴에서 선택 **데이터 소스 표시** 열려는 합니다 **데이터 소스 창**합니다.  
  
2. 에 **데이터 원본** 창 확장 합니다 **NorthwindDataSet** 노드를 선택한 후는 **고객** 테이블.  
  
3. 테이블 노드의 아래쪽 화살표를 선택 하 고 선택한 **DataGridView** 드롭 다운 목록에서.  
  
4. 폼의 빈 영역으로 테이블을 끕니다.  
  
     A <xref:System.Windows.Forms.DataGridView> 라는 컨트롤 `CustomersDataGridView` 및 <xref:System.Windows.Forms.BindingNavigator> 라는 `CustomersBindingNavigator` 바인딩되는 폼에 추가 됩니다는 <xref:System.Windows.Forms.BindingSource>합니다. 이에서는 설정에 바인딩된 합니다 `Customers` 테이블에 `NorthwindDataSet`합니다.  
  
## <a name="test-the-form"></a>형식 테스트  
 이제 폼이이 지점까지 예상 대로 작동 하는지 확인을 테스트할 수 있습니다.  
  
#### <a name="to-test-the-form"></a>폼을 테스트 하려면  
  
1. 선택 **F5** 응용 프로그램을 실행 하려면  
  
     폼이 표시는 <xref:System.Windows.Forms.DataGridView> 데이터로 채워진에 컨트롤을 `Customers` 테이블입니다.  
  
2. 에 **디버그** 메뉴에서**디버깅 중지**합니다.  
  
## <a name="handleconcurrency-errors"></a>Handleconcurrency 오류  
 오류를 처리 하는 방법을 응용 프로그램을 제어 하는 특정 비즈니스 규칙에 따라 달라 집니다. 이 연습에서는 다음 전략 예로 사용 하는 방법에 대 한 tohandle 동시성 오류가 발생 했습니다.  
  
 Applicationpresents 레코드의 세 가지 버전을 사용 하 여 사용자:  
  
- 데이터베이스의 현재 레코드  
  
- 데이터 집합에 로드 된 원본 레코드  
  
- 데이터 집합에서 제안 된 변경  
  
  그러면 사용자는 제안된 된 버전을 사용 하 여 데이터베이스를 덮어쓸 또는 업데이트 작업을 취소 및 데이터베이스의 새 값을 사용 하 여 데이터 집합을 새로 고칠 수 있습니다.  
  
#### <a name="to-enable-the-handling-of-concurrency-errors"></a>동시성 오류 처리를 사용 하도록 설정 하려면  
  
1. 사용자 지정 오류 처리기를 만듭니다.  
  
2. 사용자에 게 선택 항목을 표시 합니다.  
  
3. 사용자의 응답을 처리 합니다.  
  
4. 업데이트를 다시 하거나 데이터 집합의 데이터를 다시 설정 합니다.  
  
### <a name="addcode-to-handle-the-concurrency-exception"></a>동시성 예외를 처리 하는 Addcode  
 업데이트를 수행 하려고 하면 예외가 발생할 때 일반적으로 발생된 된 예외에서 제공 하는 정보를 사용 하 여 작업을 수행 하려고 합니다.  
  
 이 섹션에서는 데이터베이스를 업데이트 하는 코드를 추가 합니다. 또한 처리 된 <xref:System.Data.DBConcurrencyException> 이 발생, 다른 예외와 합니다.  
  
> [!NOTE]
> 합니다 `CreateMessage` 고 `ProcessDialogResults` 이 연습의 뒷부분에서 메서드를 추가 합니다.  
  
##### <a name="to-add-error-handling-for-the-concurrency-error"></a>동시성 오류를 처리 하는 오류를 추가 하려면  
  
1. 아래 다음 코드를 추가 합니다 `Form1_Load` 메서드:  
  
     [!code-csharp[VbRaddataConcurrency#1](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConcurrency/CS/Form1.cs#1)]
     [!code-vb[VbRaddataConcurrency#1](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConcurrency/VB/Form1.vb#1)]  
  
2. 대체는 `CustomersBindingNavigatorSaveItem_Click` 메서드를 호출 하는 `UpdateDatabase` 메서드를 다음과 같이 표시 됩니다:  
  
     [!code-csharp[VbRaddataConcurrency#2](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConcurrency/CS/Form1.cs#2)]
     [!code-vb[VbRaddataConcurrency#2](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConcurrency/VB/Form1.vb#2)]  
  
### <a name="displaychoices-to-the-user"></a>사용자에 게 Displaychoices  
 방금 코드 호출을 작성 합니다 `CreateMessage` 사용자에 게 오류 정보를 표시 하는 프로시저입니다. 이 연습에서는 사용자에 게 서로 다른 버전의 레코드를 표시 하는 메시지 상자를 사용 합니다. 이 레코드 변경 내용으로 덮어쓰거나 편집을 취소 하도록 선택할 수 있습니다. 응답에 전달 되 면 메시지 상자에 있는 (단추 클릭) 하는 옵션을 선택 합니다 `ProcessDialogResult` 메서드.  
  
##### <a name="to-create-the-message-to-display-to-the-user"></a>사용자에 게 표시할 메시지를 만들려면  
  
- 다음 코드를 추가 하 여 메시지를 만들 합니다 **코드 편집기**합니다. 아래이 코드를 입력 합니다 `UpdateDatabase` 메서드.  
  
     [!code-csharp[VbRaddataConcurrency#4](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConcurrency/CS/Form1.cs#4)]
     [!code-vb[VbRaddataConcurrency#4](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConcurrency/VB/Form1.vb#4)]  
  
### <a name="process-the-users-response"></a>사용자의 응답 처리  
 메시지 상자에 대 한 사용자의 응답을 처리 하는 코드를 해야 합니다. 제안된 된 변경으로 데이터베이스의 현재 레코드를 덮어쓸 또는 로컬 변경 내용을 취소 하 고 현재 데이터베이스에 있는 레코드를 사용 하 여 데이터 테이블을 새로 고칠를 선택할 수 있습니다. 사용자가 yes를 선택 하는 경우는 <xref:System.Data.DataTable.Merge%2A> 메서드를 호출 합니다 *preserveChanges* 인수와 함께 `true`입니다. 이렇게 하면 될 레코드의 원래 버전 데이터베이스의 레코드와 일치 하므로 업데이트 하려고 합니다.  
  
##### <a name="to-process-the-user-input-from-the-message-box"></a>사용자를 처리 하는 데 메시지 상자에서 입력  
  
- 이전 섹션에서 추가한 코드 아래에 다음 코드를 추가 합니다.  
  
     [!code-csharp[VbRaddataConcurrency#3](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConcurrency/CS/Form1.cs#3)]
     [!code-vb[VbRaddataConcurrency#3](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConcurrency/VB/Form1.vb#3)]  
  
## <a name="test-the-form"></a>형식 테스트  
 이제 예상 대로 작동 되도록 폼을 테스트할 수 있습니다. 동시성 위반을 시뮬레이션 하기 위해 NorthwindDataSet를 채운 후 데이터베이스의 데이터를 변경 해야 합니다.  
  
#### <a name="to-test-the-form"></a>폼을 테스트 하려면  
  
1. 선택 **F5** 응용 프로그램을 실행 합니다.  
  
2. 폼에 나타납니다. 계속 해 서 실행 후 Visual Studio IDE로 전환 합니다.  
  
3. 에 **뷰** 메뉴 선택 **서버 탐색기**합니다.  
  
4. **서버 탐색기**, 응용 프로그램은 사용 및 확장 한 다음 연결을 확장 합니다 **테이블** 노드.  
  
5. 마우스 오른쪽 단추로 클릭 합니다 **고객이** 테이블을 선택한 후 **테이블 데이터 표시**합니다.  
  
6. 첫 번째 레코드에서 (`ALFKI`)을 변경 `ContactName` 에 `Maria Anders2`입니다.  
  
    > [!NOTE]
    > 변경 내용을 커밋하려면 다른 행으로 이동 합니다.  
  
7. 전환할는 `ConcurrencyWalkthrough`의 폼을 실행 합니다.  
  
8. 폼의 첫 번째 레코드에서 (`ALFKI`)을 변경`ContactName` 에 `Maria Anders1`입니다.  
  
9. **저장** 단추를 선택합니다.  
  
     동시성 오류가 발생 하 고 메시지 상자가 나타납니다.  
  
10. 선택 **No** 업데이트를 취소 하 고 현재 데이터베이스에 있는 값을 사용 하 여 데이터 집합을 업데이트 합니다. 선택 **예** 제안 된 값이 데이터베이스에 기록 합니다.
  
## <a name="see-also"></a>참고 항목

- [데이터를 다시 데이터베이스에 저장](../data-tools/save-data-back-to-the-database.md)