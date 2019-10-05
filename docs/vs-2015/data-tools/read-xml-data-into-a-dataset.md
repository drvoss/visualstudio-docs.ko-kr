---
title: 읽기 XML 데이터를 dataset | Microsoft Docs
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
- reading XML
- data access [Visual Studio], XML data
- reading files, XML
- data [Visual Studio], reading from XML files
- reading data, XML files
- XML [Visual Studio], reading
- XML documents, reading
- datasets [Visual Basic], reading XML data
ms.assetid: fae72958-0893-47d6-b3dd-9d42418418e4
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 64a5edbec2f9f482981002e609117996f0080e56
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67825889"
---
# <a name="read-xml-data-into-a-dataset"></a>XML 데이터를 데이터 세트에 읽어오기
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

ADO.NET에는 XML 데이터로 작업 하기 위한 간단한 방법을 제공 합니다. 이 연습에서는 데이터 집합에 XML 데이터를 로드 하는 Windows 응용 프로그램을 만들 수 있습니다. 데이터 집합에 표시 됩니다는 <xref:System.Windows.Forms.DataGridView> 제어 합니다. 마지막으로, XML 파일의 내용을 기반으로 XML 스키마는 텍스트 상자에 표시 됩니다.  
  
 이 연습에서는 5 개의 주요 단계로 구성 됩니다.  
  
1. 새 프로젝트 만들기  
  
2. 데이터 집합으로 읽어 올 XML 파일 만들기  
  
3. 사용자 인터페이스 만들기  
  
4. 데이터 집합을 만드는 XML 파일을 읽고에 표시 된 <xref:System.Windows.Forms.DataGridView> 컨트롤  
  
5. XML 파일에 따라 XML 스키마를 표시 하는 코드 추가 <xref:System.Windows.Forms.TextBox> 컨트롤  
  
> [!NOTE]
> 대화 상자와 메뉴 명령은 활성 설정 또는 버전에 따라 도움말에서 설명 된 것과 다를 수 표시를 사용 합니다. 설정을 변경 하는 **도구** 메뉴에서**설정 가져오기 및 내보내기**합니다. 자세한 내용은 [Visual Studio에서 개발 설정 사용자 지정](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3)을 참조하세요.  
  
## <a name="create-a-new-project"></a>새 프로젝트 만들기  
 이 단계에서는이 연습을 포함 하는 Visual Basic 또는 Visual C# 프로젝트를 만듭니다.  
  
#### <a name="to-create-the-new-windows-project"></a>새 Windows 프로젝트를 만들려면  
  
1. 에 **파일** 메뉴에서 새 프로젝트를 만듭니다.  
  
2. 프로젝트 이름을 `ReadingXML`로 지정합니다.  
  
3. 선택 **Windows 응용 프로그램**를 선택한 후 **확인**합니다. 자세한 내용은 [클라이언트 응용 프로그램](https://msdn.microsoft.com/library/2dfb50b7-5af2-4e12-9bbb-c5ade0e39a68)합니다.  
  
     합니다 **ReadingXML** 프로젝트에 추가한 생성 **솔루션 탐색기**합니다.  
  
## <a name="generate-the-xml-file-to-be-read-into-the-dataset"></a>데이터 집합으로 읽어 올 XML 파일을 생성  
 이 연습에서는 데이터 집합에 XML 데이터 읽기에 집중, 하므로 XML 파일의 내용은 제공 됩니다.  
  
#### <a name="to-create-the-xml-file-that-will-be-read-into-the-dataset"></a>데이터 집합으로 읽을 수 있는 XML 파일을 만들려면  
  
1. 에 **프로젝트** 메뉴에서**새 항목 추가**합니다.  
  
2. 선택 **XML 파일**, 파일 이름을 `authors.xml`를 선택한 후 **추가**합니다.  
  
     XML 파일을 디자이너에 로드 하 고 편집 하기 위해 준비가 됩니다.  
  
3. XML 선언 아래 편집기에 다음 코드를 붙여 넣습니다.  
  
    ```xml  
    <Authors_Table>  
      <authors>  
        <au_id>172-32-1176</au_id>  
        <au_lname>White</au_lname>  
        <au_fname>Johnson</au_fname>  
        <phone>408 496-7223</phone>  
        <address>10932 Bigge Rd.</address>  
        <city>Menlo Park</city>  
        <state>CA</state>  
        <zip>94025</zip>  
        <contract>true</contract>  
      </authors>  
      <authors>  
        <au_id>213-46-8915</au_id>  
        <au_lname>Green</au_lname>  
        <au_fname>Margie</au_fname>  
        <phone>415 986-7020</phone>  
        <address>309 63rd St. #411</address>  
        <city>Oakland</city>  
        <state>CA</state>  
        <zip>94618</zip>  
        <contract>true</contract>  
      </authors>  
      <authors>  
        <au_id>238-95-7766</au_id>  
        <au_lname>Carson</au_lname>  
        <au_fname>Cheryl</au_fname>  
        <phone>415 548-7723</phone>  
        <address>589 Darwin Ln.</address>  
        <city>Berkeley</city>  
        <state>CA</state>  
        <zip>94705</zip>  
        <contract>true</contract>  
      </authors>  
      <authors>  
        <au_id>267-41-2394</au_id>  
        <au_lname>Hunter</au_lname>  
        <au_fname>Anne</au_fname>  
        <phone>408 286-2428</phone>  
        <address>22 Cleveland Av. #14</address>  
        <city>San Jose</city>  
        <state>CA</state>  
        <zip>95128</zip>  
        <contract>true</contract>  
      </authors>  
      <authors>  
        <au_id>274-80-9391</au_id>  
        <au_lname>Straight</au_lname>  
        <au_fname>Dean</au_fname>  
        <phone>415 834-2919</phone>  
        <address>5420 College Av.</address>  
        <city>Oakland</city>  
        <state>CA</state>  
        <zip>94609</zip>  
        <contract>true</contract>  
      </authors>  
    </Authors_Table>  
    ```  
  
4. 에 **파일** 메뉴에서**authors.xml 저장**합니다.  
  
## <a name="create-the-user-interface"></a>사용자 인터페이스 만들기  
 이 응용 프로그램에 대 한 사용자 인터페이스는 다음과 같이 구성 됩니다.  
  
- <xref:System.Windows.Forms.DataGridView> 데이터로 XML 파일의 내용을 표시 하는 컨트롤입니다.  
  
- <xref:System.Windows.Forms.TextBox> XML 파일에 대 한 XML 스키마를 표시 하는 컨트롤입니다.  
  
- 두 <xref:System.Windows.Forms.Button> 컨트롤.  
  
  - 단추 하나는 데이터 집합에 XML 파일을 읽고에 표시 된 <xref:System.Windows.Forms.DataGridView> 컨트롤입니다.  

  - 두 번째 단추를 통해 데이터 집합에서 스키마를 추출를 <xref:System.IO.StringWriter> 에 표시 된 <xref:System.Windows.Forms.TextBox> 컨트롤입니다.  
  
#### <a name="to-add-controls-to-the-form"></a>컨트롤을 폼에 추가하려면  
  
1. 열기 `Form1` 디자인 뷰에서 합니다.  
  
2. **도구 상자**, 다음과 같은 컨트롤을 폼으로 끌어 옵니다.  
  
    - 하나의 <xref:System.Windows.Forms.DataGridView> 컨트롤  
  
    - 하나의 <xref:System.Windows.Forms.TextBox> 컨트롤  
  
    - 두 <xref:System.Windows.Forms.Button> 컨트롤  
  
3. 다음 속성을 설정합니다.  
  
    |Control|속성|설정|  
    |-------------|--------------|-------------|  
    |`TextBox1`|**Multiline**|`true`|  
    ||**ScrollBars**|**세로**|  
    |`Button1`|**이름**|`ReadXmlButton`|  
    ||**텍스트**|`Read XML`|  
    |`Button2`|**이름**|`ShowSchemaButton`|  
    ||**텍스트**|`Show Schema`|  
  
## <a name="create-the-dataset-thatreceives-the-xml-data"></a>XML 데이터를 데이터 집합 thatreceives를 만들려면  
 이 단계에서는 명명 된 새 데이터 집합을 만든 `authors`합니다. 데이터 집합에 대 한 자세한 내용은 참조 하세요. [Visual Studio에서 데이터 집합 도구](../data-tools/dataset-tools-in-visual-studio.md)합니다.  
  
#### <a name="to-create-a-new-dataset-that--receives-the-xml-data"></a>XML 데이터를 수신 하는 새 데이터 집합을 만들려면  
  
1. **솔루션 탐색기**에 대 한 원본 파일을 선택 **Form1**를 선택한 후는 **뷰 디자이너** 단추를 **솔루션 탐색기** 도구 모음입니다.  
  
2. [도구 상자, 데이터 탭](../ide/reference/toolbox-data-tab.md)를 끌어를 **데이터 집합** 끌어다 **Form1**합니다.  
  
3. 에 **데이터 집합 추가** 대화 상자에서 **형식화 되지 않은 데이터 집합**를 선택한 후 **확인**합니다.  
  
     **DataSet1** 구성 요소 트레이에 추가 됩니다.  
  
4. 에 **속성** 창에서 **이름** 및 <xref:System.Data.DataSet.DataSetName%2A> 에 대 한 속성`AuthorsDataSet`합니다.  
  
## <a name="create-the-event-handler-to-read-the-xml-file-into-the-dataset"></a>데이터 집합에 XML 파일을 읽을 수 이벤트 처리기 만들기  
 합니다 **읽기 XML** 단추는 데이터 집합에 XML 파일을 읽습니다. 그런 다음에 속성을 설정 합니다 <xref:System.Windows.Forms.DataGridView> 데이터 집합에 바인딩되는 컨트롤입니다.  
  
#### <a name="to-add-code-to-the-readxmlbuttonclick-event-handler"></a>ReadXmlButton_Click 이벤트 처리기에 코드를 추가 하려면  
  
1. **솔루션 탐색기**를 선택 **Form1**를 선택한 후는 **뷰 디자이너** 단추를 **솔루션 탐색기** 도구 모음입니다.  
  
2. 선택 된 **읽기 XML** 단추입니다.  
  
     합니다 **코드 편집기** 열립니다는 `ReadXmlButton_Click` 이벤트 처리기입니다.  
  
3. 다음 코드를 입력 합니다 `ReadXmlButton_Click` 이벤트 처리기:  
  
     [!code-csharp[VbRaddataFillingAndExecuting#2](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/CS/Form1.cs#2)]
     [!code-vb[VbRaddataFillingAndExecuting#2](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/VB/Form1.vb#2)]  
  
4. 에 `ReadXMLButton_Click` 이벤트 처리기 코드를 변경은 `filepath =` 올바른 경로를 입력 합니다.  
  
## <a name="create-the-event-handler-to-display-the-schema-in-the-textbox"></a>텍스트 상자에 스키마를 표시 하려면 이벤트 처리기 만들기  
 **스키마 표시** 단추를 만듭니다를 <xref:System.IO.StringWriter> 스키마를 사용 하 여 채워지고에 표시 되는 개체는 <xref:System.Windows.Forms.TextBox>제어 합니다.  
  
#### <a name="to-add-code-to-the-showschemabuttonclick-event-handler"></a>ShowSchemaButton_Click 이벤트 처리기에 코드를 추가 하려면  
  
1. **솔루션 탐색기**를 선택 **Form1**를 선택한 후는 **뷰 디자이너** 단추입니다.  
  
2. 선택 된 **스키마 표시** 단추입니다.  
  
     합니다 **코드 편집기** 열립니다는 `ShowSchemaButton_Click` 이벤트 처리기입니다.  
  
3. 다음 코드를 입력 합니다 `ShowSchemaButton_Click` 이벤트 처리기입니다.  
  
     [!code-csharp[VbRaddataFillingAndExecuting#3](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/CS/Form1.cs#3)]
     [!code-vb[VbRaddataFillingAndExecuting#3](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/VB/Form1.vb#3)]  
  
## <a name="test-the-form"></a>폼 테스트  

이제 예상 대로 작동 되도록 폼을 테스트할 수 있습니다.
  
1. 선택 **F5** 응용 프로그램을 실행 합니다.  
  
2. 선택 된 **읽기 XML** 단추입니다.  
  
     DataGridView에는 XML 파일의 내용이 표시 됩니다.  
  
3. 선택 된 **스키마 표시** 단추입니다.  
  
     텍스트 상자는 XML 파일에 대 한 XML 스키마를 표시합니다.  
  
## <a name="next-steps"></a>다음 단계  

이 연습에서는 데이터 집합에 XML 파일을 읽을 수 있을 뿐만 아니라 XML 파일의 내용을 기반으로 하는 스키마 만들기의 기본 사항을 설명 합니다. 그런 다음 수행할 수 있는 일부 태스크는 다음과 같습니다.  
  
- 데이터 집합 및 XML로 다시 작성할에서 데이터를 편집 합니다. 자세한 내용은 <xref:System.Data.DataSet.WriteXml%2A>을 참조하세요.  
  
- 데이터 집합에서 데이터를 편집 하 고 데이터베이스에 작성 합니다.
  
## <a name="see-also"></a>참고 항목  
 [데이터 연습](https://msdn.microsoft.com/library/15a88fb8-3bee-4962-914d-7a1f8bd40ec4)   
 [Visual Studio에서 데이터 액세스](../data-tools/accessing-data-in-visual-studio.md)   
 [데이터를 받기 위해 애플리케이션 준비](https://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad)   
 [Visual Studio의 XML 도구](../xml-tools/xml-tools-in-visual-studio.md)
