---
title: Access 데이터베이스 (Windows Forms)에서 데이터에 연결 | Microsoft Docs
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
- databases, connecting to
- databases, Access
- data [Visual Studio], connecting
- connecting to data, from Access databases
- Access databases, connecting
ms.assetid: 4159e815-d430-4ad0-a234-e4125fcbef18
caps.latest.revision: 32
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 120297a7e1b3c1e973f1775d769ab6deb8c2902a
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65705570"
---
# <a name="connect-to-data-in-an-access-database-windows-forms"></a>Access 데이터베이스의 데이터에 연결(Windows Forms)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio를 사용 하 여 Access 데이터베이스 (.mdf 파일 또는.accdb 파일)에 연결할 수 있습니다. 연결을 정의한 후 **데이터 원본** 창에 데이터가 나타납니다. 그 창에서 테이블 또는 뷰를 폼으로 끌 수 있습니다.  
  
## <a name="prerequisites"></a>전제 조건  
 이러한 절차를 사용 하려면 Windows Forms 응용 프로그램 프로젝트를 및 Access 데이터베이스 (.accdb 파일) 또는 Access 2000 – 2003 데이터베이스 (.mdb 파일)이 필요 합니다. 파일 형식에 해당하는 절차를 따릅니다.  
  
## <a name="creating-the-dataset-for-an-accdb-file"></a>.accdb 파일에 대한 데이터 세트 만들기  
 다음 절차를 사용 하 여 Access 2013, Office 365, Access 2010 또는 Access 2007을 통해 만든 데이터베이스에 연결할 수 있습니다.  
  
#### <a name="to-create-the-dataset"></a>데이터 세트을 만들려면  
  
1. 데이터를 연결하려는 Windows Forms 애플리케이션을 엽니다.  
  
2. 에 **뷰** 메뉴에서 **기타 Windows** > **데이터 원본**합니다.  
  
     ![다른 Windows 데이터 원본 보기](../data-tools/media/viewdatasources.png "ViewDataSources")  
  
3. **데이터 소스** 창에서 **새 데이터 소스 추가**를 클릭합니다.  
  
     ![새 데이터 원본 추가](../data-tools/media/dataaddnewdatasource.png "dataAddNewDataSource")  
  
4. 선택 **데이터베이스** 에 **데이터 소스 형식 선택** 페이지를 선택한 후 **다음**합니다.  
  
5. 선택 **데이터 집합** 에 **데이터베이스 모델 선택** 페이지를 선택한 후 **다음**합니다.  
  
6. **데이터 연결 선택** 페이지에서 **새 연결**을 선택하여 새 데이터 연결을 구성합니다.  
  
7. 변경 된 **데이터 원본** 하 **.NET Framework Data Provider for OLE DB**합니다.  
  
     ![OLE db 데이터 공급자를 변경](../data-tools/media/datachangedatasourceoledb.png "dataChangeDataSourceOLEDB")  
  
    > [!IMPORTANT]
    > 하지만 데이터 원본 **Microsoft Access 데이터베이스 파일 (OLE DB)** 해당 데이터 원본 유형.mdb 데이터베이스 파일에 대해서만 사용 하 여 올바른 선택을 처럼 보일 수 있습니다.  
  
8. **OLE DB Provider**를 선택 **Microsoft Office 12.0 Access Database Engine OLE DB Provider**합니다.  
  
     ![OLE DB 공급자 Microsoft Office 12.0 Access](../data-tools/media/dataoledbprovideroffice12access.png "dataOLEDBProviderOffice12Access")  
  
9. **서버 또는 파일 이름**에 연결 하 고 클릭 하려는.accdb 파일의 이름과 경로 지정 **확인**합니다.  
  
    > [!NOTE]
    > 데이터베이스 파일에 있으면 사용자 이름 및 암호를 지정 하 선택 하기 전에 **확인**합니다.  
  
10. 선택 **다음** 에 **데이터 연결 선택** 페이지입니다.  
  
11. 선택 **다음** 에 **응용 프로그램 구성 파일에 연결 문자열 저장** 페이지입니다.  
  
12. **데이터베이스 개체 선택** 페이지에서 **테이블** 노드를 확장합니다.  
  
13. 모든 테이블 또는 뷰에서 데이터 집합에 원하는 하 고 선택 하면 선택 **완료**합니다.  
  
     데이터 세트가 프로젝트에 추가되고 테이블과 뷰가 **데이터 원본** 창에 나타납니다.  
  
## <a name="creating-the-dataset-for-an-mdb-file"></a>.Mdb 파일에 대 한 데이터 집합 만들기  
 데이터 세트는 **데이터 원본 구성 마법사**를 실행하여 만듭니다.  
  
#### <a name="to-create-the-dataset"></a>데이터 세트을 만들려면  
  
1. 데이터를 연결하려는 Windows Forms 애플리케이션을 엽니다.  
  
2. 에 **뷰** 메뉴에서 **기타 Windows** > **데이터 원본**합니다.  
  
     ![다른 Windows 데이터 원본 보기](../data-tools/media/viewdatasources.png "ViewDataSources")  
  
3. **데이터 소스** 창에서 **새 데이터 소스 추가**를 클릭합니다.  
  
4. 선택 **데이터베이스** 에 **데이터 소스 형식 선택** 페이지를 선택한 후 **다음**합니다.  
  
5. 선택 **데이터 집합** 에 **데이터베이스 모델 선택** 페이지를 선택한 후 **다음**합니다.  
  
6. **데이터 연결 선택** 페이지에서 **새 연결**을 선택하여 새 데이터 연결을 구성합니다.  
  
7. 데이터 원본에 없는 경우 **Microsoft Access 데이터베이스 파일 (OLE DB)** 를 선택 **변경** 열려는 합니다 **데이터 소스 변경** 대화 상자 **Microsoft 데이터베이스 파일에 액세스할**를 선택한 후 **확인**합니다.  
  
8. 에 **데이터베이스 파일 이름**에 연결 하 고 클릭 하려는.mdb 파일의 이름과 경로 지정 **확인**합니다.  
  
     ![연결 액세스 데이터베이스 파일을 추가](../data-tools/media/dataaddconnectionaccessmdb.png "dataAddConnectionAccessMDB")  
  
9. 선택 **다음** 에 **데이터 연결 선택** 페이지입니다.  
  
10. 선택 **다음** 에 **응용 프로그램 구성 파일에 연결 문자열 저장** 페이지입니다.  
  
11. **데이터베이스 개체 선택** 페이지에서 **테이블** 노드를 확장합니다.  
  
12. 모든 테이블 또는 뷰에서 데이터 집합에 원하는 하 고 선택 하면 선택 **완료**합니다.  
  
     데이터 세트가 프로젝트에 추가되고 테이블과 뷰가 **데이터 원본** 창에 나타납니다.  
  
## <a name="security"></a>보안  
 중요한 정보(예: 암호)를 저장하면 애플리케이션 보안 문제가 발생할 수 있습니다. 데이터베이스 액세스를 제어할 경우에는 통합 보안이라고도 하는 Windows 인증을 사용하는 방법이 더 안전합니다. 자세한 내용은 [연결 정보 보호](https://msdn.microsoft.com/library/1471f580-bcd4-4046-bdaf-d2541ecda2f4)를 참조하세요.  
  
## <a name="next-steps"></a>다음 단계  
 방금 만든 데이터 집합에서 제공 됩니다. 합니다 **데이터 원본** 창입니다. 다음 작업 중 어떤 작업이든 수행할 수 있습니다.  
  
- 항목을 선택 합니다 **데이터 원본** 창에서 폼으로 끌어와 (참조 [Visual Studio에서 데이터 바인딩 Windows Forms 컨트롤](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)).  
  
- 데이터 원본을 추가 하거나 데이터 집합을 구성 하는 개체를 편집 하려면 데이터 집합 디자이너에서 엽니다.  
  
- 유효성 검사 논리를 추가 합니다 <xref:System.Data.DataTable.ColumnChanging> 또는 <xref:System.Data.DataTable.RowChanging> 데이터 집합에 있는 데이터 테이블의 이벤트 (참조 [데이터 집합의 데이터 유효성 검사](../data-tools/validate-data-in-datasets.md)).  
  
## <a name="see-also"></a>참고 항목

 [데이터를 받기 위해 애플리케이션 준비](https://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad)   
 [Visual Studio에서 데이터에 컨트롤 바인딩](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [데이터 유효성 검사](https://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)   
 [데이터 연습](https://msdn.microsoft.com/library/15a88fb8-3bee-4962-914d-7a1f8bd40ec4)