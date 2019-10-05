---
title: 데이터 집합 및 Tableadapter를 다른 프로젝트로 분리 | Microsoft Docs
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
- TableAdapters, n-tier applications
- n-tier applications, separating Datasets and TableAdapters
ms.assetid: f66a3940-6227-46af-a930-9177f425f4fd
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: bfd6cc62fc93ca3a535fb60c4ea5e1323c720558
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65690230"
---
# <a name="separate-datasets-and-tableadapters-into-different-projects"></a>데이터 세트 및 TableAdapter를 다른 프로젝트로 분리
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

형식화 된 데이터 집합 향상 된 있도록 합니다 [Tableadapter](https://msdn.microsoft.com/library/09416de9-134c-4dc7-8262-6c8d81e3f364) dataset 클래스는 별도 프로젝트로 생성 될 수 있습니다. 이 통해 빠르게 응용 프로그램 계층을 분리 하 고 n 계층 데이터 응용 프로그램을 생성할 수 있습니다.  
  
 다음 절차에서는 데이터 집합 디자이너를 사용 하 여 생성 된 포함 된 프로젝트에서 분리 되는 프로젝트에 데이터 집합 코드를 생성 하는 프로세스 `TableAdapter` 코드입니다.  
  
## <a name="separatedatasets-and-tableadapters"></a>Separatedatasets 및 Tableadapter  
 데이터 집합 코드를 분리할 때는 `TableAdapter` 코드, 데이터 집합 코드를 포함 하는 프로젝트를 현재 솔루션에 있어야 합니다. 이 프로젝트는 현재 솔루션에 있지 않으면, 경우에 사용할 수 없습니다는 **데이터 집합 프로젝트** 목록에 **속성** 창입니다.  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
#### <a name="to-separate-the-dataset-into-a-different-project"></a>데이터 집합을 다른 프로젝트를 분리 하려면  
  
1. 데이터 집합 (.xsd 파일)를 포함 하는 솔루션을 엽니다.  
  
   > [!NOTE]
   > 솔루션에는 데이터 집합 코드를 분리 하려면 프로젝트를 찾을 수 없는 경우 프로젝트를 만들거나 기존 프로젝트를 솔루션에 추가 합니다.  
  
2. 형식화 된 데이터 집합 파일 (.xsd 파일)을 두 번 클릭 **솔루션 탐색기** 에서 데이터 집합을 열려고 합니다 **데이터 집합 디자이너**합니다.  
  
3. 빈 영역을 선택 합니다 **데이터 집합 디자이너**합니다.  
  
4. 에 **속성** 창 찾을 합니다 **데이터 집합 프로젝트** 노드.  
  
5. 에 **데이터 집합 프로젝트** 목록에서 데이터 집합 코드를 생성 하려는 프로젝트의 이름을 선택 합니다.  
  
    데이터 집합 코드를 생성 하려는 프로젝트를 선택 합니다 **데이터 집합 파일** 속성은 기본 파일 이름으로 채워집니다. 필요한 경우이 이름을 변경할 수 있습니다. 또한 특정 디렉터리에 데이터 집합 코드를 생성 하려는 경우 설정할 수 있습니다 합니다 **프로젝트 폴더** 속성 폴더의 이름입니다.  
  
   > [!NOTE]
   > 데이터 집합 및 TableAdapters를 분리할 때는 (설정 하 여 합니다 **데이터 집합 프로젝트** 속성), 프로젝트의 기존 부분 데이터 집합 클래스를 자동으로 이동할 수 없습니다. 기존 데이터 집합 부분 클래스는 데이터 집합 프로젝트에 수동으로 이동 해야 합니다.  
  
6. 데이터 집합을 저장 합니다.  
  
    데이터 집합 코드에서 선택한 프로젝트에 생성 됩니다는 **데이터 집합 프로젝트** 속성인 하며 **TableAdapter** 코드가 현재 프로젝트에 생성 됩니다.  
  
   기본적으로 데이터 집합을 분리 한 후 및 `TableAdapter` 결과 코드는 각 프로젝트의 개별 클래스 파일입니다. 원래 프로젝트 파일에 포함 된 DatasetName.Designer.vb (또는 DatasetName.Designer.cs)는 `TableAdapter` 코드입니다. 지정 된 프로젝트를 **데이터 집합 프로젝트** 속성이 파일을 데이터 집합 코드를 포함 하는 DatasetName.DataSet.Designer.vb (또는 DatasetName.DataSet.Designer.cs) 라는 합니다.  
  
> [!NOTE]
> 생성 된 클래스 파일을 보려면 데이터 집합을 선택 또는 `TableAdapter` 프로젝트입니다. 그런 다음, **솔루션 탐색기**를 선택 **모든 파일 표시** 합니다.  
  
## <a name="see-also"></a>참고 항목  
 [N 계층 데이터 응용 프로그램 개요](../data-tools/n-tier-data-applications-overview.md)   
 [연습: N 계층 데이터 응용 프로그램 만들기](../data-tools/walkthrough-creating-an-n-tier-data-application.md)   
 [계층적 업데이트](../data-tools/hierarchical-update.md)   
 [Visual Studio에서 데이터 액세스](../data-tools/accessing-data-in-visual-studio.md)   
 [ADO.NET](https://msdn.microsoft.com/library/5b96ed06-9759-4966-a797-a1d5f6ee50ca)
