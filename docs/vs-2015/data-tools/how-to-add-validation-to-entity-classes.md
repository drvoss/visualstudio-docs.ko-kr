---
title: '방법: 엔터티 클래스에 유효성 검사 추가 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 61107da9-7fa3-4dba-b101-ae46536f52c4
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 56feab0eb399c2ce99ce3a6f2442ff602209c634
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65697748"
---
# <a name="how-to-add-validation-to-entity-classes"></a>방법: 엔터티 클래스에 유효성 검사 추가
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

엔터티 클래스의 *유효성 검사*는 데이터 개체에 입력된 값이 개체의 스키마 제약 조건과 애플리케이션에 대해 설정된 규칙을 따르는지 확인하는 과정입니다. 업데이트를 내부 데이터베이스에 보내기 전에 데이터의 유효성을 검사하면 오류를 줄일 수 있습니다. 또한 애플리케이션과 데이터베이스 간에 발생할 수 있는 잠재적 라운드트립 횟수를 줄일 수 있습니다.  
  
 합니다 [LINQ to SQL 도구 Visual Studio에서](../data-tools/linq-to-sql-tools-in-visual-studio2.md) 삽입, 업데이트 하는 동안 실행 되며 전체 엔터티 중 및 개별 열 뒤 삭제 하는 디자이너에서 생성 된 코드를 확장할 수 있도록 하는 부분 메서드를 제공 합니다. 변경 내용입니다.  
  
> [!NOTE]
> 이 항목에서는 [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]를 사용하여 엔터티 클래스에 유효성 검사를 추가하는 기본 단계를 설명합니다. 특정 엔터티 클래스를 참조 하지 않고이 일반 단계를 수행 하기 어려울 수 있으므로, 실제 데이터를 사용 하는 연습이 제공 되었습니다.  
  
## <a name="adding-validation-for-changes-to-the-value-in-a-specific-column"></a>변경 내용에 대한 유효성 검사를 특정 열의 값에 추가  
 이 절차는 열의 값이 변경될 때 데이터의 유효성을 검사하는 방법을 보여 줍니다. 유효성 검사는 사용자 인터페이스 대신 클래스 정의 내에서 수행되기 때문에 값에 대한 유효성 검사가 실패하면 예외가 throw됩니다. 애플리케이션에서 열 값을 변경하려고 하는 코드에 대한 오류 처리를 구현하세요.  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
#### <a name="to-validate-data-during-a-columns-value-change"></a>열의 값을 변경하는 동안 데이터의 유효성을 검사하려면  
  
1. 새 LINQ to SQL 클래스 파일을 만들거나 열 ( **.dbml** 파일)에 [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]합니다. (**솔루션 탐색기**에서 **.dbml** 파일을 두 번 클릭합니다.)  
  
2. O/R 디자이너에서 유효성 검사를 추가 하 고 클릭 한 다음 원하는 클래스를 마우스 오른쪽 단추로 **코드 보기**합니다.  
  
    선택한 엔터티 클래스의 partial 클래스와 함께 코드 편집기가 열립니다.  
  
3. 커서를 partial 클래스에 놓습니다.  
  
4. Visual Basic 프로젝트의 경우  
  
   1. **메서드 이름** 목록을 확장합니다.  
  
   2. 찾을 합니다 **에**_COLUMNNAME_**Changing** 유효성 검사를 추가 하려는 열에 대 한 메서드.  
  
   3. `On` *COLUMNNAME* `Changing` 메서드가 partial 클래스에 추가 됩니다.  
  
   4. 다음 코드를 추가하여 입력된 값을 먼저 확인한 다음 열에 입력된 값이 애플리케이션에서 허용되는지 확인합니다. 다음 `value` 인수는 제안된 값을 포함하고 있으므로 이를 유효한 값으로 확인하는 논리를 추가합니다.  
  
      ```vb  
      If value.HasValue Then  
          ' Add code to ensure that the value is acceptable.  
          ' If value < 1 Then  
          '    Throw New Exception("Invalid data!")  
          ' End If  
      End If  
      ```  
  
      C# 프로젝트의 경우:  
  
   5. C# 프로젝트는 이벤트 처리기를 자동으로 생성하지 않기 때문에 IntelliSense를 사용하여 열 변경 부분 메서드를 만들 수 있습니다.  
  
       `partial`을 입력한 다음 사용 가능한 부분 메서드에 액세스하기 위한 공간을 입력합니다. 유효성 검사를 추가할 열에 대해 열 변경 메서드를 클릭합니다. 다음 코드는 열 변경 부분 메서드를 선택할 때 생성된 코드와 비슷합니다.  
  
      ```csharp  
      partial void OnCOLUMNNAMEChanging(COLUMNDATATYPE value)  
          {  
             throw new System.NotImplementedException();  
          }  
  
      ```  
  
## <a name="adding-validation-for-updates-to-an-entity-class"></a>업데이트에 대한 유효성 검사를 엔터티 클래스에 추가  
 변경하는 동안 값을 검사하는 작업 이외에도 전체 엔터티 클래스에 대해 업데이트를 시도할 때 데이터의 유효성을 검사할 수도 있습니다. 비즈니스 규칙에서 여러 열의 값에 대한 비교를 요구하는 경우 업데이트를 시도하는 동안 유효성 검사가 해당 작업을 수행합니다. 다음 절차는 전체 엔터티 클래스를 업데이트하려고 할 때 유효성을 검사하는 방법을 보여 줍니다.  
  
> [!NOTE]
> 전체 엔터티 클래스 업데이트에 대한 유효성 검사 코드는 특정 엔터티 클래스의 partial 클래스가 아니라 partial <xref:System.Data.Linq.DataContext> 클래스에서 실행됩니다.  
  
#### <a name="to-validate-data-during-an-update-to-an-entity-class"></a>엔터티 클래스에 대한 업데이트 동안 데이터의 유효성을 검사하려면  
  
1. 새 LINQ to SQL 클래스 파일을 만들거나 열 ( **.dbml** 파일)에 [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]합니다. (**솔루션 탐색기**에서 **.dbml** 파일을 두 번 클릭합니다.)  
  
2. O/R 디자이너에서 빈 영역을 마우스 오른쪽 단추로 클릭 하 고 클릭 **코드 보기**합니다.  
  
    `DataContext`의 partial 클래스와 함께 코드 편집기가 열립니다.  
  
3. 커서를 `DataContext`의 partial 클래스에 놓습니다.  
  
4. Visual Basic 프로젝트의 경우  
  
   1. **메서드 이름** 목록을 확장합니다.  
  
   2. 클릭 **업데이트**_ENTITYCLASSNAME_합니다.  
  
   3. `Update` *ENTITYCLASSNAME* 메서드가 partial 클래스에 추가 됩니다.  
  
   4. 다음 코드에 표시된 것과 같은 `instance` 인수를 사용하여 개별 열 값에 액세스합니다.  
  
      ```vb  
      If (instance.COLUMNNAME = x) And (instance.COLUMNNAME = y) Then  
          Dim ErrorMessage As String = "Invalid data!"  
          Throw New Exception(ErrorMessage)  
      End If  
      ```  
  
      C# 프로젝트의 경우:  
  
   5. C# 프로젝트는 이벤트 처리기를 자동으로 생성 하지 않기를 하므로 부분을 만들려면 IntelliSense를 사용할 수 있습니다 `Update` *CLASSNAME* 메서드.  
  
   6. `partial`을 입력한 다음 사용 가능한 부분 메서드에 액세스하기 위한 공간을 입력합니다. 유효성 검사를 추가할 클래스에 대해 업데이트 메서드를 클릭합니다. 다음 코드를 선택 하면 생성 되는 코드와 비슷합니다는 `Update` *CLASSNAME* 부분 메서드:  
  
      ```csharp  
      partial void UpdateCLASSNAME(CLASSNAME instance)  
      {  
          if ((instance.COLUMNNAME == x) && (instance.COLUMNNAME = y))  
          {  
              string ErrorMessage = "Invalid data!";  
              throw new System.Exception(ErrorMessage);  
          }  
      }  
      ```  
  
## <a name="see-also"></a>참고 항목  
 [LINQ to SQL 도구 Visual Studio에서](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)   
 [데이터 유효성 검사](https://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)
