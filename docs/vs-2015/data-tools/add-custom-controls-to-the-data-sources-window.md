---
title: 데이터 소스 창에 사용자 지정 컨트롤 추가 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
f1_keywords:
- vs.datasource.howtoaddcustomcontrol
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- Data Sources Window, adding controls
- controls [Visual Studio], adding to Data Sources Window
- DefaultBindingPropertyAttribute class, using
- LookupBindingPropertiesAttribute class, using
- ComplexBindingPropertiesAttribute class, using
- Data Sources Window, selecting controls
ms.assetid: 8c43e7d2-ba94-4d9b-96de-3aa971955afd
caps.latest.revision: 45
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 28476c454dc78f30e33c0b37e8319bfe5a65df2d
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65699381"
---
# <a name="add-custom-controls-to-the-data-sources-window"></a>데이터 소스 창에 사용자 지정 컨트롤 추가
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

항목을 끌면 합니다 **데이터 원본** 창 데이터 바인딩된 컨트롤을 만드는 디자인 화면에 사용자가 만든 컨트롤의 형식을 선택할 수 있습니다. 창의 각 항목에는 드롭다운 목록에서 선택할 수 있는 컨트롤을 표시 하는 있습니다. 각 항목에 연결 된 컨트롤 집합에는 항목의 데이터 형식에 의해 결정 됩니다. 만들려는 컨트롤 목록에 나타나지 않으면, 목록 컨트롤을 추가 하려면이 항목의 지침을 따라 수 있습니다.  
  
 데이터 바인딩된 컨트롤에서 항목에 대 한 만들기를 선택 하는 방법에 대 한 자세한 내용은 합니다 **데이터 원본** 창 참조 [데이터 소스 창에서 끌어올 때 만들 컨트롤 설정](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)합니다.  
  
> [!NOTE]
> 표시되는 대화 상자와 메뉴 명령은 실제 설정이나 버전에 따라 도움말에서 설명하는 것과 다를 수 있습니다. 설정을 변경 하는 **도구** 메뉴에서 **설정 가져오기 및 내보내기**합니다. 자세한 내용은 [Visual Studio에서 개발 설정 사용자 지정](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3)을 참조하세요.  
  
## <a name="customizinglist"></a> 데이터 형식에 대 한 바인딩 가능한 컨트롤 목록 사용자 지정  
 추가 하거나 컨트롤의 항목에 대 한 사용 가능한 컨트롤 목록에서 제거 하는 **데이터 원본** 창 다음 단계를 수행 하는 특정 데이터 형식입니다.  
  
#### <a name="to-select-the-controls-to-be-listed-for-a-data-type"></a>데이터 형식에 대 한 나열 될 컨트롤을 선택 하려면  
  
1. WPF 디자이너 또는 Windows Forms 디자이너가 열려 있는지 확인 합니다.  
  
2. 에 **데이터 원본** 창, 창에 추가한 데이터 원본의 일부인 항목을 클릭 한 다음 항목에 대 한 드롭다운 메뉴를 클릭 합니다.  
  
3. 드롭다운 메뉴에서 클릭 **사용자 지정**합니다. 다음 대화 상자 중 하나를 엽니다.  
  
    - Windows Forms 디자이너가 열려 있으면 합니다 **데이터 UI 사용자 지정** 페이지의 **옵션** 대화 상자가 열립니다.  
  
    - WPF Designer 열려 있으면 합니다 **컨트롤 바인딩 사용자 지정** 대화 상자가 열립니다.  
  
4. 대화 상자에서 데이터 형식을 선택 합니다 **데이터 형식** 드롭 다운 목록.  
  
    - 테이블 또는 개체에 대 한 컨트롤의 목록, 사용자 지정 하려면 선택 **[목록]** 합니다.  
  
    - 테이블의 열 또는 개체의 속성에 대 한 컨트롤 목록을 사용자 지정 하려면 내부 데이터 저장소에서 데이터 형식의 열 이나 속성을 선택 합니다.  
  
    - 사용자 정의 도형을 데이터 개체를 표시 하는 컨트롤의 목록, 사용자 지정 하려면 선택 **[기타]** 합니다. 예를 들어 선택할 **[기타]** 응용 프로그램에 특정 개체의 속성이 둘 이상에서 데이터를 표시 하는 사용자 지정 컨트롤입니다.  
  
5. 에 **연결 된 컨트롤** 상자에서 선택한 데이터 형식에 대해 사용할 수 있도록 하려는 각 컨트롤을 선택 하거나 목록에서 제거 하려는 모든 컨트롤의 선택을 취소 합니다.  
  
    > [!NOTE]
    > 컨트롤 선택 하려는 경우에 나타나지 않습니다 합니다 **연결 된 컨트롤** 상자 컨트롤 목록에 추가 해야 합니다. 자세한 내용은 [데이터 형식의 연결 된 컨트롤 목록에 컨트롤 추가](#addingcontrols)합니다.  
  
6. **확인**을 클릭합니다.  
  
7. 에 **데이터 원본** 창, 하나 이상의 컨트롤을 연결한 입력 데이터 항목 클릭 한 다음 항목에 대 한 드롭다운 메뉴를 클릭 합니다.  
  
     선택한 컨트롤을 **연결 된 컨트롤** 상자 항목에 대 한 드롭다운 메뉴에 나타납니다.  
  
## <a name="addingcontrols"></a> 데이터 형식에 대 한 연결 된 컨트롤의 목록에 Addcontrols  
 데이터 형식을 사용 하 여 컨트롤을 연결 하려는 경우 컨트롤에 표시 되지 않습니다 합니다 **연결 된 컨트롤** 상자 컨트롤 목록에 추가 해야 합니다. 컨트롤이 현재 솔루션에서 또는 참조 된 어셈블리에 배치 해야 합니다. 사용할 수 있는 수도 있어야 합니다 **도구 상자**, 있고 컨트롤의 데이터 바인딩 동작을 지정 하는 특성입니다.  
  
#### <a name="to-add-controls-to-the-list-of-associated-controls"></a>연결 된 컨트롤의 목록에 컨트롤을 추가 하려면  
  
1. 원하는 컨트롤을 추가 합니다 **도구 상자** 마우스 오른쪽 단추로 클릭 하 여 합니다 **도구 상자** 선택 하 고 **항목 선택**합니다.  
  
     컨트롤 다음 특성 중 하나가 있어야 합니다.  
  
    |특성|설명|  
    |---------------|-----------------|  
    |<xref:System.ComponentModel.DefaultBindingPropertyAttribute>|와 같은 데이터의 단일 열 (또는 속성)를 표시 하는 간단한 컨트롤에서이 특성을 구현 된 <xref:System.Windows.Forms.TextBox>합니다.|  
    |<xref:System.ComponentModel.ComplexBindingPropertiesAttribute>|와 같은 목록 또는 테이블의 데이터를 표시 하는 컨트롤에서이 특성을 구현 된 <xref:System.Windows.Forms.DataGridView>합니다.|  
    |<xref:System.ComponentModel.LookupBindingPropertiesAttribute>|와 같은 데이터 뿐만 아니라 단일 열 또는 속성을 제공할 필요가의 목록 (또는 테이블)를 표시 하는 컨트롤에서이 특성을 구현 된 <xref:System.Windows.Forms.ComboBox>합니다.|  
  
2. Windows forms에 **옵션** 대화 상자를 엽니다 합니다 **데이터 UI 사용자 지정** 페이지. 또는 WPF에 대 한 열을 **컨트롤 바인딩 사용자 지정** 대화 상자. 자세한 내용은 [데이터 형식에 대 한 바인딩 가능한 컨트롤 목록 사용자 지정](#customizinglist)합니다.  
  
3. 에 **연결 된 컨트롤** 상자에 방금 추가한 컨트롤을 **도구 상자** 나타나야 합니다.  
  
    > [!NOTE]
    > 연결 된 컨트롤의 목록에 현재 솔루션 내에서 또는 참조 된 어셈블리에 있는 유일한 컨트롤을 추가할 수 있습니다. (컨트롤 구현 해야 데이터 바인딩 특성 중 하나 앞의 표에서.) 데이터에서 사용할 수 없는 사용자 지정 컨트롤을 바인딩할 합니다 **데이터 원본** 창에서 컨트롤을 끌어 합니다 **도구 상자** 를 디자인 화면으로 끌어에서 바인딩할 항목으로는 **데이터 원본** 컨트롤 창입니다.  
  
## <a name="see-also"></a>참고 항목  
 [Visual Studio에서 데이터에 컨트롤 바인딩](../data-tools/bind-controls-to-data-in-visual-studio.md)
