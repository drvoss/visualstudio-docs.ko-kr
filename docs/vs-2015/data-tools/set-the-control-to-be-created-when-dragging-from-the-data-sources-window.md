---
title: 데이터 소스 창에서 끌어올 때 만들 컨트롤 설정 | Microsoft Docs
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
- Data Sources Window, select controls
- Windows Forms, displaying data
- data [Visual Studio], displaying on Windows Forms
- data [Visual Studio], Data Sources window
ms.assetid: 20597ff8-0c98-43ec-8fb1-05376804ba48
caps.latest.revision: 34
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 3c9902080ae501c1d77a59f152d7d272462d2264
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62563222"
---
# <a name="set-the-control-to-be-created-when-dragging-from-the-data-sources-window"></a>데이터 소스 창에서 끌어올 때 만들 컨트롤 설정
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

항목을 끌어 데이터 바인딩된 컨트롤을 만들 수 있습니다 합니다 **데이터 원본** 창 WPF 디자이너 또는 Windows Forms 디자이너입니다. 각 항목에는 **데이터 원본** 창 디자이너를 끌 때 만들어지는 기본 컨트롤이 있습니다. 그러나 다른 컨트롤을 만들 수 있습니다.  
  
## <a name="set-the-controls-to-be-created-for-data-tables-or-objects"></a>데이터 테이블 또는 개체에 대해 생성 될 컨트롤 설정  
 데이터 테이블 또는 개체를 나타내는 항목을 끌어 오기 전에 합니다 **데이터 원본** 창 한 컨트롤에 모든 데이터를 표시 하거나 별도의 컨트롤로 각 열 또는 속성 표시 하도록 선택할 수 있습니다.  
  
 이 컨텍스트에서 용어 *개체* 사용자 지정 비즈니스 개체, (엔터티 데이터 모델)에서 엔터티 또는 서비스에 의해 반환 된 개체를 가리킵니다.  
  
#### <a name="to-set-the-controls-to-be-created-for-data-tables-or-objects"></a>데이터 테이블 또는 개체에 대해 생성 될 컨트롤을 설정 하려면  
  
1. WPF 디자이너 또는 Windows Forms 디자이너가 열려 있는지 확인 합니다.  
  
2. 에 **데이터 원본** 창, 데이터 테이블을 나타내는 항목을 선택 하거나 설정할 개체입니다.  
  
3. 항목에 대해 드롭다운 메뉴를 클릭 하 고 메뉴에서 다음 항목 중 하나를 클릭 합니다.  
  
   - 별도 컨트롤에서 각 데이터 필드를 표시 하려면 클릭 **세부 정보**합니다. 디자이너에 데이터 항목을 끌면이 작업 각 열 또는 부모 데이터 테이블의 각 컨트롤에 대 한 레이블과 함께 개체 속성에 대 한 다양 한 데이터 바인딩된 컨트롤을 만듭니다.  
  
   - 모든 데이터를 단일 컨트롤에 표시 하려면 다른 컨트롤 선택 목록에서와 같은 **DataGrid** 또는 **목록** WPF 응용 프로그램, 또는 **DataGridView** Windows Forms에서 응용 프로그램입니다.  
  
     사용 가능한 컨트롤 목록 집니다 있는 디자이너 열기,.NET Framework의 버전은 프로젝트가 대상 및 해당 지원에 데이터 바인딩 컨트롤 여부 추가한 사용자 지정 된 **도구 상자**합니다. 만들려는 컨트롤의 사용 가능한 컨트롤 목록에 있으면 목록에 컨트롤을 추가할 수 있습니다. 자세한 내용은 [데이터 소스 창에 사용자 지정 컨트롤을 추가할](../data-tools/add-custom-controls-to-the-data-sources-window.md)합니다.  
  
     데이터 테이블 또는 개체에 대 한 컨트롤의 목록에 추가할 수 있는 사용자 지정 Windows Forms 컨트롤을 만드는 방법에는 **데이터 원본** 창 참조 [복잡 한 데이터를 지 원하는 Windows Forms 사용자 컨트롤 만들기 바인딩](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md)합니다.  
  
## <a name="set-the-controls-to-be-created-for-data-columns-or-properties"></a>데이터 열 또는 속성에 대해 생성 될 컨트롤 설정  
 열 또는 속성에서 개체를 나타내는 항목을 끌어 오기 전에 합니다 **데이터 원본** 디자이너 창에 만들어질 컨트롤을 설정할 수 있습니다.  
  
#### <a name="to-set-the-controls-to-be-created-for-columns-or-properties"></a>열 또는 속성에 대해 생성 될 컨트롤을 설정 하려면  
  
1. WPF 디자이너 또는 Windows Forms 디자이너가 열려 있는지 확인 합니다.  
  
2. 에 **데이터 원본** 창에서 원하는 테이블을 확장 하거나 해당 열 또는 속성을 표시할 개체입니다.  
  
3. 만들 컨트롤 설정 하려는 각 열 또는 속성을 선택 합니다.  
  
4. 열 또는 속성에 대 한 드롭다운 메뉴를 클릭 하 고 항목을 디자이너로 끌어올 때 만들 컨트롤을 선택 합니다.  
  
     사용 가능한 컨트롤 목록이 있는 디자이너에서 열어 놓은,.NET Framework의 버전 프로젝트가 대상으로 다르며는 사용자 지정 바인딩을 사용 하면 데이터에 추가한을 지 원하는 컨트롤을 **도구 상자**합니다. 만들려는 컨트롤의 사용 가능한 컨트롤 목록에 있으면 목록에 컨트롤을 추가할 수 있습니다. 자세한 내용은 [데이터 소스 창에 사용자 지정 컨트롤을 추가할](../data-tools/add-custom-controls-to-the-data-sources-window.md)합니다.  
  
     데이터 열 또는 속성에 대 한 컨트롤의 목록에 추가할 수 있는 사용자 지정 컨트롤을 만드는 방법에는 **데이터 원본** 창 참조 [단순데이터바인딩을지원하는WindowsForms사용자컨트롤만들기](../data-tools/create-a-windows-forms-user-control-that-supports-simple-data-binding.md).  
  
     선택 열 이나 속성에 대 한 컨트롤을 만드는 않으려면 **None** 드롭 다운 메뉴에서. 부모 테이블 또는 개체를 디자이너로 끌어 하려고 하지만 특정 열 이나 속성을 포함 하지 않을 경우에 유용 합니다.  
  
## <a name="see-also"></a>참고 항목  
 [Visual Studio에서 데이터에 컨트롤 바인딩](../data-tools/bind-controls-to-data-in-visual-studio.md)
